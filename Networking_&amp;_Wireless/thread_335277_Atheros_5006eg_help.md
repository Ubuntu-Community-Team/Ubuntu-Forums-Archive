---
title: "Atheros 5006eg help"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by sjb05004 on 2007-01-10
Just wondering if anyone has any information or suggestions about how to get this card working.  It will not show up in network manager.  It does however seem to show up in the devices list.  I have used ndiswrapper with the windows driver in Mandriva 2007 and had success, but have yet to have  success in Ubuntu.  Any suggestions would be helpful.

---

### Post by Andrew Smith on 2007-01-13
Hi,
i had problems with this card, too! I dowloaded the LATEST driver from: 

[http://snapshots.madwifi.org/](http://snapshots.madwifi.org/)

and then:
removed any existing files from:

/lib/modules/2.6.17-10-generic/net/

after it i still couldn't get it work [-(  because there were two modules (ath_hal, and wlan) still in use (the error message was something like: versions are not matching [-X  , or stuff like that.)
so: 

rmmod wlan
rmmod ath_hal

(and any other module that you know: created by older version on madwifi)

after it:

make
make install
modprobe ath_pci

[-o< [-o< 
thanks to God:
[-o< [-o< 
all is good:-\" \\:D/

---

### Post by sjb05004 on 2007-01-16
What is the best way to remove those because:

  bo@bo-laptop:~$ rmmod wlan
ERROR: Module wlan is in use by ath_pci,ath_rate_sample
bo@bo-laptop:~$ rmmod ath_hal
ERROR: Module ath_hal is in use by ath_pci,ath_rate_sample
bo@bo-laptop:~$

---

### Post by Andrew Smith on 2007-01-19
> **sjb05004 said:**
> What is the best way to remove those because:

  bo@bo-laptop:~$ rmmod wlan
ERROR: Module wlan is in use by ath_pci,ath_rate_sample
bo@bo-laptop:~$ rmmod ath_hal
ERROR: Module ath_hal is in use by ath_pci,ath_rate_sample
bo@bo-laptop:~$


i :-k first you should rmmod those that are using your ath_hal, and wlan:
so: 

i guess, you should start it with, (it's one of the main modules of madwifi): 

rmmod ath_pci     

then follow it with:
 

rmmod ath_rate_sample

, and then all those that was created by the former (built in) version of madwifi.

there is a list of created modules in either the readme file, or in the install file. ALL THOSE MUST be REMOVED, because they cause vesion mismatch with the newest madwifi dirver...

if it is possible, then follow the instructions i wrote in my first reply

pls let me know if it worked!

---

### Post by deso on 2007-03-28
i use my laptop at multiple coffee shops, is there a way to set it up to automatically detect the network in range like windows or do you have to manually go in everytime you go somewhere and type in the settings?

---

### Post by stchman on 2007-03-30
> **sjb05004 said:**
> Just wondering if anyone has any information or suggestions about how to get this card working.  It will not show up in network manager.  It does however seem to show up in the devices list.  I have used ndiswrapper with the windows driver in Mandriva 2007 and had success, but have yet to have  success in Ubuntu.  Any suggestions would be helpful.

My laptop has the same card for the built in wireless.

Use the procedure on my website to get that card up and running.  It uses the madwifi drivers.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

This will get it going with wireless encryption to boot.

---

### Post by stchman on 2007-03-30
> **deso said:**
> i use my laptop at multiple coffee shops, is there a way to set it up to automatically detect the network in range like windows or do you have to manually go in everytime you go somewhere and type in the settings?

Install the network manager.  This will give you a drop down to see available networks.  Remember, if they broadcast their SSID then you won't detect them without a sniffer.

---

