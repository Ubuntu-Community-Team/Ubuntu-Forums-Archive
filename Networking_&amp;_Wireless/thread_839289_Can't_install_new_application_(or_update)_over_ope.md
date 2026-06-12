---
title: "Can't install new application (or update) over openSSH, can sudo to root successfully"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by willemgroenewald on 2008-06-24
I have a server which successfully can "apt-get update" when I'm sitting in front of it and I'm logged in as root. I installed openSSH on it and it is working fine, I can ssh into the server and I'm also able to sudo successfully. But when I'm trying to update or install new applications when connected to it via ssh it fails to download from the repositories. Below is the output I get, I cut out the middle so to keep it shorter. Please remember when I do the same "apt-get update" when physically logged in to the server it works fine. 

I have the same problem with both Ubuntu 7.10 and 8.04 with the latest version of openSSH installed. 

Please help...Is there any settings that I might be missing. How can I ensure the connection over ssh will become true super user?

Output:
willem@willem-laptop:~$ ssh controlroom@10.101.98.44
controlroom@10.101.98.44's password: 
Linux Controlwebserver 2.6.22-15-generic #1 SMP Tue Jun 10 09:21:34 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Mon Jun 23 19:52:26 2008 from willem-laptop.local
controlroom@Controlwebserver:~$ sudo -s
[sudo] password for controlroom:
root@Controlwebserver:~# apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_ZA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_ZA
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
.........
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_ZA           
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_ZA               
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_ZA     
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_ZA       
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
/multiverse/i18n/Translation-en_ZA.bz2  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by willemgroenewald on 2008-07-07
Sorry man, no one else wants to comment, so me who is actually you is just commenting to say hi.

---

