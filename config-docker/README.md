
# Overview
This Ansible playbook installs Docker and Docker Compose on a remote Ubuntu server, sets up user permissions, creates a directory for monitoring files, and copies a Docker Compose file to the target directory.

## Requirements
- Ansible installed on your local machine.
- SSH access to the remote_host.

## File Structure
- `install-config-docker.yml`: Main Ansible playbook to install Docker and configure the monitoring environment.
- `inventory`: Inventory file defining the target host.
- `docker-compose.yml`: Docker Compose file (sample) that will be copied to the remote server.

## Playbook Details
The `install-config-docker.yml` playbook performs the following tasks:

- Updates and upgrades APT packages.
- Installs Docker prerequisites.
- Adds Docker's GPG key and repository.
- Installs Docker and Docker Compose.
- Adds the specified user to the Docker group for permission management.
- Creates a directory for monitoring in the user’s home directory.
- Copies the `docker-compose.yml` file to the remote server's monitoring directory.

## Inventory Configuration
Define the `remote_host` in the inventory file, specifying the `IP address` and `SSH user`.

## Usage Instructions
1. Clone the Repository
2. Customize Variables:

- Edit `install-config-docker.yml` as needed to match your setup.
- Update `inventory` with the remote server details.
3. Run the Playbook:

```
ansible-playbook -i inventory install-config-docker.yml
```
## Variables in install-config-docker.yml
`docker_compose_sample_path`: Path to your Docker Compose file on the local machine. Defaults to `./docker-compose.yml`.
## Additional Notes
- Ensure the `SSH user` in `inventory` has `sudo` privileges.
- The playbook runs certain tasks as root for installation, while others are executed as the target user specified in the inventory file.
