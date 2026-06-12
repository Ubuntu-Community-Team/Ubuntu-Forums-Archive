---
title: "Wireless Problems"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by mcgodx on 2008-11-13
Hi,

I have Linux Mint (currently it's 6, RC1, which is built on 8.10, but I also had this problem with the Linux Mint 5 final release, which is based on 8.04).

The problem I have is that occasionally I will lose my network connection and I cannot regain it until I restart the computer (I did not try stopping and restarting the network services).

It only does this on Ubuntu/Linux Mint (I haven't tried it on Fedora or other distros, although in Windows I never have lost connectivity).

My wireless adapter is an Intel 3945a/b/g card, and the router is a Linksys WRT110.

I sometimes use smb:// in Nautilus's address bar to connect to a Windows Share on my desktop, and this seems to aggravate the problem, (usually within 5-10 minutes I'll notice I lost connection) although it'll happen even if I don't connect to the Share at all.

Anyone know why this is or a way to fix it?

---

### Post by bswilson on 2008-11-13
You should have a file called **/var/log/wpa_supplicant.log**.  Try looking at that file with the System Log tool or via the command line.  That log file may give you some indication as to what's wrong.

Otherwise, maybe give restarting the networking services a try?  This command should do it.

```
sudo /etc/init.d/networking restart
```

---

### Post by mcgodx on 2008-11-13
Thanks for the tip.

In the log there are several (at least 20 at a time) lines that all say "CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys", I'm not really sure what that means, although I get the jist of it.

There are also some that say "Trying to associate with [MAC address here] (SSID='home' freq=2412 MHz)", at which point,  it then has the same "CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys" line 8 times afterwards, until I am assuming I restart, because after that there is a line that says key negotiation was completed.

-EDIT-

I tried restarting the network service, it did not solve the problem when it showed up again.

---

### Post by bswilson on 2008-11-13
> **mcgodx said:**
> SSID='home' freq=2412 MHz

This is the most interesting part of your log entries.  I suspect you have another wireless device, such as a 2.4GHz cordless telephone nearby.

If that's the case, then all you need to do is modify your Wireless Access Point's radio frequency.  If you can tell me what kind of Wireless router you have, I can instruct you on how to do that.

---

### Post by mcgodx on 2008-11-13
> **bswilson said:**
> This is the most interesting part of your log entries.  I suspect you have another wireless device, such as a 2.4GHz cordless telephone nearby.

If that's the case, then all you need to do is modify your Wireless Access Point's radio frequency.  If you can tell me what kind of Wireless router you have, I can instruct you on how to do that.

It's possible that we do.  I'm not sure what frequency our cordless phones are on.  I'll try a different channel and report back.

Alright, I just tried out channel 11, instead of channel 1, which is 2.462GHz and I am still getting the problem.  To test I went to play a video that was shared on my desktop and I got disconnected after about 45 seconds of play time.

---

### Post by bswilson on 2008-11-14
Well, I did some more research and found that other folks are having problems with the *Intel ProWireless 3945* also.  One remedy that I discovered is known to work on Fedora Core 8, but I suspect it's the same for Ubunutu.  Run these commands:

First, let's back up your [modprobe]("http://en.wikipedia.org/wiki/Modprobe") configuration:

```
sudo cp /etc/modprobe.conf /etc/modprobe.conf.ORIG
```

Next, we'll add a line to that file:

```
sudo echo options iwl3945 disable_hw_scan=1 >> /etc/modprobe.conf
```

Last, reboot your system to ensure this change gets added to the kernel.  I hope this will fix your problem, but write back if it doesn't!

---

### Post by mcgodx on 2008-11-14
Unfortunately it appears that there is no modprobe.conf in Ubuntu, and I am not quite sure how to create something similar.  There is a directory for /etc/modprobe.d/ however, but when I do an ls to figure out what is inside, it's just the following:

```
aliases       blacklist-framebuffer  fuse        lrm-video
alsa-base     blacklist-modem        i2c         options
arch          blacklist-oss          isapnp      toshiba_acpi.modprobe
arch-aliases  blacklist-watchdog     libpisock9
blacklist     dkms                   libsane
```

The options file may be what I am looking for, the contents of that file are as follows:

```
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

# Stop auto-association.
# LP: #264104
options ipw2200 associate=0

# XXX: Ignore HPA by default. Needs to be revisted in jaunty
options libata ignore_hpa=1
```

---

### Post by mcgodx on 2008-11-14
Okay I went ahead and did it, I added that line to the /etc/modprobe.d/options file and it may be too early to tell but it seems like it is working so far.  I have been doing some heavy file transfers between my laptop and desktop to see if I can purposefully break the connection (as doing this stuff seemed to do it in no time in the past) so far no problems at all so I am hoping that it fixed it.

Thanks a million for pointing me in the right direction

---

### Post by bswilson on 2008-11-14
Man, I was just in the processing of posting again to tell you I screwed up.  You're right, Ubunutu has modularized the modprobe implementation, so there's no modprobe.conf anymore.

Looks like you updated **/etc/modprobe.d/options**, which was the right thing to do.  Sorry for giving you faulty information, but I think you arrived at the right fix. :)

---

### Post by mcgodx on 2008-11-15
I have another issue that is more of an inconvenience than anything, but when I turn my laptop on I cannot automatically connect to the router.

I have to click the NM icon, click "connect to hidden wireless network" then select my network from the dropdown menu, and then press okay.

On my router I am using WPA with AES encryption, and I turned SSID broadcast off.

Is there a way to automatically connect to it?  Windows does.

---

