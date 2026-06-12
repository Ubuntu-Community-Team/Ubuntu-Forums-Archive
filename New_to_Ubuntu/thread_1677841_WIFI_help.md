---
title: "WIFI help"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by Bo Sischo on 2011-01-29
Ok, I have a dell inspiron 1501 with built in windows Xp.
I've installed ubuntu 10.10.
Everything seems to work save the built in wireless card.
Now I know that these don't work and that you have to install ndiswrapper and all that.
SO I also found and installed the drivers. Mine is called bcmwl5.inf.

Yet the computer doesn't recognize the wireless card and the wifi light isn't lit.

SO what do I have to do next?

PLEASE HELP!

---

### Post by Mark_in_Hollywood on 2011-01-29
Have you read the How-To at Ubuntu for Broadcomm wifi?

[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)


please make sure that this How-To applies to your product. You don't give enough info in your post for me to do that for you.

Also see a weblog

[http://www.ubuntu1501.com/](http://www.ubuntu1501.com/)

about your laptop and specifically.

Sorry I can't be more help.

---

### Post by smithr.michael1997 on 2011-01-29
Run:
```
lspci | grep -i net
```
and paste the output into a reply. This will give us a better idea of how to help you by listing your WiFi card. You may need to compile a module from Broadcom.

---

### Post by Bo Sischo on 2011-01-30
Ok this is my wlan card info.
05:00.0 Network controller: broadcom corporation bcm4311 802.11b/g wlan (rev 01)
08:00.0 Ethernet controllr: broadcom corporation bcm4401-bo 100base-tx (rev 02)

Is there any other code I could use to give you more information?

Thanks!

---

### Post by Bo Sischo on 2011-01-30
Ok this is my wlan card info.
05:00.0 Network controller: broadcom corporation bcm4311 802.11b/g wlan (rev 01)
08:00.0 Ethernet controllr: broadcom corporation bcm4401-bo 100base-tx (rev 02)

Is there any other code I could use to give you more information?

Thanks!

---

### Post by Bo Sischo on 2011-01-30
Yes I've been all through that thread and thus far I've come up bupkis.
What do you need to know so that you can help me?

---

### Post by gandaran on 2011-01-30
did you check in system » administration » additional drivers for the broadcom wireless driver?
you have to connect the laptop to ethernet cable internet and update the software package list (sudo apt-get update) then if theres a broadcom driver available all you have to do is enable it.

---

### Post by Bo Sischo on 2011-01-30
don't have a wired connection.
But when I went to system/administration/windows wireless drivers, I have my driver installed. It's the driver that came with the laptop I just made a copy and transfered it over. 
But the wifi light isn't lit yet when I click on the network icon is says wireless enabled.

---

### Post by Bo Sischo on 2011-01-30
don't have a wired connection.
But when I went to system/administration/windows wireless drivers, I have my driver installed. It's the driver that came with the laptop I just made a copy and transfered it over. 
But the wifi light isn't lit yet when I click on the network icon is says wireless enabled.

---

### Post by lkraemer on 2011-01-31
Perhaps this HOWTO: on Broadcom will give you the necessary steps to
choose one method and get it working.  I'd not worry about the Wifi LED
at the moment.  It may fully function with the LED in the incorrect color.

[http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+broadcom)

Post your chosen method, along with what you have done so far via the
History command and we'll proceed.  Shouldn't take long.

ie...in a Terminal Command Window:
history > junk.txt

If you have tried a couple of different ways, you will have to back out
those changes, to get the one you have chosen to work correctly.


LK

---

### Post by Mark_in_Hollywood on 2011-02-03
While this may not be the same for you, my public library has free internet, via ethernet cable.

---

