---
title: "Broadband USB Modem help in 9.04"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by 1993cb7 on 2009-05-30
Trying to connect my blackberry as a USB modem in 9.04. Never was able to do this in previous distros but i see 9.04 has a broadband modem option under network connections. I choose tmobile and set it up and i never have the option of choosing it when i click the net icon in upper right corner. 

I had a friend help me install barry and set it up and i only got so far with that, see below. 

Please help!!!

the phone restarts and terminal says:

exception in IPmodem: Datareadthread:exception caught in main():Error in USB_bulk_write script/usr/sbin/pppob finished (pid 18747), status =0x1

Modem hangup

connect time 0.5 minutes.
sent 4274 bytes, recieved 7524 bytes
script /etc/ppp/ip-down started (pid 18898 )
connection terminated
waiting for 1 child processes........
script/etc/ppp/ip-down,(pid 18898 ),
status =0x0


?????

What if anything do i need to post here?


Thanks in advance.

---

### Post by freeman2000 on 2009-05-30
I don't know if this will help you, but I'm running Verizon's 3G USB mobile broadband.  I had to go to System --> Admin --> Hardware Drivers and install ("activate") a proprietary driver for QualComm CDMA Broadband in order to get my broadband 3G USB modem to work.  Now when I right-click the network icon in the panel, I then click on the line that says "auto" broadband to connect.  Good luck.

---

### Post by 1993cb7 on 2009-06-01
> **freeman2000 said:**
> I don't know if this will help you, but I'm running Verizon's 3G USB mobile broadband.  I had to go to System --> Admin --> Hardware Drivers and install ("activate") a proprietary driver for QualComm CDMA Broadband in order to get my broadband 3G USB modem to work.  Now when I right-click the network icon in the panel, I then click on the line that says "auto" broadband to connect.  Good luck.

Well when i went and clicked through there it said no drivers found on this system so then i tried plugging the phone in and clicking it again and again it found no drivers so im not sure if im doing something wrong or what.

---

### Post by LewRockwell on 2009-06-01
[http://ubuntuforums.org/showthread.php?t=617811](http://ubuntuforums.org/showthread.php?t=617811)

---

### Post by LewRockwell on 2009-06-01
[http://groups.google.com/group/blackberryonlinux](http://groups.google.com/group/blackberryonlinux)

---

### Post by 1993cb7 on 2009-06-01
> **LewRockwell said:**
> [http://ubuntuforums.org/showthread.php?t=617811](http://ubuntuforums.org/showthread.php?t=617811)

> **LewRockwell said:**
> [http://groups.google.com/group/blackberryonlinux](http://groups.google.com/group/blackberryonlinux)


Neither of these really help. 

The first i tried already and couldn't get it to work.

The second really doesn't offer much.

I am not trying to sync my BB, i just want to tether it. 

Last time i had a problem getting my USB wireless adapter to work with linux and this was with 8.10 and now it works fine.

I guess one day this will work fine too. 
:(

---

### Post by lswb on 2009-06-01
IIRC a blackberry needs to have a a proram running to act as a tethered modem. I think it is called "Blackberry Handheld Manager" or something similar. These links may be out of date but maybe will help you find a solution:

[http://www.blackberryfaq.com/index.php/Using_BlackBerry_As_Modem](http://www.blackberryfaq.com/index.php/Using_BlackBerry_As_Modem)

[http://www.berry4all.com/home](http://www.berry4all.com/home)

---

### Post by 1993cb7 on 2009-06-02
> **lswb said:**
> IIRC a blackberry needs to have a a proram running to act as a tethered modem. I think it is called "Blackberry Handheld Manager" or something similar. These links may be out of date but maybe will help you find a solution:

[http://www.blackberryfaq.com/index.php/Using_BlackBerry_As_Modem](http://www.blackberryfaq.com/index.php/Using_BlackBerry_As_Modem)

[http://www.berry4all.com/home](http://www.berry4all.com/home)

Yea the first link is for Windows, not Linux. 

And the second one i tried already but had no luck, if someone could explain in better detail what needs to be done it might help.

I ran those commands and downloaded the file but it gave me an error somewhere.

And as far as something running in the background, unless i use Wine, i dont think its possible. Blackberry doesnt have anything for Linux yet.

---

### Post by 1993cb7 on 2009-06-02
Ok well i went through the second link again and it worked. 

Works great actually, getting DSL speeds. 

Just go to [www.berry4all.com](www.berry4all.com) and follow the instructions.

---

