---
title: "WMP54G problems!"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by drumstick on 2006-07-28
I recently installed Ubuntu and ran into a huge problem. I'm using a wireless card to access my interenet. The card works perfectly fine in Windows XP so I know it's not the card that is having problems.

I went to this site and did exactly what was said there:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

It said driver was installed and working and hardware was working. But I couldn't access the internet. So I rebooted to see if that would work and the boot up just stops at "Configuring network interface." The only way to get back into Ubuntu is to reinstall it.

Any help in this matter would be greatly appreciated. :D

BTW, I have a Linksys WMP54G

---

### Post by bigken on 2006-07-28
take a look here it worked for me using linksys wifi pci card

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174) ;)

---

### Post by ravindran.k on 2006-07-28
Greetings!
No doubt thats a good guide.. But there are two versions of WMP54G
1. Broadcomm Based : version 4.0
2. RT61 Based :version 4.1 
 
Please check the version on your wireless card . Im using the 2nd one and so far no success with Ndiswrapper as well Linux driver RT61. Trying again now... WIll keep you posted if it works !

---

### Post by bigken on 2006-07-28
If I remember rightly it was the broadcom version I have since sold the card hope you get it sorted ;)

---

### Post by bionnaki on 2006-07-28
wmp54g also uses the rt2500 driver.
It works for me using wpa.
although I'd like to install the beta drivers for [supposed] better performance,
but I havent had any luck.

no need to use ndiswrapper though.
follow my instructions instructions: [http://www.ubuntuforums.org/showthread.php?t=161376&highlight=wmp54g](http://www.ubuntuforums.org/showthread.php?t=161376&highlight=wmp54g)

---

### Post by breezyONE on 2006-07-28
i don't know if this will help any but...
are you using the most current release?
i just did two installs in the past week and am getting confused of what i did to which system.
but i can almost swear that it automatically configured the card during the installation.

also try this [thread]("http://ubuntuforums.org/showthread.php?t=132980&highlight=wireless")
if it is version 4.1 it will help

---

