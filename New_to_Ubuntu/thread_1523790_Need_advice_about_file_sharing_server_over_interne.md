---
title: "Need advice about file sharing server over internet"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by chaotik on 2010-07-04
Hi.  I am new to this, and am trying to decide what is the best program to use to share a large number of pdf technical articles over the internet (mostly between myself from home to work).  

I set up an ebox but it was way to difficult having to upload ~ 13,000 individual files.  So now I have a Ubuntu server, and am trying to figure out whether I should be using Samba, Webmin, vsftpd, or exactly what.  Most of the information I have found deals with home servers connecting computers at one location.


I already have all the files loaded onto my server at home.  I will be using a windows machine at work that I do not have any administrative privileges on.  

Thanks!

---

### Post by gordintoronto on 2010-07-04
The obvious answer is FTP. Most ISPs do not allow customers to run a server, is yours one of them? Do you have a static IP address?

---

### Post by handydan918 on 2010-07-04
There is no easy answer to this, because you are trying to do something complicated. 
1) Agree with the previous poster. FTP is the obvious choice. I use proftpd (in the repos...)

2) If you are behind a router, you will need to forward a port to your ftp server. Not all routers allow this, Netgear is my choice.

3)You will need either a static IP, or something like [www.dyndns.com](www.dyndns.com) which I have been using for some time.

Good luck.

---

### Post by bodhi.zazen on 2010-07-04
If you want one-way transfers I suggest http. For two way transfers , use ssh . Windows has a graphical client, winscp.

If you use ssh, be sure to secure the server (use keys, disable passwords, use denyhosts / fail2ban / or iptables).

FTP will also work, but is less secure, more so if you allow uploads.

I advise against samba or NFS over the internet.

---

### Post by handydan918 on 2010-07-04
> **bodhi.zazen said:**
> If you want one-way transfers I suggest http. For two way transfers , use ssh . Windows has a graphical client, winscp.

If you use ssh, be sure to secure the server (use keys, disable passwords, use denyhosts / fail2ban / or iptables).

FTP will also work, but is less secure, more so if you allow uploads.

I advise against samba or NFS over the internet.

Good advice. SSH is a good option, and the PUTTY client will work well with windows. More secure than ftp, as stated.

---

### Post by Garthhh on 2010-07-04
there is of course the hardware option
Keep the files on an external hard drive

---

### Post by Palanthas on 2010-07-04
There is also the online storage option. My particular favorite is [Dropbox]("www.dropbox.com"). Which has a program that will run on Mac, Windows, and Linux. You could install it on you home Ubuntu machine and on the work PC. It would then synchronize your files between all your computers that have the dropbox app and their website.

You mentioned that you don't have admin rights at work so you might not be able to install the dropbox app but you can just jump to the dropbox website and get the files from your account. It gives you 2gigs of free space.

---

### Post by chaotik on 2010-07-04
Thanks for everyone's suggestions.

I have already configured my router, and there is no issue with port forwarding.  I have a "static ip" through dyndns.   

As I mentioned, I had ebox configured but it was just too cumbersome.   Could only up or download one file at a time. 

I want to access are over 15 gigabytes, so unless I pay a monthly or annual fee, dropbox (and others I believe) have a limit of 2 gigs.  

I need two way transfers, and cannot use a portable flash drive or hard drive (not allowed at work).  I am not anticipating anyone one else using this server.   Security, although important, is less of an issue as none of the files are "sensitive" and I have plenty of complete backups.  The router and ISP I use at home on this network is a  completely separate company, ISP and router from what me and my family use at home, so no issue there either.

Unfortunately I cannot install any programs on my work computer, and do not have administrative privileges.

---

### Post by bodhi.zazen on 2010-07-04
ssh clients (putty and winscp) are portable and do not require installation.

If you use http or ftp you should also be just fine (firefox or IE).

---

### Post by aust77 on 2010-07-04
> **Palanthas said:**
> There is also the online storage option. My particular favorite is [Dropbox]("www.dropbox.com"). Which has a program that will run on Mac, Windows, and Linux. You could install it on you home Ubuntu machine and on the work PC. It would then synchronize your files between all your computers that have the dropbox app and their website.

You mentioned that you don't have admin rights at work so you might not be able to install the dropbox app but you can just jump to the dropbox website and get the files from your account. It gives you 2gigs of free space.

Very much so agreed! I use Dropbox on my Desktop and Laptop to transfer files easily. It works on Ubuntu perfectly.

Cheers,


aust77

---

