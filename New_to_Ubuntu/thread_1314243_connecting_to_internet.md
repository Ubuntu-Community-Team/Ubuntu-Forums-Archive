---
title: "connecting to internet"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by tonybarrett on 2009-11-04
Hi, please can someone help me. I have installed version 9.04 from a magazine disc, which seeems OK. However i can't connect to the internet, and having read through the forums, I frankly don't understand most of what is written.
Here is what I have;
USB-wired ADSL Thomson Speedtouch 330 modem
ISP: virginmedia.com
I am posting this via IE in windows xp in a dual boot mode
thanks,
tony barrett

---

### Post by ukripper on 2009-11-04
> **tonybarrett said:**
> Hi, please can someone help me. I have installed version 9.04 from a magazine disc, which seeems OK. However i can't connect to the internet, and having read through the forums, I frankly don't understand most of what is written.
Here is what I have;
USB-wired ADSL Thomson Speedtouch 330 modem
ISP: virginmedia.com
I am posting this via IE in windows xp in a dual boot mode
thanks,
tony barrett

Go to terminal --> [Click me to see where terminal is]("http://www.psychocats.net/ubuntu/terminal")

Can you post output of the following commands after running in terminal:
```
lsusb
```

```
ifconfig
```
```
iwconfig
```

---

### Post by hgraham on 2009-11-04
It is a bug.  Once you have installed 9.10  go to terminal and enter

sudo pppoeconf

enter all the info using the default where you can

Then enter

sudo pon dsl-provider

You should be connected to the internet but no icons in the panel will be displayed.  Try using firefox and see if you are connected.  You will need to enter 

sudo pon dsl-provider

whenever you log on after a restart

I hope this works for you.  It worked for me.

h

---

### Post by ukripper on 2009-11-04
Read this to setup your speedtouch modem: [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)

---

### Post by Scunnered on 2009-11-04
I am using Virgin Media as my ISP and it was necessary for me when setting up the internet connection to use password that was agreed with Virgin when my original ISP connection was made.

This is totally different from your login password. 

I am unsure about the other aspects of your system but hope this may assist

---

