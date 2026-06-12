---
title: "Providing an FTP user access to all the storage devices on the remote machine"
date: 2021-07-08
forum: Networking &amp; Wireless
---

### Post by combrink on 2021-07-08
Good day,

I would like to start of by saying that I'm as good as a newb in regards to Linux so please bear with me if this is posted in the wrong forum or if I'm asking the wrong question.

I have set up an ftp connection and created a user together with the user's /home/ directory.

However, when I connect to the remote machine through FileZilla I can only access the local drive and none of the other attached storage devices.

We want to use the remote machine as a friends and family storage device and would like to give them access to all the drives.

Is it a setting that I have to change in the vsftpd.conf file?

Thank you in advance.

---

### Post by scorp123 on 2021-07-09
FTP is insecure and unencrypted, a relic of the early 1970's. You should not be using it in 2021.

Please use SFTP instead. SFTP is a sub-protocol of SSH and FileZilla should be able to handle SFTP connections too.

---

### Post by TheFu on 2021-07-09
+1 for never using plain FTP again.  There's no need for vsftp. 

Use sFTP. Filezilla and WinSCP support it for Windows.  Almost every Linux file manager supports it on Linux, just use sftp:// as the URL on Linux.  Every networked OS has great sftp clients.

If you want to make it easier for the clients, consider using nextcloud and giving them userids on that system. This will skip the required understanding of Unix owner, group and permissions that is mandatory for all the other solutions.  Permissions in Nextcloud are controlled inside the web-GUI.  

Otherwise, you'll need to spend 45 minutes actually concentrating and learning POSIX Unix permissions.  There are hundreds of tutorials on the internet for this stuff.

If you need help with sftp, ask.  It is fairly bonehead.

---

### Post by combrink on 2021-07-13
Good day,

Thank you for the response.

I misspoke when I said FTP. I am using sftp with vsftp. (As I said I'm new to Linux.)

I set up vsftp and the user as follows:
** Install VSFTPD Server :
- Open Terminal
- sudo apt update
- sudo apt install vsftpd
- sudo service vsftpd status


** Configure Firewall :
- sudo ufw allow 20/tcp
- sudo ufw allow 21/tcp
- sudo ufw allow 40000:50000/tcp
- sudo ufw allow 990/tcp
- sudo ufw allow openssh
- sudo ufw enable
- sudo ufw status


** Create FTP User:
- sudo adduser ftpuser
- sudo mkdir /home/ftpuser/ftp
- sudo chown nobody:nogroup /home/ftpuser/ftp
- sudo chmod a-w /home/ftpuser/ftp
- sudo mkdir /home/ftpuser/ftp/files
- sudo chown ftpuser:ftpuser /home/ftpuser/ftp/files


** VSFTPD Server Configuration :
- sudo vi /etc/vsftpd.conf
listen=NO
listen_ipv6=YES
anonymos_enable=NO
local_enable=YES
write_enable=YES
local_mask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
force_dot_files=YES
pasv_min_port=400000
pasv_max_port=500000


user_sub_token=$USER
local_root=/home/$USER/ftp

On Filezilla I use the sftp:// prefix to connect but as is obvious from the setup the user will only have access to the home directory.

Filezilla does not show any of the other storage devices available on the system. 

How do I enable either the user or Filezilla to display and provide access to the other storage devices.

This is going to be a personal server and the users that will be accessing it have enough knowledge not to mess around where they shouldn't. As such I do not have qualms about giving the users access to all the drives.

On the other hand. Is it better to rather use a different application?

I appreciate your help.

---

### Post by scorp123 on 2021-07-13
> **combrink said:**
> I am using sftp with vsftp.

But why? All you need is **openssh-server** and nothing else. SFTP is a sub-protocol of SSH, any additional package or service is not needed at all.

EDIT:  "How to configure OpenSSH - for Beginners"
[https://itsfoss.com/set-up-ssh-ubuntu/]("https://itsfoss.com/set-up-ssh-ubuntu/")

Once this is installed and running you should be able to also point any suitable SCP / SFTP client such as WinSCP, FileZilla, CyberDuck etc. to your server and then transfer files anyway you want.

For outside access (e.g. by family members living elsewhere on this planet?) you will need to forward port 22 from the Internet to your installation. Ideally each family member would have their own login and their own password... or even better: their own SSH key with a passphrase.

Getting attacked by script kiddies (e.g. bored kids sitting in their Mom's basement and trying to get into your system just for the fun of it ...) is a thing, so please also install this package:

**"Fail2ban"**
[https://linuxize.com/post/install-configure-fail2ban-on-ubuntu-20-04/]("https://linuxize.com/post/install-configure-fail2ban-on-ubuntu-20-04/")

This package will auto-ban any wannabe-hacker who causes too many failed login attempts on your PC. Highly recommended. A "must have" in my opinion.

---

### Post by TheFu on 2021-07-13
I don't think vsftp provides sftp.  I think there is confusion between that an FTPs (FTP in an SSL wrapper).

The first 2 things I install on every Linux system are ssh and fail2ban.
**sudo apt install ssh fail2ban**
Then do what this post says: [Https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278](Https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278)

There is almost no downside to having fail2ban installed. It can be setup to protect other services, but out of the box, it is for ssh on port 22/tcp, which is what we want.

---

### Post by combrink on 2021-07-13
Thank you for the advice.

I already had OpenSSH installed and set up.

I've found that I was stuck on the Windows mentality of a drive letter that you navigate to instead of just mounting the drives into folders that the users can have access to.

---

