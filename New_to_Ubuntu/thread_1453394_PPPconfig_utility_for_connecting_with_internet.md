---
title: "PPPconfig utility for connecting with internet"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by kerrykk on 2010-04-13
After reading the internet for 8 hours I figure out Ubuntu 9.10 uses a utility called pppconfig to configure modems and that Gnome-PPP is not available on 9.10.  

I connect to the internet with my Nokia 6303.  My ISP is AIS 12call mobilelife Thailand.  But the questions are for a modem and not for a mobile phone modem.  What do I do?  Will it still work?  

These are the questions pppconfig asks me. 

1.  Is my ISP dynamic or static. (I don’t know)

2.  Enter the IP number for your server.  (Where do I find it?) 

3.   Enter the IP number for your secondary  (Do I have one?)

4.  Authentication Method for provider  (PAP, Chat, Chap?)  (I don’t know)

5.  Enter your modem port speed (e.g. 9600, 19200, 38400, 57600, 115200).  (I don’t know?)     

6.  Select method of dialing. Touch tone or pulse.  (My phone does not dial anything?)

7.  Enter the number to dial.  (it doesn’t dial a number.  It connects with nokia pc suite)

8.  The port your modem is on identified automatically or enter the port your modem is on (example /dev/ttyS0 is COM1 in DOS.)   (It is not on a port it is USB data cable.) and the connfig program does not find my mobile phone plugged into a USB port.  

