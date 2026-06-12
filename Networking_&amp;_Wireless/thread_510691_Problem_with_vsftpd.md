---
title: "Problem with vsftpd"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by theadam on 2007-07-26
I setup vsftpd and i can access my FTP on my home network with a user name and password, but the same user name and password will not work with a friends connection.  She gets a message that says she has the wrong user name and password.  She is getting to my server, because it prompts for a password, but the password i enter on my network does not work for her.

Anyone know what to do to make this work?

---

### Post by PaulFr on 2007-07-27
Have you checked the vsftpd.log file to see any error messages there ? By default, this log file is in /var/log/vsftpd.log, though you could change it (**grep xferlog_file /etc/vsftpd.conf** to see if it has been changed).

---

### Post by rg_stephens on 2007-07-27
> , but the same user name and password will not work with a friends connection. 

Sorry to interrupt, but I'm having the same problem. My friend connects and gets as far as "Welcome to my FTP server" and then it stops. My log file says that he has connected, but nothing else. Could my ISP be blocking it?

Robert

---

### Post by KiloEleven on 2007-07-27
What ports are open on your router/firewall? Is the vsftp setup for active or passive FTP? Differences can be seen here: [http://en.wikipedia.org/wiki/File_Transfer_Protocol]("http://en.wikipedia.org/wiki/File_Transfer_Protocol")

---

### Post by rg_stephens on 2007-07-29
It's set up for passive mode. I tried a few random ports; right now I'm using port 1024 as the listen port. I'm not sure which ones I should use. I opened all the ports on the router, and firestarter doesn't report that it blocked it.

Right now when I try connecting from the external IP, it gets as far as the LIST command, displays the icon for the root directory, and then hangs up. It doesn't give me a directory listing.

```
listen_port=1024
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
ftp_data_port=20
pasv_min_port=10050
pasv_max_port=10060
anon_other_write_enable=YES

#The permissions with which uploaded files are created. Umasks are applied on top of this value. You #may wish to change to 0777 if you want uploaded files to be executable.
#Default: 0666 
file_open_mode=0777

# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=0000

# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=YES
anon_root=/media/shared/abyssws/htdocs/files
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#

#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
anon_upload_enable=NO
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
anon_mkdir_write_enable=NO
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
pasv_enable=YES


#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
chown_uploads=YES
chown_username=shared
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
ftpd_banner=Welcome to Robert's FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

```

---

### Post by rg_stephens on 2007-07-29
I just noticed that if I log in using the internal IP address, everything works beautifully. If I try to connect with the external IP address from inside my LAN, it enters passive mode, then gives the error:

425 Security: Bad IP connecting. : //

It appears to be connected, but doesn't give a directory listing.

---

### Post by PaulFr on 2007-07-29
rg_stephens, your section at the top says```
listen_port=1024
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
ftp_data_port=20
pasv_min_port=10050
pasv_max_port=10060
```I assume the transfer is in **passive mode**. If so, the client will make two connections to your server: one to the listen_port **1024** and one to some port in the range **10050 to 10060**. Please check that these ports are open on your firewall.

---

### Post by PaulFr on 2007-07-29
Also try the following in the vsftpd.conf file:```
pasv_promiscuous=YES
``` and if that does not work by itself, add ```
pasv_address=<your_public_ip_address>
``` Again, this is only valid for **passive** FTP.

---

### Post by rg_stephens on 2007-07-29
> **PaulFr said:**
> Also try the following in the vsftpd.conf file:```
pasv_promiscuous=YES
``` and if that does not work by itself, add ```
pasv_address=<your_public_ip_address>
``` Again, this is only valid for **passive** FTP.

I ran a port scan and the ports were visible, and I opened all the firewall ports. 

By public IP address, do you mean my external IP? 

IP: 70.173.154.225
port: 1024
username: troy
password: 54321

Now it connects and I can see some files in the directory, but it gives me a "invalid pasv address" error if I try to transfer anything. Also, it's not displaying the disk drive that I mounted to the user's home folder.

---

### Post by PaulFr on 2007-07-29
Yes, I mean the address that the client machine sees (assuming this is outside your network, it will be your public IP address)

 Basically, the vsftpd sends (in passive mode) the IP address and port number to the client; and the client is supposed to use that IP address and port to connect. If you have an IP address on your NAT network like 192.168.1.12, then sending this out to the client is useless, since if it tries to connect to 192.168.1.2 it will not be routed across the Internet.

So setting pasv_address is to force vsftpd to use a different IP address like your public IP address.

One way (of many) is to go to **[http://www.dnsstuff.com](http://www.dnsstuff.com)** or **[http://www.internetfrog.com/](http://www.internetfrog.com/)**. At the top of the page, your public IP address will be shown.

---

### Post by rg_stephens on 2007-07-29
Thanks PaulFr

Yes, I've done what you suggested. Perhaps I mis-typed something.  Here is what happens in CoreFTP:

[I]30 Login successful.  
SYST  
215 UNIX Type: L8  
Keep alive off...
PASV  
500 OOPS: invalid pasv_address  
Attemping Active mode transfer...
PORT 10,0,0,20,74,11  

Error loading directory...
disconnected  [/I]

---

### Post by PaulFr on 2007-07-30
Could you post
1. The latest modifications to your vsftpd.conf file ? 
2. The FTP server public IP address from either dnsstuff.com or internetfrog.com ?
3. The internal IP address of your FTP server (**ifconfig -a|grep inet|grep Mask|grep -v 127**) ?
4. Your client's public IP address from  either dnsstuff.com or internetfrog.com ?
5. The internal IP address of your client machine ?

---

### Post by rg_stephens on 2007-07-30
> **PaulFr said:**
> Could you post
1. The latest modifications to your vsftpd.conf file ? 
2. The FTP server public IP address from either dnsstuff.com or internetfrog.com ?
3. The internal IP address of your FTP server (**ifconfig -a|grep inet|grep Mask|grep -v 127**) ?
4. Your client's public IP address from  either dnsstuff.com or internetfrog.com ?
5. The internal IP address of your client machine ?

The entire system suddenly crashed a couple of times. I decided to reformat and upgrade to Ubuntu 7.04, and now the partitioner says that my file system has errors. It's a fairly new hard drive, so I'm not sure what happened. I'll let you know what happens when I get this contraption working again.

---

### Post by rg_stephens on 2007-07-31
Ok, I reformatted the computer and installed Ubuntu 7.04CE. I took the router out of the system to simplify things. Right now I'm at work behind a firewall, and my external ip is 205.159.86.244. I am able to connect, but it times out when when it tries to get a directory listing. 

I copied my vsftpd.conf file to [http://70.173.155.88:10000/vsftpd.conf](http://70.173.155.88:10000/vsftpd.conf)

> 27 Entering Passive Mode (70,173,155,88,9,45)  
LIST  
Connect socket #668 to 70.173.155.88, port 2349...
timeout
QUIT  
Connect socket #636 to 70.173.155.88, port 1024...
220 (vsFTPd 2.0.5)  
USER beto  
331 Please specify the password.  
PASS **********  
230 Login successful.  
SYST  
215 UNIX Type: L8  
Keep alive off...
Attemping Active mode transfer...
PORT 192,168,7,237,116,194  
Error loading directory...
disconnected  


*ifconfig -a|grep inet|grep Mask|grep -v 127*
returns the following:
*inet addr:70.173.155.88  Bcast:70.173.155.255  Mask:255.255.252.0*

---

### Post by PaulFr on 2007-08-01
Please replace ```
pasv_address=<70.173.155.88>
``` in your vsftpd.conf file with ```
pasv_address=70.173.155.88
``` and try from **outside** your network.

---

### Post by rg_stephens on 2007-08-01
Right now my client machine is at 192.168.7.237 with an external IP of 205.159.86.10. 

The strange thing is if I try to connect locally (using 127.0.0.1) it gives me a directory listing, but doesn't let me write or change directories.

Using passive mode:

```
57 "/home/beto/Desktop/web"  
PASV  
227 Entering Passive Mode (70,173,155,88,9,47)  
LIST  
Connect socket #484 to 70.173.155.88, port 2351...
timeout
QUIT  
```

And using active mode:

```
Connect socket #448 to 70.173.155.88, port 1024...
220 (vsFTPd 2.0.5)  
USER shared  
331 Please specify the password.  
PASS **********  
230 Login successful.  
SYST  
215 UNIX Type: L8  
Keep alive off...
Attemping Active mode transfer...
PORT 192,168,7,237,54,97  

Error loading directory...
disconnected  
```

---

### Post by PaulFr on 2007-08-01
In your last post, the failure in passive FTP mode is to be expected. The problem is that any passive FTP request will elicit a pasv_address response giving your public IP address - which usually will be a problem for your local network machines to access. So, you need to stick to active FTP access for machines inside your FTP server's network, and passive FTP for machines from outside (including your expected client **205.159.86.10**).

Could you use the attached vsftpd.conf file (I've put it in a tar file) after **backing up your own** and let us know how it goes ? I've put in your IP address, and port assignments, but turned off anonymous FTP. **tar xvf vsftpd.conf.tar** to untar the file, but you already know that.

---

### Post by rg_stephens on 2007-08-02
Yeaaaa!!
 It finally works. I've been trying to get this thing going for a long time. Thanks for your help PaulFr. 

By the way, how should the "shells" be configured for this user (the user who accesses my shared folder)? I left it as /bin/bash because that's how it was set by default, but does it make any difference? He just needs to access the folder that's public to my web server.

Robert

---

### Post by PaulFr on 2007-08-03
Good to hear it works, and glad to be of help (finally) :-)

Yes, bash is fine. Anyway, the ftp commands are all that can be used, the client cannot access or run a real shell.

---

### Post by Konundrum on 2008-07-13
One thing to note regarding the login shell granted to your FTP users.
Though connecting via FTP will not allow them to run commands outside of the scope of FTP, it is generally advisable to set these users to /bin/nologin on RH type systems and /bin/false on Debian(ubuntu) type systems. Since should a user decide to do so, and you ran openSSH, they could jump over to port 22 on an SSH client and gain access to your system where they could run most any non-root command they like. Not all that likely that your good chums would do this, but if you use weak username/password, you could be easily hacked.

---

