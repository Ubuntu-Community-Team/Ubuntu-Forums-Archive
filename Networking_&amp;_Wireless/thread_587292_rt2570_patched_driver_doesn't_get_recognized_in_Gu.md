---
title: "rt2570 patched driver doesn't get recognized in Gutsy"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by TheAgress0r on 2007-10-22
Hi.

I've upgraded tot Gutsy (fresh install) and I'm trying to install the rt2570 patched driver again which worked fine in Feisty. Gutsy already has a driver build-in for it and I can't get it replaced by the patched version from [here]("http://homepages.tu-darmstadt.de/~p_larbig/wlan/"). I followed the same steps which worked in Feisty (make, make install, modprobe rt2750) but when I plug the wireless antenna in, it uses the build-in driver rather than the one I want it to use.
How can I fix this pls??

Thx.

---

### Post by xshakakee on 2007-11-07
Man, this has been available for two weeks?  Not fair.  Anyway, in order to unload your current driver, you should take a look at```

lsmod | grep rt2500
```

If you see a rt2500usb in there, you need to unload and blacklist it.```

sudo modprobe -r rt2500usb
sudo echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist
```

Now, I have to download and play with this driver to see if it works on my system.

Anyway, I got this working using ndiswrapper, at least, I think the chipset is a 2570.

It's a Belkin F5D7050 Version 2000.  The lsmod has says its a 1000, but I'm skeptical.

[This site]("http://ralink.rapla.net/") says it's a 2000.  I'm pretty sure the 1000 is a prism54 chipset.  Some default Linux distros install that driver, which fails for obvious reasons.

Anyway, I'll have to check out this driver, now, and post back when, rather if, I have it working.  Oh, if you've already loaded it up, it should be in /etc/modules.
**UPDATE: This is wrong**  > So this:
```
sudo echo "rt2570.ko >> /etc/modules
```
You'll have to run that code from the folder that the module is actually in.  I'll post again if I can get this driver to work.
** Here is the correct way:**
You only need to```

gedit /etc/modules
``` and add "rt2570" to the end of the file.  Save and exit.
It doesn't need to know the file extension.  I wasn't able to get this module working, anyway.  I used ndiswrapper.

---

### Post by xshakakee on 2007-11-08
Well, that was fruitless.  I wasn't able to use the rt2570.ko module at all for my wireless nic.  Here's what I've got.

```
sudo su
lsusb
Bus 004 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

See, it says version 1000, which has the prism54 chipset.  I'm probably going wrong here.

Anyway, I had to use ndiswrapper to get this to work, even marginally.  First, I pulled ndiswrapper down, and installed it according to [this]("http://ubuntuforums.org/showthread.php?t=564419") guide.

I needed to get the drivers, which are labelled rt2500usb.inf, rt2500usb.sys, and rt2500usb.cat  I put those into a folder on the desktop and went on with wieman01's guide.  At the end I could do this:
```
 ndiswrapper -l
rt2500usb : driver installed
        device (050D:7050) present (alternate driver: p54usb)
```
Not elegant, but wait.  It gets worse.  I tried using rutilt, which some folks here have said works great with Ralink chips.  I did the obvious thing and used```

apt-get install rutilt
```
and just let it install, automagically.  Then I started playing with it.  Oh, first I blacklisted the old driver, as well as a few others:
contents of ```
 /etc/modprobe.d/blacklist
...
blacklist rt2500usb
blacklist rt73usb
blacklist rt2500
blacklist rt2570
blacklist rt73
blacklist 2x00usb
blacklist 2x00lib
```
Then I added ndiswrapper to the /etc/modules file like so:```
 gedit /etc/modules
/etc/modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
[COLOR="green"]ndiswrapper[/COLOR]
```
Saved and closed that window.

May have rebooted, at that point.  I'm sure it didn't work the first couple of hours, or tries, so I shut the machine off for a while.

Anyway, when I came back, I went into rutilt and tried to futz with the parameters.  Nothing I did would give me WPA.  I created a profile, set it up so that it looked as close as I was going to get, made the encryption type WEP, with a key of "1111".  Hey, I needed to get out of rutilt and into /etc/network/interfaces.

Then in ```
 gedit /etc/network/interfaces
``` I made the following changes:```

auto wlan0
iface wlan0 inet static
address 192.168.2.4
netmask 255.255.255.0
gateway 192.168.2.1
[COLOR="red"]#[/COLOR]dns-nameserver 68.94.156.1, 68.94.157.1

[COLOR="red"]wpa-ssid "<My SSID>"
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk "mysupersecretkey"[/COLOR]
```

weirdly, this was totally unlike the iwpriv and iwconfig statements that I was used to.  Oh well, let's give it a shot.  I did```

