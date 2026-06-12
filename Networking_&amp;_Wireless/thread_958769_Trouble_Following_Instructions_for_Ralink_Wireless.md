---
title: "Trouble Following Instructions for Ralink Wireless Card &quot;Operation Not Supported&quot;"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by The Sunburned Surveyor on 2008-10-25
I switched from Debian to Ubuntu about 8 months ago. I was connecting to my wireless network with Ubuntu with no problems until about a month ago. I "lost" my ability to connect to or configure wireless networks with Ubuntu after a software update.

I've been following the instructions in the sticky portion of this forum for the last couple of hours. I tried to follow the instructions to manually configure my access to the wireless internet connection listed in this post: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

I was specifically following the instructions for those with Ralink Drivers using WPA.

When I tried to run several of the commands listed there, including the "sudo ifconfig <interface> up" I got an "Operation not supported" message.

I know that I have a wireless network card installed. Access to the wireless internet connection works fine on my wife's Windows XP computer.

Here are the specs for my set-up:

Computer Make and Model: Dell Dimension E521
Router Make and Model: Linksys Wireless-G Broadband Router WRT546
Wireless Network Card: Ralink RT2561/RT61 802.11g 

I'm a fairly savvy computer user, and I've been using Linux for a couple of years. If someone can help me with suggestions on what to try next, I'd appreciate it.

The Sunburned Surveyor

P.S. - I removed GNOME Network Manager and installed WCID. WCID didn't detect any wireless networks after a reboot.

---

### Post by melojo on 2008-10-25
I used the same thread to get mine working.

did you use ndiswrapper?

open a terminal and type
```
lsmod
```

post the output

---

### Post by melojo on 2008-10-25
Forgot to ask do you also have a wired network adapter on this system?

If so before trying to us your wireless unplug it or type 

ifconfig eth0 down  if eth0 is your wired interface

---

### Post by The Sunburned Surveyor on 2008-10-25
Thanks for the quick response Melojo.

The output of lsmod is quite long. :] Is there a particular module(s) you are looking for? If you need the whole list I can copy some screenshots of the terminal output to post here.

I don't think I used the program called ndiswrapper.

I do also have a wired network card installed. I'll try disabling it as you suggested and will report back here with the results.

The Sunburned Surveyor

---

### Post by The Sunburned Surveyor on 2008-10-25
I shut of the wired network card with the 

sudo ifconfig <wired interface> down

command. I then tried to run through the commands to fire up the wireless network card. Here is the output of the 

sudo dhclient -r <wireless interface> 

command:

northstar@northstar-desktop:~$ sudo dhclient -r wmaster0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback

When I then attempt to run the 

sudo ifconfig <wireless interface> up 

command, i get this error message:

SIOCSIFFLAGS: Operation not supported

Thanks,

The Sunburned Surveyor

---

### Post by The Sunburned Surveyor on 2008-10-25
It sounds like I might be having the same problem as the user on this forum:

[http://ubuntuforums.org/archive/index.php/t-324340.html](http://ubuntuforums.org/archive/index.php/t-324340.html)

It doesn't look like he got an answer to his problem in the thread. He gave up and went back to WinXP.

I'm still hoping to find a solution. :]

The Sunburned Surveyor

---

### Post by melojo on 2008-10-25
sry it took so long for me to replay
ok you might try ndiswrapper and use the windows driver to get it to work.

first install ndiswrapper

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

remove the driver module that its using now you can find this with 
```
lsmod
``` then ```
rmmod name of module
```

get your windows driver.  should consist of a .inf and .sys make sure they are in the same directory.

To install the driver after ndiswrapper is installed and after removing the linux driver module.

open a terminal and type ```
sudo -i 
```so you don't have to keep entering sudo. then

```
ndiswrapper -i location of the inf file
```
this installs the driver to ndiswrapper 

```
modprobe ndiswrapper
```
this loads the module

If went well you should have a light on showing that its enabled.

then 

```
ifconfig
```
To see if it picked up the wlan interface, if it did post back with the name of the wlan interface.

---

