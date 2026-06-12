---
title: "having problems with dpkg and downloading limewire"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by mrscocagne on 2009-01-22
ok hi there i am having a problem with installing new updates and downloading limewire i read all the post with the dpkg and this is what it tells me when i do the codes 

cocagne@cocagne-desktop:/var/lib/dpkg/updates$ sudo dpkg --configure -a
[sudo] password for cocagne: 

cocagne@cocagne-desktop:/var/lib/dpkg/updates$ 
cocagne@cocagne-desktop:/var/lib/dpkg/updates$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [44.0kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release [51.2kB]       
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [52.2kB]      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages [275kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages [1785B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources [16.0kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources [571B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [21.0kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources [3589B]   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages [1330B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources [584B]  
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages [5770B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources [85.2kB]     
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources [1701B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages [39.9kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources [9247B]  
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages [3180B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources [1145B]
Fetched 614kB in 7s (79.8kB/s)                                                 
Reading package lists... Done
cocagne@cocagne-desktop:/var/lib/dpkg/updates$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
cocagne@cocagne-desktop:/var/lib/dpkg/updates$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
cocagne@cocagne-desktop:/var/lib/dpkg/updates$ y
bash: y: command not found
cocagne@cocagne-desktop:/var/lib/dpkg/updates$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
cocagne@cocagne-desktop:/var/lib/dpkg/updates$ wget -c [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
--2009-01-21 23:07:44--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
Resolving fpdownload.macromedia.com... 96.7.18.70
Connecting to fpdownload.macromedia.com|96.7.18.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3962157 (3.8M) [application/x-gzip]
install_flash_player_10_linux.tar.gz: Permission denied

Cannot write to `install_flash_player_10_linux.tar.gz' (Permission denied).
cocagne@cocagne-desktop:/var/lib/dpkg/updates$ 

I don't know how to grant it permission. I am the root user please help

---

### Post by Ahadiel on 2009-01-22
You aren't the root user. Prefix your commands with *sudo* to grant the process root permissions.

Also, Frostwire is a better alternative to Limewire.

---

### Post by Eisenwinter on 2009-01-22
Use "sudo" in front of the commands.

> cocagne@cocagne-desktop:/var/lib/dpkg/updates$ wget -c [http://fpdownload.macromedia.com/get...0_linux.tar.gz](http://fpdownload.macromedia.com/get...0_linux.tar.gz)

You are trying here, to download a file, into a subdirectory on the root filesystem.

You cannot do this action as a regular user.

Use **sudo** wget -c <file>, if you wish to download it there.

I suggest you download it to your /home/ directory anyway.

Open terminal:

```
cd ~
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz

```

If you need installation help, keep posting here.

---

### Post by ugm6hr on 2009-01-22
> **mrscocagne said:**
> I don't know how to grant it permission. I am the root user please help

Learn about sudo: [http://www.psychocats.net/ubuntu/security#sudomoreinfo](http://www.psychocats.net/ubuntu/security#sudomoreinfo)

And then, before anything else:
```
sudo apt-get install -f
```

---

### Post by cariboo on 2009-01-22
Just one other suggest, to install flash, java and most of the codecs you need to play most audio/video media install the ubuntu-restricted-extras meta package. You need java in order to run frostwire anyhow.

Jim

---

### Post by mrscocagne on 2009-01-22
ok i tryed the cd one that you told me and this is what it told me


cocagne@cocagne-desktop:/var/lib/dpkg/updates$ cd ~
cocagne@cocagne-desktop:~$ wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux).
--2009-01-21 23:34:52--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux).
Resolving fpdownload.macromedia.com... 72.246.190.70
Connecting to fpdownload.macromedia.com|72.246.190.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-01-21 23:34:53 ERROR 404: Not Found.

cocagne@cocagne-desktop:~$ 

 so now what do i do i am very thankful that you are all helping  me thank you

---

### Post by mrscocagne on 2009-01-22
hey its me again here is another question can i download aim useing aim

---

