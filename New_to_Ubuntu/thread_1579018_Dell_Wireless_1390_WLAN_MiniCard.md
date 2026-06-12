---
title: "Dell Wireless 1390 WLAN MiniCard"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by llyrroberts on 2010-09-21
Hello

I have installed a fresh/clean copy of UBUNTU on my dell 6400.
Everything works great apart from my WIFI.
I have a Dell Wireless 1390 WLAN MiniCard is there an easy way to get it working without using code. I have downloaded the windows XP driver for it.

I have tried to follow this but can't get my head around it.

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

Thanks Llyr

---

### Post by ibizatunes on 2010-09-21
Dont think so not without typing these commands
open up a terminal
application > accessories > terminal 
copy each line in (carefully) and hit enter
it looks a very well writen how to....
the command line isnt that scary, just be brave!!

---

### Post by llyrroberts on 2010-09-22
> **ibizatunes said:**
> Dont think so not without typing these commands
open up a terminal
application > accessories > terminal 
copy each line in (carefully) and hit enter
it looks a very well writen how to....
the command line isnt that scary, just be brave!!

I'll have a go. How do I put in my directory where i have put the file?

---

### Post by migs73 on 2010-09-22
Have you tried to connect using a cable an then goto System->Administration->Hardware Drivers and select the one for your wireless.
Disconnect your cable and enable your wireless.

---

### Post by anewguy on 2010-09-22
The post you were looking at/pointed to is ancient.  There is no need to compile ndiswrapper - just use it as it is.  If you want to use ndiswrapper (it works fine, it's just that others prefer native or restricted drivers where possible), just do the following:

- place your Windows driver .sys and .inf files on your Ubuntu desktop

- with Ubuntu booted, put the LiveCD in your drive.  It may say software disk found - is so, just cancel that.

- using "Places" navigate to the /pool/main/n/ndiswrapper folder on the CD.

- double-click ndiswrapper common to begin its' installation and wait for it to finish.

- double-click ndiswrapper utilities to begin its' installation and wait for it to finish.

- navigate to the /pool/main/n/ndisgtk folder on the CD

- double-click ndisgtk to begin its' installation and wait for it to finish.

Go to System/Administration/Windows Wireless Drivers to start ndisgtk. Click add [or maybe it's "new"], point it to the .inf file on your desktop, and ok it.  That should install the wireless driver.

Right-click on the network manager icon and be sure that "Enable Wireless" is checked.

Left-click on the network manager icon and see if any wireless networks now show.

Remember that if you use MAC filtering and/or any type of encryption with your router you must match that.

Okay, that's how to do it in ndiswrapper.  However, I thought I had seen others getting this working without that.

In a terminal, type:

lshw -C network <press enter> 

lspci <press enter>

lsusb <press enter>

Copy and paste those outputs back here for us to review and give you guidance.


BTW - if you can, hard-wire your PC to the router temporarily and do the following:

- in a terminal window:  sudo apt-get update <press enter> and wait for it to finish

- check in System/Administration/Hardware Drivers and see if there is a driver for your wireless listed there - if so, enabled it.  If this starts downloading something wait for it to finish.

- physically disconnect the hard-wire connection

- follow the above for checking network manager, etc..

Dave ;)

---

