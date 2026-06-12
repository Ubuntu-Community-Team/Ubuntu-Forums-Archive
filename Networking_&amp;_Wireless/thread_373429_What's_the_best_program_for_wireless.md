---
title: "What's the best program for wireless?"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by steveyos666 on 2007-03-01
It seems Ubuntu detects my wireless card, so this might mean I can finally get wireless working. I upgraded to Feisty and at the top right up by the volume and stuff there's now a second icon with the two monitors that has wired network and wireless networks, but that's blank. I tried going to connect to other wireless network and typing in my network's name and password but it's not working that way. 

I've been cursed with the worst laptop ever created (Compaq Presario V5101US which I'll have to say this is a do-not-buy classic piece of technology, especially because of the ati radeon xpress 200m which is one of the few reasons I will be switching to nvidia with my new laptop) , and the good ol' AirForce One... BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller is what it says under device manager...

I've tried programs like ndiswrapper but I could never get any good instructions. If you think I should use something like that, please provide a tutorial and not just a link to the program or something :guitar:

---

### Post by solar george on 2007-03-01
I used this tutorial,
[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318]("http://www.ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318")

---

### Post by steveyos666 on 2007-03-01
**./ndiswrapper_setup: 1: Syntax error: Unterminated quoted string** ehhhh I don't know what that means but thanks for the link.. I'll post it in that thread and see what people say :/

```
f@f-laptop:~$ cd ~/Desktop
f@f-laptop:~/Desktop$ tar -xf bcm4318*.tar.gz
f@f-laptop:~/Desktop$ sudo ./ndiswrapper_setup
Password:
Starting ndiswrapper install...
If you have any package managers open (i.e. Adept or Synaptic or apt-get),
Please close them now.
Pausing for 10 seconds - please read the message.
./ndiswrapper_setup: 1: Syntax error: Unterminated quoted string
f@f-laptop:~/Desktop$ 


```

---

### Post by Brian625 on 2007-03-02
I have a Compaq 5201us with the same broadcom drivers. I documented my wireless install and stored the drivers on my website. Feel free to try.
[http://www.ubuntuguides.net/wireless.asp]("http://www.ubuntuguides.net/wireless.asp")
let me know if it works for you.

---

### Post by FIONEX on 2007-03-02
Man..wireless and ubuntu don't mix.  Well, not ubuntu out of the box (or off the cd).
It's about time they start shipping ubuntu with basic wireless necessities that hava WEP, WPA, and VPN.

Follow these instructions, but when you get to the end DONT RESTART, just do the "/init.rc/dbus restart" command. After you do that, run "nm-applet" and you're all good.
[http://www.debianadmin.com/enable-wp...ntu-linux.html](http://www.debianadmin.com/enable-wp...ntu-linux.html)

---

