#ansible-pi-setup 

##About
This is a pair of ansible plays intended to perform the following basic configuration tasks listed below. You must enable SSH on the target pi before this will work. 

- Install fail2ban
- apt-get update
- Upgrade all packages
- Add new user
- (optional) add authorized key
- delete pi user

##How To:
- Enable the SSH server via raspi-config (advanced options>SSH) or your preferred method
- Make sure you can successfully SSH from the ansible machine using pi/raspberry
- Install [Ansible](https://www.ansible.com/)
- Run the main playbook `ansible-playbook -i TARGETIPADDRESSGOESHERE, -k main.yml`
..-	SSH Password: this is the password for the pi. By default it is 'raspberry'.
..-	Hostname: new hostname for the raspberry pi, use alpa numeric characters.
..-	Username: enter the username of the new user that ansible will create. 
..-	Password: enter salted pass for the new user (openssl passwd -salt <salt> -1 <plaintext>).
- Test that you can ssh and sudo with you new username and password
- If you can `ssh ansible-playbook -i TARGETIPADDRESSGOESHERE, -k cleanup.yml`

### WARNING: Fail2ban will keep brute force attacks at bay, but remember this setup is only as secure as the password for your new user. 

##Thanks:

I used the page below as a guide for what should be done. In addition to the current configuration a firewall would be also help with security but that more depends on the usecase for the server. 
https://mattwilcox.net/web-development/setting-up-a-secure-home-web-server-with-raspberry-pi





