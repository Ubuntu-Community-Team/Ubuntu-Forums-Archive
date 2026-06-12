---
title: "Can't install bcm43xx"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by poot on 2007-11-27
i just recently install ubuntu 10.7 (from the website) on my laptop. It's a kinda old laptop and it doesn't have a built in wireless card. I use a linksys card of some type and when i look in the restriced driver manger it says i need to install bcm43xx-fwcutter. When i click enable it says it can't find a package required to activate the driver. I tried typing it  into the terminal and it told me to type in sudo get apt install something or another and when i did it sayed it couldn't find the package. I am on my desktop computer right now...i would be extremely thankfull if someone could help me fix my problem. ^_^

---

### Post by x64Jimbo on 2007-11-28
Have you enabled the additional repositories in the "Software Sources" dialogue under System -> Administration ? You should be able to install whatever firmwares you need if you enable the non-free repositories.

---

### Post by poot on 2007-11-28
I went to software sources and in the first tab that says ubuntu software it has a lot of little checkmarks and i enabled them all and when i hit close it said that i needed a working internet connection to use them.

---

### Post by spd106 on 2007-11-28
You need to download the bcm43xx-fwcutter package and firmware file, neither of these are in the install CD. 

There are instructions for an indirect install on this help wiki page. [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

---

### Post by poot on 2007-11-28
That website says that the bcm43xx-fwcutter comes with a .deb file...the one on the website gives you a weird package....no deb file in it

---

### Post by spd106 on 2007-11-29
When you click through to the Ubuntu packages page you need to scroll down to where it says 'Download bcm43xx-fwcutter' and click on your architecture.  This will most likely be i386, unless you have a 64bit install.

Then you can select the .deb file from a download mirror near your location.

You are right that it's a little tricky for first time users, so I'll update the wiki page with some direct links.

---

### Post by poot on 2007-11-29
uhhh...ok i got the .deb files from the site ( i was clicking the wrong link) and when i double clicked it it said that there was a major error in my file system. Something with the sources.list.....the only thing i did to the software sources is click add cd and put in my ubuntu cd......

---

