---
title: "Can't Install Samba - Please Help!"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by novice_geek on 2006-10-29
Hello,

I just got my Ubuntu LAMP server setup, and now I am trying to install Samba so that I can use this system as a File & Print Server, (I am also doing a web and SFTP server, but those are working :) ) but I cannot get Samba to install.  When I am in an SSH console and I type: sudo apt-get install samba
I get the following:
> $ sudo apt-get install samba
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu3.1) but it is not going to be installed
         Depends: libcupsys2 (>= 1.1.99.rc2) but it is not going to be installed
  webmin: Depends: libnet-ssleay-perl but it is not going to be installed
          Depends: libauthen-pam-perl but it is not installable
          Depends: libio-pty-perl but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
$

If I type "sudo apt-get -f install samba", I get the same error. ](*,) 

If someone knows what's wrong, I would greatly appreciate it :-D 

Thanks,
Novice_Geek

---

### Post by novice_geek on 2006-10-29
Oops... I forgot to tell you some sys info...
The machine has the latest version of Ubuntu LAMP server (I downloaded it a week ago)
It is installed on an old eMachine computer...
Intel Celeron @ 500MHz
64MB RAM
Samsung CD Burner
No Floppy Drive
Maxtor 20GB Hard Drive (IDE)
Brand New Gigabit NIC
Brand New power supply (not that it matters)

I also have an HP Deskjet (3745) printer that I have hooked up, but I haven't done any install.  This is the printer that I am going to network.

Thanks for talking time to read and possible answer this :)

Novice_Geek

---

