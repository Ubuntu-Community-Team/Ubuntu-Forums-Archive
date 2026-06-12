---
title: "can't get vlc 1.00 to install"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by DarinB on 2009-09-16
I have tried what it says on this site, i would like to add vlc 1.00 any ideas? or a detailed how to. i had it before a clean re install of jaunty

---

### Post by zeroseven0183 on 2009-09-16
How did you install VLC the first time you tried?

Open **Synaptic** (System > Administration > Synaptic Package Manager).
In Settings > Repositories, make sure you have a "multiverse"  repository activated.


 Search for **vlc** and install it.
You should also install **vlc-plugin-esd, mozilla-plugin-vlc (and libdvdcss2)**.


Or if you want to do it in the Terminal, you need to check that a "multiverse" mirror is listed in your /etc/apt/sources.list.

```

sudo apt-get update
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

```

---

### Post by DarinB on 2009-09-16
when i do this sudo apt-get update 
i get this response and multiverse is there in origin
the end of this says it failed don't know why

darin@darin-desktop:~$ sudo apt-get update
[sudo] password for darin: 
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty Release.gpg
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty Release
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
darin@darin-desktop:~$

---

### Post by DarinB on 2009-09-16
ok i unchecked the part in software souces that says it needs cd then i got this so if i have vlc 1.00 where is it???
darin@darin-desktop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Reading package lists... Done
darin@darin-desktop:~$ sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc is already the newest version.
vlc-plugin-esd is already the newest version.
mozilla-plugin-vlc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
darin@darin-desktop:~$

---

### Post by oldos2er on 2009-09-16
You should have a vlc menu entry in Applications, Sound & Video.

---

### Post by zeroseven0183 on 2009-09-16
That's a good update. You should probably see VLC in the Applications.

---

### Post by DarinB on 2009-09-16
well i didn't but i did this step by step holding my breath and it worked, whew!!!!
[http://tuxarena.blogspot.com/2009/07/how-to-install-vlc-10-from-ubuntu-ppa.html](http://tuxarena.blogspot.com/2009/07/how-to-install-vlc-10-from-ubuntu-ppa.html)

---

### Post by zeroseven0183 on 2009-09-16
Good for you! Enjoy!

---

### Post by DarinB on 2009-09-16
yeah thanks VLC 1.00 rocks the best they have had in a few generations.

---

