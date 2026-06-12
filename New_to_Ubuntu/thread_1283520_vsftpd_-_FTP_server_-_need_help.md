---
title: "vsftpd - FTP server - need help"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by TMVirginia on 2009-10-05
Hi All,

  My linux box runs vsftpd - FPT server, my WindowsXP run WinSCP client. It was able to establish a connection as an anonymous. The connection was at the linux root but I cannot see or change to any sub directory. Need help.

Virginia

---

### Post by keith.newell on 2009-10-05
I found this link very helpful.  [https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html)  Hope it helps.

---

### Post by TMVirginia on 2009-10-07
Thanks for the link. I'm able to establish anonymous sessions and download file from the FTP server. However, it's kink of confusing to set up an authenticated user for password log in. How do you create an authenticated user, the password, and his/her directory. Thanks

---

### Post by kracheck on 2009-10-07
Hopefully this will be of use to you. It's the way my FTP server is set-up on ubuntu hardy 8.04 behind a linksys WRT54G Router with static IP adresses.

If you are behind a router make sure to forward following ports to the computer running VSFTPD :
60021 - This is the listening port for incoming FTP connections
62222-63333 - Ports for PASV data connections.


1. Install VSFTPD

        # sudo apt-get install vsftpd

2. Virtual users and authentication 

        We are going to use pam_userdb to authenticate the virtual users. This needs a username / password file in `db&#8217; format &#8211; a common database format. We need `db_load&#8217; 

program. 
        
        # sudo apt-get install db4.2-util
        
        
To create a `db&#8217; format file, first create a plain text file `virtual-users.txt&#8217; in your home directory with the usernames and passwords on alternating lines:

mary
123456
jack
654321
        
        
Then execute the following command to create the actual database: 

        # sudo db4.2_load -T -t hash -f /home/YourUsernameOnTheSystem/virtual-users.txt /etc/virtual-users.db
        
        
Now, create a PAM file /etc/pam.d/vsftpd-virtual which uses your database: 

        auth required pam_userdb.so db=/etc/virtual-users
        account required pam_userdb.so db=/etc/virtual-users
        
        
3. Configuration of VSFTPD

Create a configuration file /etc/vsftpd-virtual.conf, 

# disables anonymous FTP
anonymous_enable=NO
# enables non-anonymous FTP
local_enable=YES
# activates virtual users
guest_enable=YES
# virtual users to use local privs, not anon privs
virtual_use_local_privs=YES
# enables uploads and new directories
write_enable=YES
# the PAM file used by authentication of virtual uses
pam_service_name=vsftpd-virtual
# in conjunction with 'local_root',
# specifies a home directory for virtual users
local_root=/var/www/virtual
# the virtual user is restricted to the virtual FTP area
chroot_local_user=YES
# hides the FTP server user IDs and just display "ftp" in directory listings
hide_ids=YES
# runs vsftpd in standalone mode
listen=YES
# listens on this port for incoming FTP connections
listen_port=60021
# In response to BAD IP CONNECTING with FireFTP / comment out if you
# don't have the problem
pasv_promiscuous=YES
# the minimum port to allocate for PASV style data connections
pasv_min_port=62222
# the maximum port to allocate for PASV style data connections
pasv_max_port=63333
# controls whether PORT style data connections use port 20 (ftp-data)
connect_from_port_20=YES
# the umask for file creation
local_umask=022
        
        
4. Creation of home directories

Create each user&#8217;s home directory in /var/www/virtual, and change the owner of the directory to the user `ftp&#8217;: 
# sudo groupadd ftp
# sudo useradd -g ftp -d /dev/null -s /etc ftp
# sudo mkdir /var/www
# sudo mkdir /var/www/virtual
# sudo mkdir /var/www/virtual/USERNAME (same as in virtual-users.txt)
# sudo chown ftp:ftp /var/www/virtual/USERNAME (same as in virtual.users.txt)
        
        
5. Startup of VSFTPD and test
Now we can start VSFTPD by the command: 

# sudo vsftpd
        
        
and test the FTP access of a virtual user: 

# ftp localhost 60021

---

