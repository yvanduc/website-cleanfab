# Spécifications Techniques

## Environnement de Développement

- WordPress
- PHP 8.x
- MySQL 8.x
- Serveur Web : Apache/Nginx

## Performance

- Optimisation des images
- Cache avec WP Rocket
- Minification CSS/JS
- Lazy loading

## Sécurité

- SSL/HTTPS
- Protection formulaires
- Sauvegardes automatiques
- Mises à jour automatiques

## Base de Données

### Tables Personnalisées

```sql
-- Réservations
CREATE TABLE wp_reservations (
    id INT PRIMARY KEY AUTO_INCREMENT,
    date DATE NOT NULL,
    heure_debut TIME NOT NULL,
    heure_fin TIME NOT NULL,
    nom VARCHAR(100) NOT NULL,
    prenom VARCHAR(100) NOT NULL,
    email VARCHAR(255) NOT NULL,
    telephone VARCHAR(20) NOT NULL,
    service_type ENUM('exterieur', 'interieur', 'integral') NOT NULL,
    status ENUM('en_attente', 'confirme', 'annule') NOT NULL DEFAULT 'en_attente',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Configuration Prix
CREATE TABLE wp_prix_services (
    id INT PRIMARY KEY AUTO_INCREMENT,
    service_type VARCHAR(50) NOT NULL,
    prix DECIMAL(10,2) NOT NULL,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```