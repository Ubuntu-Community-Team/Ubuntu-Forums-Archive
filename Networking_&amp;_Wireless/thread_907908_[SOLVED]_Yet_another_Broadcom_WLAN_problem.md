---
title: "[SOLVED] Yet another Broadcom WLAN problem"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by AlcoholicDoc on 2008-09-01
**[COLOR="Blue"]_I have figured this out, but am leaving it here so that others may use it to help themselves. My solution is outlined in [[COLOR="Red"][U]post #7_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=907908&postcount=7") of this thread.[/U][/COLOR]**

I have a Dell Inspiron 1501 laptop with the Dell Wireless 1390 WLAN MiniPCI Card. I'm using Ubuntu Hardy Heron 8.04.1...

The WLAN card is initially seen as the BCM94311MCG MiniPCI Rev 01

I have searched These forums as well as many others over the past few days looking for a way to make this card work again, but to no avail.

I've tried the native driver as well as every way of using ndiswrapper I could find, doing a fersh install of Hardy every time.

I first had Hardy beta installed when it came out and the native b43 driver worked beautifully, but in my quest to learn as much as possible, I tried installing a few other distros to see what the differences were. None of those worked with my wireless card, so I decided to go back to Ubuntu.

In that time I lost the Beta CD I had so I decided to just download the newest iso and go from there thinking it would have to be better since it was no longer beta.

I have spent days trying to get this card to work now and the most I've been able to get to happen is my WLAN LED will come on after booting.

I read that there was some kind of patch that made these cards work, but broke others, so it was removed before the final release of Hardy.

I was wondering if anyone could give me instructions on where to find the patch and how to install it.

I'm not a complete newb, but I'm not great either.

If anyone could help me, I'd be grateful.

---

### Post by cdtech on 2008-09-01
Do you have the b43-fwcutter installed?
```
sudo apt-get install b43-fwcutter
```

---

### Post by AlcoholicDoc on 2008-09-01
> **cdtech said:**
> Do you have the b43-fwcutter installed?
```
sudo apt-get install b43-fwcutter
```

That was the first thing I tried. That's what I was using with the Beta, but it doesn't work now. Gives me my WLAN light and i have the wlan0 device, but doesn't see any networks. I tried manually connecting to my network, but still nothing.

---

### Post by cdtech on 2008-09-02
Just some things to check. The b43 now works with the 4311 so remove ndiswrapper and check your /etc/modprobe.d/blacklist, this is my file:
```
# everything to do with wireless
blacklist b44
blacklist ipv6
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist agpgart
blacklist intel_agp
```
If you have b43-fwcutter installed just reinstall.

---

### Post by cdtech on 2008-09-02
What do you get with "ifconfig"

Also try using "wicd" and see if it detects wireless networks.....

---

### Post by AlcoholicDoc on 2008-09-02
> **cdtech said:**
> What do you get with "ifconfig"

Also try using "wicd" and see if it detects wireless networks.....

I get nothing right now. I just finished a clean install so I could see if anyone came up with anything I haven't seen yet.

I tried wicd, but it had the same problem. It was like the card was on, but not doing anything.

Just in case anyone needs it, this is the output from lspci:
dustin@dustin-laptop:~$ lspci -vv -nn | grep Broadcom
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

---

### Post by AlcoholicDoc on 2008-09-02
Okay... Amazingly enough, I finally got this card working using the new driver process in this post: [[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=880218_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=880218")

It works great now, and at full speed too! I had a problem with it disconnecting after a couple of minutes, but fixed that by re-enabling the wireless hotkey in the BIOS.

So if anyone else has this card, and is having trouble getting it working, go to that post and follow the instructions.

I had to modprobe every time I started the computer, but got around that using the following process:

```
Make a script for wl's fix
In a terminal type:
sudo gedit /etc/init.d/wirelessfix.sh

Paste this into the file:
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r wl
modprobe wl
modprobe b44

Point the terminal to your init.d file and make your script exectuable:
In a terminal type:
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

Update and make it stick:
In a terminal type:
sudo update-rc.d wirelessfix.sh defaults

Then reboot
In a terminal type:
sudo reboot
```

I got that from [[COLOR="Red"]_here_[/COLOR]]("http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html"), and modified it to match the new "wl" module.

---

### Post by GrandpaLeaman on 2008-09-02
> **AlcoholicDoc said:**
> Okay... Amazingly enough, I finally got this card working using the new driver process in this post: [[COLOR=Red]_http://ubuntuforums.org/showthread.php?t=880218_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=880218")

It works great now, and at full speed too! I had a problem with it disconnecting after a couple of minutes, but fixed that by re-enabling the wireless hotkey in the BIOS.

So if anyone else has this card, and is having trouble getting it working, go to that post and follow the instructions.

I had to modprobe every time I started the computer, but got around that using the following process:

```
Make a script for wl's fix
In a terminal type:
sudo gedit /etc/init.d/wirelessfix.sh

Paste this into the file:
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r wl
modprobe wl
modprobe b44

Point the terminal to your init.d file and make your script exectuable:
In a terminal type:
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

Update and make it stick:
In a terminal type:
sudo update-rc.d wirelessfix.sh defaults

Then reboot
In a terminal type:
sudo reboot
```I got that from [[COLOR=Red]_here_[/COLOR]]("http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html"), and modified it to match the new "wl" module.

Well, I tried this and...IT WORKED. I can't say that my connections is any better, even though WICD says I,m connecting at 80% (as opposed to 26% with ndiswrapper).

---

### Post by AlcoholicDoc on 2008-09-03
I'm glad this worked for you. I'm still having a couple of issues after the latest updates, but I'm sure I'll get through them. If you have any issues, I'd like to hear about them. Maybe I can help.

---

