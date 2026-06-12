---
title: "3G Connection Huawei E220"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Kevi Stubbs on 2009-01-24
I have Ubuntu 8.1 and a 3G huawie E220 vodacom Modem.
When I go to the connection Icon top righ of screen, click Vodacom under Mobile broadband, I get a message "The network connection has been disconected.
What am I doing wrong.
Kevin Stubbs

---

### Post by dj-toonz on 2009-01-24
Hi, I don't Know if this helps but I'm also having the same problem with the same modem If I log off then try to re-log on I get disconnected, then I try to log on it connects. what I normally do is pull the modem out and re-insert it then it connects first time,, the modems do work under Ubuntu 8.10 as I've used the E169, E160g & the E220 under Ubuntu, if it's saying disconnected all the time, post back & i'll try to help

---

### Post by Kevi Stubbs on 2009-01-24
My one will not conect at all when I plug in
Kevin

---

### Post by ithanium on 2009-01-24
I also have an E220 modem running on Vodafone but I can't make it work under ubuntu :|

---

### Post by diablo75 on 2009-01-24
Might check this out:  [https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220](https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220)

---

### Post by dj-toonz on 2009-01-24
Thx diablo75, you just beat me to it lol, i was going to post that web address as well, it seems that the E220 isn't a usb mass storage device dongle like the E169 & 160G usb modems, that's why them two modems work using network manager 0.70 and not the E220, how I got the E220 working in 8.1 was by installing the Vodafone connect Linux software from [https://forge.betavine.net/projects/vodafonemobilec/](https://forge.betavine.net/projects/vodafonemobilec/) it's just a case of installing the .deb files for the software & the usb mount, but you also need to install some python files as well, hope that helps

---

### Post by mbzn on 2009-01-24
hi, I also had an e220 on vodacom, it seems to give a litle trouble.
i used the "vodafone mobile connect card driver for linux" that i got from my friend. there is a couple of places to look

try
> Huawei E220:
[http://ubuntuforums.org/showthread.php?t=262867](http://ubuntuforums.org/showthread.php?t=262867)
[http://ske.sourceforge.net/html/projects/huawei/huawei_tre.html](http://ske.sourceforge.net/html/projects/huawei/huawei_tre.html)
[http://oozie.fm.interia.pl/pro/huawei-e220/index.html](http://oozie.fm.interia.pl/pro/huawei-e220/index.html)
that i got from another thread

or Google
[http://www.google.com/linux?hl=en&q=vodafone+mobile+connect+card+driver&btnG=Search](http://www.google.com/linux?hl=en&q=vodafone+mobile+connect+card+driver&btnG=Search)
[http://ezinearticles.com/?How-to-Install-a-Huawei-E220-Modem-in-Ubuntu-Linux&id=1603708](http://ezinearticles.com/?How-to-Install-a-Huawei-E220-Modem-in-Ubuntu-Linux&id=1603708)

hope this helps

---

### Post by Kevi Stubbs on 2009-01-30
> **dj-toonz said:**
> Thx diablo75, you just beat me to it lol, i was going to post that web address as well, it seems that the E220 isn't a usb mass storage device dongle like the E169 & 160G usb modems, that's why them two modems work using network manager 0.70 and not the E220, how I got the E220 working in 8.1 was by installing the Vodafone connect Linux software from [https://forge.betavine.net/projects/vodafonemobilec/](https://forge.betavine.net/projects/vodafonemobilec/) it's just a case of installing the .deb files for the software & the usb mount, but you also need to install some python files as well, hope that helps
Hi DJ Toons
I tried the link you sugested and downloaded.
 Debian, Ubuntu, Ubuntu Netbook Remix  2008-12-04 08:54 
  INSTALL.txt 798 bytes 7,331 Any text 
  usb-modeswitch_0.9.4-1_i386.deb 10 KB 6,870 i386 .deb  
  vodafone-mobile-connect_1.99.17-8_all.deb 1.23 MB 7,640 Any .deb 
The first one"usb modem switch"installed, but the second one " vodafone-mobile-connect would not.
I then ran "sudo apt-get -f install" it looked like it did the right thing.
 I then tried again with vodafone-mobile, I get a message that the python is twisted.
When you say execute the driver with:vodafone-mobile-connect-card-driver-for linux  how do i do that.
I am new to linux.
Kevin

---

### Post by rampageoberon on 2009-01-30
In my experience the Vodafone Mobile Connect Driver application can be quite tempramental.

If you are happy with a simple command line approach solution this might be helpful. Unfortunately it doesn't allow SMS but is quick and very simple to connect.

First modify/create your wvdial config file at '*/etc/wvdial.conf*'. Mine reads as follows.

```
[Dialer Pin]
Init1 = AT+CPIN=**YOURPIN**
Modem = /dev/ttyUSB0
Baud = 9600

[Dialer Connect]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = **PHONENUMBER**
Modem = /dev/ttyUSB0
Username = **YOURUSERNAME**
Password = **YOURPASSWORD**
Baud = 9600
Dial Command = ATDT
Stupid Mode = 1
```

To connect you need to run the following line

```
wvdial pin && wvdial connect
```

To get the Phone Number, Username and Password the easiest way is to contact the provider support and ask them.

I hope this helps

EDIT: If you don't have the pin you can omit the [Dialer Pin] section. To connect just run

```
wvdial connect
```

---

