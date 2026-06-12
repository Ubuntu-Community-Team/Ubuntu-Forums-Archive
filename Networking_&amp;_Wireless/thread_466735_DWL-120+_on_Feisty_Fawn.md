---
title: "DWL-120+ on Feisty Fawn"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by botulismo on 2007-06-07
I'm currently running Xubuntu Feisty Fawn and I was wondering if anyone had gotten the D-Link DWL-120+ successfully working on it. I had a different wireless USB device working fine on this laptop but the way that it jutted out kind of awkardly kind of destined it for failure, so I'm just trying to use my back-up wireless device from my Windows days, but... no luck. I've tried following a couple of guides on here for installing it but they all seem to be geared towards 6.06, and also, more importantly, don't work.

I also heard that I should build the newest acx drivers but 1.) even if I supposedly have all the dependencies required to build it, it always seems to fail, and 2.) the web host that has the firmware for my device is giving me 404 errors.

So, do I need to downgrade, or has anyone done it, and, if so, could you give me some suggestions on how to do it? I'm not picky about open-source vs. ndiswrapper drivers (please don't flame me, I'm just not rich and I would prefer to be able to use some kind of wireless internet vs. none)

---

### Post by cazique on 2007-09-04
i had the same problem here when i update from ubuntu 6 to ubuntu 7. 
The problem seemed, that **ndiswrapper and the acx-driver were loaded at the same time** and both tried to access the usb-device!! 

So here is what i did:
[SIZE="5"]
[COLOR="DarkRed"]1.) [/COLOR][/SIZE]**Go to /etc/modprobe.d/blacklist:**
```
sudo gedit /etc/modprobe.d/blacklist
```

[SIZE="5"][COLOR="DarkRed"]2.)[/COLOR][/SIZE] and add a new line: 
*"blacklist acx"*
[SIZE="5"]
[COLOR="DarkRed"]3.) [/COLOR][/SIZE]Then unplug the your d-link dwl-120+ usb wlan adapter.
[SIZE="5"][COLOR="DarkRed"]4.)[/COLOR] [/SIZE]**Remove the acx-driver:**
```
sudo rmmod acx
```

[SIZE="5"][COLOR="DarkRed"]5.)[/COLOR][/SIZE] **load the appropriate windowsdriver (included with the usb-adapter):**
```
sudo ndiswrapper -i windowsdriver.inf
```[SIZE="5"]
[COLOR="DarkRed"]6.)[/COLOR][/SIZE] **Check if everything went right and set the driver to auto-startup:**
```
ndiswrapper -l
ndiswrapper -m

```
[SIZE="5"]
[COLOR="DarkRed"]7.)[/COLOR][/SIZE] **Start your wlan:**
```
ifup wlan essid default
``` 
where 'default' is the you wlan-network-name. If you don't know it, just try 'default'.

[COLOR="DarkRed"]So that's what i had to do to get my d-link dwl-120+ usb wlan working again on ubuntu 7.04. It was fairly strange that it worked out of the box from the live cd ubuntu 6 but it wouldn't work anymore after the update to ubuntu 7. [/COLOR]

---

### Post by Gage_AB on 2007-09-04
Hi,

Here is how i got my dwl-g122 to work, ignore the dll stuff and make sure you don't plug it in until you have done everything else.

[http://ubuntuforums.org/showthread.php?t=536079&highlight=dwl-g122](http://ubuntuforums.org/showthread.php?t=536079&highlight=dwl-g122)

---

