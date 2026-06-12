---
title: "AT&amp;T 3G Mobile Broadband"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by Holend on 2008-12-01
I have the ThinkPad T500 with built in MiniPCI AT&T WLAN

( Ericsson F3507g Mobile Broadband Minicard )


I can't connect to my AT&T Mobile Broadband service.  Ubuntu can see the 3g card and takes me through the mobile broadband setup.  It just will not connect to AT&T Mobile Broadband.  It will attempt to connect but after a few seconds of trying message pops up saying disconnected.  

I talked with someone in network support at att and he had me change a few things in mobile broadband settings but nothing has worked so far.

Anyone have any idea how to make this work?

---

### Post by webdevelopment on 2010-03-20
same problem... im standing here in the mall at the AT&T store and the mobile card isnt working... looking for a solution before i buy it...

---

### Post by alexfish on 2010-03-21
hi

which version of Ubuntu are you using, also by which method are you trying to make the connection,can you post details of what has been done so far

in Ubuntu try to find out if the modem has been detected with these commands from the terminal, this can be found in the Applications/Accessories Menu

if usb device , plug the device in

Code:

lsusb

used to identify devices on the usb ports

pci devices

code:

lspci

..........

dmesg | grep -e "modem" -e "tty" 

used to identify which lines the modem is connected to

from a seperate terminal

Code:

tail -f /var/log/syslog

outputs the last 10 lines of a file, with the -f option it continues to  monitor the file and keeps outputing any further additions appended to  the file in real time.

if possible post the details

Thanks in advance

alexfish

post found here

[http://www.thinkwiki.org/wiki/Ericsson_F3507g_Mobile_Broadband_Module](http://www.thinkwiki.org/wiki/Ericsson_F3507g_Mobile_Broadband_Module)

---

### Post by gradinaruvasile on 2010-03-21
Have you tried using gnome-ppp? Cause network manager is really dodgy with 3G devices.
Just install the gnome-ppp package, launch it from the menu.

---

### Post by webdevelopment on 2010-03-28
> **gradinaruvasile said:**
> Have you tried using gnome-ppp? Cause network manager is really dodgy with 3G devices.
Just install the gnome-ppp package, launch it from the menu.

i tried the gnome-ppp but have no clue how to use it????

i'm also have the same problem on ubuntu 10.04 beta

everything is fine but it wont connect (it can see the network and the device just wont connect to it)

this is a problem in the current stable (9 something) version but was supposed to be fixed in 10.04 but i see its not fixed yet... why cant someone just fix this?

why does ubuntu always have to have problems with wireless?

---

### Post by webdevelopment on 2010-03-29
how do you use gnome-ppp to connect to at&t wireless broadband?

---

### Post by Tamale on 2010-05-11
I've used the built-in network manager in ubuntu 9.04 and 9.10 to connect to the internet with my AT&T 3G Nokia E71x with no problems for well over a year now, but suddenly after upgrading to 10.04 I cannot connect anymore.

I tried removing and re-adding the connection to no avail, and I tried all three of my usb ports. The wizard discovered my phone fine, and the phone shows its connected, but after trying to connect it just says "GSM Network disconnected" every time.

What gives?

---

### Post by foresthill on 2010-05-11
usb_modeswitch somehow got left out of the default install with 10.4. 

Find a way to get on the internet, and first run Update Manager and patch up your system, then go to Synaptics Package Manager and install usb_modeswitch. 

3G modem should be detected the same as previous Ubuntu versions after you do that. Or at least that's what I did to get my Cricket 3G USB modem working. YMMV.

---

