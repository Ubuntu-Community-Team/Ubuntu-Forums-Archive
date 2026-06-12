---
title: "Inventel or Belkin?"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by tartarian on 2007-07-04
I have two usb wireless recievers. 
A Belkin Wireless USB Networking adapter - F5D7050
or 
A Inventel UR054g RO1 adapter (it comes as standard with Orange/Wanadoo wireless broadband)

I've tried using ndiswrapper for the drivers of each of them and neither of them seem to work
Which one should I focus on?
And *please* could somebody help me 
I'm on my knees here! :(

and it won't let me set my access point through iwconfig either. 
Here's the output of iwconfig:

```

no wireless extensions

eth0
no wireless extensions

eth2
IEEE 802.11b ESSID:"WANADOO-3EB4"
Mode:Auto Channel=14 Access Point:Invalid
Sensitivity=0/200
Link Quality:0 Signal Level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Incalid misc:0 Missed beacon:0

```

Thanks in advance

---

### Post by Joban on 2007-07-05
Are you using the latest version of ndiswapper? People with your Belkin adapter have had issues with ndiswrapper-1.7.

What chipset is the Inventel?


If I were you I'd use the Belkin one, as it does work with ndiswrapper.


Also: how did you try to install the drivers? I advise you use command line:

```

sudo ndiswrapper -i /path/to/your/driver/driver.inf

```
to install the driver and
```

sudo ndiswrapper -l

```
to check that it's working. If it is, then the above will print out
> 
installed drivers:
driver          driver installed, hardware (xxxx:xxxx) present


you have to copy all the .inf, .sys etc. files to your hard drive from the cd before you can install them.

good luck!

---

### Post by Austin_KW on 2007-07-05
The belkin F5D7050 is actually 4 different adapters, depending on the version they use different chipsets. Some have available native drivers for linux. There is also a problem with the ubuntu drivers and driver conflicts where sometimes ubuntu loads 3 different drivers (rt73,prism and rt2570)

What version is your belkin (and what is the windows driver that came with it)?

Also what is the output of the following terminal commands
lsusb
lsmod | grep usbcore

---

### Post by tartarian on 2007-07-05
Thanks for the help guys! Its all really appreciated :)
Thankfully I've sorted the whole Inventel/Belkin thing. I've decided on the Belkin because it seems to work now i've installed the driver with ndiswrapper
I still can't connect to my network though
Network settings decides to freeze everytime I try and input the settings, or try to activate the connection
My computer freezes when I run /etc/init.d/networking restart from the terminal
The outputs of iwconfig, ifconfig, iwlist scan and the contents of my /etc/network/interfaces are in [this thread]("http://ubuntuforums.org/showthread.php?p=2963992#post2963992")
Any help would be really appreciated!
Thanks guys :)

---

### Post by Austin_KW on 2007-07-06
The freeze is probably a driver conflict, need to see the output of the lsusb command to check.

---

### Post by tartarian on 2007-07-06
Thanks for the help :)
 output of lsusb is :
```

Bus 001 Device 003: ID 050d:7050 Belikin Components F5D7050 ver 1000 WiFi
Bus 001 Device 002: ID 046d:c50a Logitech, Inc.
Bus 001 Decive 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

```

also /etc/init.d/networking restart freezes on
```

Listening on LPF/rausb0/00:11:50:4c:37:c8
Sending on LPF/rausb0/00:11:50:4c:37:c8
Sending on Socket/fallback

```

Any ideas?

---