/etc/init.d/networking restart
```
...and it all came up!  It took about a minute, and I was sitting there banging away, waiting for Firefox to open up, when the blinking light on the usb stick suddenly started going crazy, and I could see out!

Since then, I've been able to get on the network, but through a convoluted process.

1) go into rutilit.  Add a profile (for some reason, my old profile gets deleted, either at startup, or when the utility closes).  Make all the changes (profile name, SSID, Managed, WEP, key = 1111), save, and the thing should just close out on its own.  No need to close (I think it fails here, but essentially sets up the next step).

2) go into terminal and type:```
/etc/init.d/networking restart
```

When I do that, it gets me back on-line.  This procedure may be specific to my machine.  There is no reason for me to be limited to WEP, if the driver is being picked up correctly in rutilt.  I'll have to see if I can install the prism54 driver, and if that gives me any luck.  So far, this process lacks elegance.

Well, I hope some part of this works for you.  I'd hate to have you be stuck in my situation, which is with the 2 step setup every time you boot, in order to get on-line.  Oh well, it's better than not being able to use the wireless usb at all.

---

### Post by wieman01 on 2007-11-09
As for the restart issue, see post #2 of my WPA tutorial. It's a known bug.

---

### Post by Sqweeks on 2007-11-20
Has anyone gotten this patched driver to work at all in gutsy? I am having no luck right now.

---

### Post by wieman01 on 2007-11-20
> **Sqweeks said:**
> Has anyone gotten this patched driver to work at all in gutsy? I am having no luck right now.
Yes, I have. What's the problem?

---

### Post by Sqweeks on 2007-11-20
I did this to install them

```

ifconfig rausb0 down
rmmod rt2570
wget http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt2570-k2wrlz-1.6.1.tar.bz2
tar -xvjf rt2570-k2wrlz-1.6.1.tar.bz2
cd rt2570-k2wrlz-1.6.1/Module
sudo make && make install
modprobe rt2570

```

right now I think it might be working. seems my airoscript.sh i used in a older version of ubuntu is not seeing my card. Ill do a normal test with aircrack-ng and see if its working.

---

### Post by Sqweeks on 2007-11-21
Well im not sure if the drivers are installed correctly or not. Things seem to be working fine but i get errors when entering "sudo airmon-ng start rausb0 9" (rausb0          Ralink USB      rt2570 (monitor mode enabled)Invalid command : forceprismheader). Going to reinstall a fresh ubuntu and see if i can get it to work again. i messed around alot with the drivers before. 

If you could wieman01 would you be able to post the steps you did to install the patched drivers?

---

### Post by wieman01 on 2007-11-21
> **Sqweeks said:**
> Well im not sure if the drivers are installed correctly or not. Things seem to be working fine but i get errors when entering "sudo airmon-ng start rausb0 9" (rausb0          Ralink USB      rt2570 (monitor mode enabled)Invalid command : forceprismheader). Going to reinstall a fresh ubuntu and see if i can get it to work again. i messed around alot with the drivers before. 

If you could wieman01 would you be able to post the steps you did to install the patched drivers?
Hello, 

I did exactly the same steps and posted on Aircrack-NG's web site. So no difference. What version of Ubuntu are you on? Gutsy?

---

### Post by wieman01 on 2007-11-21
You know what? I think the problem is that your old drivers are still loaded... Search for a file called "rt2570.ko" and replace it with the one you have just compiled.

You need to ensure that the new module is used rather than the one that is loaded after inserting the stick for the first time.

---

### Post by Sqweeks on 2007-11-21
Ok i reinstalled everything and removed the rt2x00 folder in /lib/modules/2.6.22-14-generic/ubuntu/wireless

when i run iwconfig i get 

```

rausb0    RT2500USB WLAN  ESSID:""  Nickname:""
          Mode:Monitor  Frequency=2.457 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-120 dBm  Noise level:-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

when i do "lsmod | grep rt2570" i get
```

rt2570                190016  1 
usbcore               138632  6 usbhid,hci_usb,rt2570,ehci_hcd,uhci_hcd
```

sudo airmon-ng gives

```

Interface       Chipset         Driver

rausb0          Ralink USB      rt2570
eth1            Centrino b/g    ipw3945
```

then "sudo airmon-ng start rausb0 9" gives me this

```

Interface       Chipset         Driver

rausb0          Ralink USB      rt2570 (monitor mode enabled)Invalid command : forceprismheader

eth1            Centrino b/g    ipw3945
```

do you get the same thing or does something look wrong?

---

### Post by Sqweeks on 2007-11-21
Well i changed my wireless security to WEP to i could have a strong signal and everything and everything worked. Packet injection worked but i have no idea whats going on with the error message in airmon-ng.

---

### Post by wieman01 on 2007-11-21
> **Sqweeks said:**
> Well i changed my wireless security to WEP to i could have a strong signal and everything and everything worked. Packet injection worked but i have no idea whats going on with the error message in airmon-ng.
Since injection works, nothing you should worry about I guess.

---

