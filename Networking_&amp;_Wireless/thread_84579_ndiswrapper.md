---
title: "ndiswrapper"
date: 2005-10-31
forum: Networking &amp; Wireless
---

### Post by seismicmike on 2005-10-31
Guys, ndiswrapper is just flat out not working for me...

i've downloaded the latest driver from Broadcom's site, and it just won't work... :(

HELP!!!!

it installs....

```

sudo -s
# ndiswrapper -i <driver>.inf
# ndiswrapper -l
<driver> driver installed
# ndiswrapper -m
# modprobe ndiswrapper

```

and yet, it doesn't work!!!!!!  :mad: :mad: :mad: :mad: :mad: :mad:

---

### Post by sigma2805 on 2005-10-31
what, if any, error messages are you getting? also what laptop do you have?

---

### Post by seismicmike on 2005-10-31
acutally i got it to work, thanks :)

i followed the directions here: [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

---

### Post by ka1axy on 2005-11-01
Just installed Ubuntu 5.10 on an old Dell Latitude D233 laptop, and was able to get the problematic "Chinese" Netgear WG511v2 card working *with no recompiles of NDISwrapper* after following the sample NDISwrapper install instructions in the Ubuntu wiki (which is down now, or I would give a link).

This involved:

- Installing 5.10 and applying all the upgrades (using a wired Ethernet card), then, as root:

# apt-get update
# apt-get install ndiswrapper-utils

Now, copy the Windows 2000 .inf and .sys files from the Netgear CDROM (I did change the .INF suffix of one file to .inf, just in case) to the working directory (I used root's home directory)

Then:

# ndiswrapper -i <driver>.inf
# ndiswrapper -l
<driver> driver installed
# ndiswrapper -m

Add the line below to /etc/networks/interfaces:

iface wlan0 inet dhcp

Rebooted, then:

# iwlist wlan0 scan

(returned two access points)

I then went to Ubuntu's software package install menu and (after enabling "Universe" sources) installed the "wifi-radar" package.

After rebooting, and bringing up Wifi-Radar, I was able to select one access point and, upon removing the wired LAN card and another reboot (just to be sure), brought up Mozilla and browsed to www.cnn.com!

---

