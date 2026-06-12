---
title: "cant make directory for wireless"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by loserkid_1 on 2006-10-22
i am setting up my wireless card (belkin f5d7000) from this guide
[http://www.ubuntuforums.org/showthread.php?t=132980]("http://www.ubuntuforums.org/showthread.php?t=132980")
scroll down for the dapper section.
when it gets to "sudo mkdir /etc/Wireless/RT61STA"
i get this error message "mkdir: cannot create directory `etc/Wireless/RT61STA': No such file or directory"
can someone tell me how to do this bit or what im doing wrong as im a complete noob. thanks

---

### Post by bettlebrox on 2006-10-22
The /etc/Wireless directory doesn't exist?

---

### Post by ser1alsn1per on 2006-10-22
hi i have the same pci wireless card this is how i get it to work follow these instructions 

[http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm4306](http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm4306)


but use this driver   if you have the ralink chipset 

[ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip](ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip)

but if you don't have the ralink one the complete list of drivers are here just scroll to your belkin driver install it 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

when it says hardware present and installed in fwcutter 

go to system administration networking 

then ur wireless --- propertys

if you have a wpa key i recomend you change it to wep untill you get it working 

enable connection type your network name 
hexidecimal then type your WEP key 
then click dhcp 

activate 

default gateway dev ath0 or wan0    or what ever its called 


if you want wpa you need to set up the wpa suplicant if you make this then download wifiradar click wpa and point it at the suplicant 

hope it helps

---

