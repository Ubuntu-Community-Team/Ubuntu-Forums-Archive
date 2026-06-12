---
title: "FTP server using tasksel in Karmic"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by RichardCL on 2009-11-09
Dear Forum,

I'm just getting started on a project to replace my external paid servers with an in-house solution. Webserver is up and running using the tasksel LAMP option.

Today's project is ftp/sftp. I've just installed ftp using tasksel but I'm not even sure which ftp that installs.

I want to create three levels of security:

1. anonymous read-only ftp to a public directory on the machine for anyone from the internet and local domains.

2. User specific access to directories on my web-server e.g. /var/www/customer1/ftp  /var/www/customer2/ftp such that only the specific customer can read files and only with a user and password. The customers also access the same directory with http and should use a password. Some customers read-only and some read-write.

3. SFTP/SSH read-write for the entire machine for my laptop from the internet and local network.

I've read a series of tutorials on proftpd and vsftpd. I'm not sure which one to use (or both?). Security is most important although I do have a firewall. I'm planning to port-forward my hardware firewall 20 and 21 to the server.


TIA



Richard

---

### Post by RichardCL on 2009-11-10
Hi Forum,

I've settled on vsftpd for the moment since I'm using apache and I want to limit users to specific http and ftp locations.

I found a tutorial [here]("http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/") which seems to show what I want but it seems out of date since the files are no longer available.

Can anyone point me to something more useful?


Rich

---

