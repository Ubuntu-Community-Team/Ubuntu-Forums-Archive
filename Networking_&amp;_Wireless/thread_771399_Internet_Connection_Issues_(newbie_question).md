---
title: "Internet Connection Issues (newbie question)"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by floppo on 2008-04-27
hey guys - when i use Ubuntu straight from the CD the network connection has no issues. but when i launch from the install despite my numerous attempts be able to connect to the internet, no luck

i am installing clean with 8.04 on a 500gig drive with dual quad core and 4gigs of ram. 

i use RCN (cable modem) and so its all dhcp and causes no issues when i run off of the cd. 

any ideas of things to try?

---

### Post by superprash2003 on 2008-04-27
please go to the terminal and type ifconfig and post results here

---

### Post by floppo on 2008-04-27
hm... one thing i'm struggling with is how to copy paste information from the computer that has no network into these forums. i toggle over to my xp computer where i have a connection, but have no idea how to take long config copies over to these forums - any suggestions on how people get around that? 

in short, after doing a a little more tinkering its clear that i'm not getting an IP address when I run from the installed version. when i run from the live cd, its having no issues getting that. 

i also noticed at the endo f the install a quick flash of linux/dos prompt like text saying some errors with the network manager

i've reinstalled, and tried doing what was recommended from here: 
[http://ubuntuforums.org/showthread.php?t=691372&page=2](http://ubuntuforums.org/showthread.php?t=691372&page=2)

but no luck yet. thanks for your response

---

### Post by floppo on 2008-04-27
hey guys - i ran recovery mode instead of the full version at prompt, and after having made the changes listed in the link i gave (not sure if that helped or not) on restart - i have a connection and am in. :) 

hope this might help someone

---

### Post by floppo on 2008-04-27
oh no.... i updated a nvidia driver as suggested, rebooted, and no internet connection again. reboot through recovery mode, no luck either... so i'm back to zero

---

### Post by x4KlV2OI on 2008-04-27
Are you using wireless or Cable?

If you are using wireless, i had a similar problem .

---

### Post by floppo on 2008-04-27
this is for a cable modem.

---

### Post by x4KlV2OI on 2008-04-28
Ahh, cable modems.  Im sorry, but i can't help you.

---

### Post by superprash2003 on 2008-04-28
ok since you are not getting an ip.. you first need to make sure you get one.. go to system->administration network and choose the LAN card(eth0 mostly) then click on properties and set it to DHCP.. and see if you get an ip in the ifconfig output.. if you dont then try typing an ip address manually..

---