10.  Password?  Username? (I don't have one for my phone?) 

Any ideas?

---

### Post by lkraemer on 2010-04-13
kerrykk,
Since you have 9.10 installed, most likely you have Wifi that
is usable immediately.  You should be able to locate Gnome-PPP
from the package manager Synaptics. SYSTEM -> ADMINISTRATION -> SYNAPTIC
assuming you can access an Open Wireless Network.

To see if your Phone is detected Open a Terminal Window and type:
```

lsusb

```
then plug in the USB cable, wait a minute, and type lsusb again.

You should see the Phone details as Ubuntu hopefully finds the Phone.
From there you are going to need more information..........for a PC

REF:
[http://klauskjeldsen.dk/setup-internet-connection-via-bluetooth-using-nokia-6300-on-mac-os-x/](http://klauskjeldsen.dk/setup-internet-connection-via-bluetooth-using-nokia-6300-on-mac-os-x/)


lk

---

### Post by kerrykk on 2010-04-13
No, I don't have wifi.  I connect with gprs and my nokia on another computer running windows xp and nokia pc suite.  

When I 1susb I get:      Bus 001 Device 005: ID 058f:6366 Alcor Micro Corp. 
  
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  
  [COLOR=Red]Bus 002 Device 005: ID 0421:01b1 Nokia Mobile Phones [/COLOR]
  
  Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
  
  Bus 002 Device 002: ID 0461:0010 Primax Electronics, Ltd 
  
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


But I don't know what to do with that information.

---

### Post by lkraemer on 2010-04-13
It appears that your Phone is recognized.  That is good.

Now from my searches you need to install Blueman and then pair the
Phone with the Laptop.

REF:
[http://ubuntuforums.org/showthread.php?t=1431954&highlight=bluetooth+tutorial](http://ubuntuforums.org/showthread.php?t=1431954&highlight=bluetooth+tutorial)
[http://ubuntuforums.org/showthread.php?t=1417383&highlight=bluetooth+tutorial](http://ubuntuforums.org/showthread.php?t=1417383&highlight=bluetooth+tutorial)
[http://www.spiration.co.uk/post/1307/Ubuntu%20Linux%20-%20Bluetooth%20and%20GPRS%20dialup%20connection](http://www.spiration.co.uk/post/1307/Ubuntu%20Linux%20-%20Bluetooth%20and%20GPRS%20dialup%20connection)

[http://ubuntuforums.org/showthread.php?t=200142&highlight=bluetooth+tutorial](http://ubuntuforums.org/showthread.php?t=200142&highlight=bluetooth+tutorial)

[http://ubuntuforums.org/showthread.php?t=1375575&highlight=bluetooth+tutorial](http://ubuntuforums.org/showthread.php?t=1375575&highlight=bluetooth+tutorial)

[http://ubuntuforums.org/showthread.php?t=651852&highlight=bluetooth+tutorial](http://ubuntuforums.org/showthread.php?t=651852&highlight=bluetooth+tutorial)

[http://ubuntuforums.org/showthread.php?t=111455](http://ubuntuforums.org/showthread.php?t=111455)

[http://codebasket.blogspot.com/2008/12/connecting-to-internet-on-ubuntu-linux.html](http://codebasket.blogspot.com/2008/12/connecting-to-internet-on-ubuntu-linux.html)

Looks as if you are in for a bit of reading.


If your using Windows consider using Keryx.
[http://keryxproject.org/](http://keryxproject.org/)
It will download all the dependencies for you.
I'd suggest downloading Gnome-ppp, wvdial first.


lk

---

### Post by lkraemer on 2010-04-13
This article looks the best to me.
[http://www.wireless-net.org/O.Reilly-Wireless.Hacks.Secon/0596101449/wirelesshks2-CHP-1-SECT-5.html](http://www.wireless-net.org/O.Reilly-Wireless.Hacks.Secon/0596101449/wirelesshks2-CHP-1-SECT-5.html)

[http://astahost.com/info.php/mobile-broadband-ubuntu-bluetooth_t19728.html](http://astahost.com/info.php/mobile-broadband-ubuntu-bluetooth_t19728.html)

[http://tim.oreilly.com/pub/a/linux/2004/02/05/linux_cellular.html](http://tim.oreilly.com/pub/a/linux/2004/02/05/linux_cellular.html)


Finally here is what you need to follow:
[http://tareqalam.wordpress.com/2008/07/11/connect-your-nokia-phone-with-linux-without-pc-suite/](http://tareqalam.wordpress.com/2008/07/11/connect-your-nokia-phone-with-linux-without-pc-suite/)

Once it is working just, setup Gnome-ppp and you're all set.
 
lk

---

### Post by dineshs on 2010-04-13
Did you try this
Right-click on the nm-applet and then click on Edit Connections.
Select the tab mobile broadband-Add,then proceed
Final step,tick connect automatically
I think you need to put your mobile in PC suite mode while trying this

---

### Post by kerrykk on 2010-04-14
I click that and although my phone was recognized when I plugged it in the USB by downloading its content it is not recognized by the “network connections” and when I go to the mobile broadband tab my phone is not there.  I can create a connection but when I choose forward a final time after leaving the plan on default I get a screen that asks username, password.  Advanced, APN, Network, Pin.

I filled out this form and checked connect automatically and when I click the internet icon it does not connect.  I don’t think network connections recognizes my phone.  

I put my phone in PC suite while trying this.

---

### Post by kerrykk on 2010-04-14
> **lkraemer said:**
> This article looks the best to me.
[http://www.wireless-net.org/O.Reilly-Wireless.Hacks.Secon/0596101449/wirelesshks2-CHP-1-SECT-5.html](http://www.wireless-net.org/O.Reilly-Wireless.Hacks.Secon/0596101449/wirelesshks2-CHP-1-SECT-5.html)

[http://astahost.com/info.php/mobile-broadband-ubuntu-bluetooth_t19728.html](http://astahost.com/info.php/mobile-broadband-ubuntu-bluetooth_t19728.html)

[http://tim.oreilly.com/pub/a/linux/2004/02/05/linux_cellular.html](http://tim.oreilly.com/pub/a/linux/2004/02/05/linux_cellular.html)


Finally here is what you need to follow:
[http://tareqalam.wordpress.com/2008/07/11/connect-your-nokia-phone-with-linux-without-pc-suite/](http://tareqalam.wordpress.com/2008/07/11/connect-your-nokia-phone-with-linux-without-pc-suite/)

Once it is working just, setup Gnome-ppp and you're all set.
 
lk

How and where do I get Gnome-ppp?  it is not in Ubuntu 9.10.  I downloaded it to a flash drive and put it on my Ubuntu desktop but I don't know how to install it.  Software center says not in 9.10 data base.  In the taregalam. wordpress it says to use wvdial.  9.10 does not have wvdial and won't load it.

---

### Post by kerrykk on 2010-04-14
I got the network manager icon working from the system menu and made a new connection although it did not recognize my Nokia 6303.  I tried opening a browser in my phone before I plugged it in to the USB port in my PC and the network manager established a connection and I got online easily.  So now it works.  I don't know quite how but I think Nokia was not sending a signal in the PC suite mode until I opened a browser in the phone.  

Thanks for all your help.  I guess the problem is solved!

---

### Post by lkraemer on 2010-04-14
I assumed that you had a Working copy of XP that worked with your phone
for the downloads.

If that was the case you could have used Keryx.
[http://keryxproject.org/](http://keryxproject.org/)
It will download all the dependencies for you.
I'd suggest downloading Gnome-ppp, wvdial first.
(This was in a previous post)

You could have also used the Ubuntu Package site:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and for 9.10 (Karmic):
[http://packages.ubuntu.com/karmic/](http://packages.ubuntu.com/karmic/)
to download a DEB file.  But, you may need other dependencies,
so it may take you several attempts.  The packages will be
marked as to where they are located........like
UNIVERSE or MULTIVERSE.

So, for future downloads in Ubuntu go to:
SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
and  click the two universe check boxes.
(NOTE:  You can also check the install from CDROM/DVD, having the
LiveCD or LiveDVD installed and try to install from the media, but
it might not be the latest version, but should solve your needs)

If you downloaded a DEB package to your Desktop, just double left
click on it to install.

Or, you can copy the DEB to var/cache/apt/archives and use Synaptics
Package Manager to mark it and install it. Assume the file is located
on your Desktop.  Open a Terminal Window:
```

cd Desktop
pwd
ls -alt
sudo cp thefilename.deb /var/cache/apt/archives
cd /
cd /var/cache/apt/archives
pwd
ls -alt firefox*
cd ~
pwd

```
I used firefox* as the example above because I wasn't sure what package you used.

And finally once you are online, you need to use the update manager:
SYSTEM -> ADMINISTRATION -> UPDATE MANAGER
to update everything.

And from there you can just pop into Synaptics Package Manager and
install or remove anything you want.

Are you now using a Bluetooth connection to the Phone, or a tethered
Phone with a USB cable?  I was just wondering..........
 
Glad to assist........Now convert one other user to Linux as payment!

And on top of everything else you learned something....NON M$
ENJOY!

lk

---

### Post by kerrykk on 2010-04-16
> **lkraemer said:**
> I assumed that you had a Working copy of XP that worked with your phone
for the downloads.

If that was the case you could have used Keryx.
[http://keryxproject.org/](http://keryxproject.org/)
It will download all the dependencies for you.
I'd suggest downloading Gnome-ppp, wvdial first.
(This was in a previous post)

You could have also used the Ubuntu Package site:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and for 9.10 (Karmic):
[http://packages.ubuntu.com/karmic/](http://packages.ubuntu.com/karmic/)
to download a DEB file.  But, you may need other dependencies,
so it may take you several attempts.  The packages will be
marked as to where they are located........like
UNIVERSE or MULTIVERSE.

So, for future downloads in Ubuntu go to:
SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
and  click the two universe check boxes.
(NOTE:  You can also check the install from CDROM/DVD, having the
LiveCD or LiveDVD installed and try to install from the media, but
it might not be the latest version, but should solve your needs)

If you downloaded a DEB package to your Desktop, just double left
click on it to install.

Or, you can copy the DEB to var/cache/apt/archives and use Synaptics
Package Manager to mark it and install it. Assume the file is located
on your Desktop.  Open a Terminal Window:
```

cd Desktop
pwd
ls -alt
sudo cp thefilename.deb /var/cache/apt/archives
cd /
cd /var/cache/apt/archives
pwd
ls -alt firefox*
cd ~
pwd

```I used firefox* as the example above because I wasn't sure what package you used.

And finally once you are online, you need to use the update manager:
SYSTEM -> ADMINISTRATION -> UPDATE MANAGER
to update everything.

And from there you can just pop into Synaptics Package Manager and
install or remove anything you want.

Are you now using a Bluetooth connection to the Phone, or a tethered
Phone with a USB cable?  I was just wondering..........
 
Glad to assist........Now convert one other user to Linux as payment!

And on top of everything else you learned something....NON M$
ENJOY!

lk

Windows XP is loaded on my old computer.  It came installed and I don’t have a separate copy of windows xp.  

My phone is connected by data cable to the USB port.  

I think the whole thing would have been easier if I used Bluetooth because the Nokia 6303 has an option to turn on the phone to be recognized by Bluetooth.  

Thanks for your help

---

