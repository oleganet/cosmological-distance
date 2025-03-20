# cosmological-distance
import math

def calculate_cosmological_distance(redshift, omega_m=0.3, omega_lambda=0.7, H0=70):
    """Calculate the proper distance to a galaxy using the Lambda-CDM cosmological model."""
    c = 299792  # Speed of light in km/s
    
    def E(z):
        return math.sqrt(omega_m * (1 + z)**3 + omega_lambda)
    
    # Integrate 1/E(z) from 0 to redshift
    num_steps = 1000
    dz = redshift / num_steps
    integral = sum(1 / E(z * dz) for z in range(num_steps)) * dz
    
    # Convert to distance in Megaparsecs (Mpc)
    distance = (c / H0) * integral
    return distance

# Example usage
redshift_value = 1.5  # Example redshift value
distance = calculate_cosmological_distance(redshift_value)
print(f"Cosmological distance to galaxy with redshift {redshift_value}: {distance:.2f} Mpc")
