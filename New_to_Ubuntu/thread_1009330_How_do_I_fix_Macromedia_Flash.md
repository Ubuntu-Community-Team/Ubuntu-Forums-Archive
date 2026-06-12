---
title: "How do I fix: Macromedia Flash"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by TechDragon on 2008-12-12
I cannot view flash media, I have 8.10 ubuntu, I have installed the restricted extras, firefox reports them as installed. But no youtube, no escapist magazine, no flash content.

Please help, I don't know where to start, it has always just worked.

---

### Post by tech9 on 2008-12-12
> **TechDragon said:**
> I cannot view flash media, I have 8.10 ubuntu, I have installed the restricted extras, firefox reports them as installed. But no youtube, no escapist magazine, no flash content.

Please help, I don't know where to start, it has always just worked.

try this link... 
 [http://get.adobe.com/**flashplayer**/otherversions/]("http://get.adobe.com/flashplayer/otherversions/") 
 Select Linux from the drop down 
 Select the tarball package 
 Download it to your desktop 
 Extract the package 
 open a terminal... 
 change paths to the packages directory 
 example cd /home/user_name/Desktop/install_flash_player_9_linux 
 
to install 
 type 
 ./name of package 
 example 
 ./**flashplayer**-installer 
 
hit enter & the rest is history 
 the install walks you through the install process 
 
Hope this helps, 
 
Tech9

---

### Post by ibuclaw on 2008-12-12
Enable your partner repository.

If it isn't in your sources list, add it:
```
deb http://archive.canonical.com/ubuntu/ hardy partner
```
And adobe's own maintained version of flash is there
```
sudo apt-get update && sudo apt-get install adobe-flashplugin
```
Regards
Iain

---

### Post by philinux on 2008-12-12
Find out where it's installed using

locate libflashplayer.so

Heres's my output.
```
sudo locate libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
```

To check in about : plugins got to about: config and change the preference **plugin.expose_full_path** to true.

---

