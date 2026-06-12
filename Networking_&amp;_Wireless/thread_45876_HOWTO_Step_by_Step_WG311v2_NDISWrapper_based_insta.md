---
title: "HOWTO: Step by Step WG311v2 NDISWrapper based install"
date: 2005-07-02
forum: Networking &amp; Wireless
---

### Post by skipper on 2005-07-02
OK, after some considerable frustration and pain, I finally have a Netgear WG311v2 working on a vanilla Ubuntu 5.04 installation. I am hoping this HOWTO will avoid problems for other unfortunates with the same config.

The following worked on an old Dell Dimension XPS233 (Pentium II), a Netgear WG311v2 PCI card and a Linksys WRT54G 802.11g AP/Router, using the standard Ubuntu 5.04 x86 installation CD.

First, let the installation detect your card and complete its installation using the acx-pci drivers. I had a number of problems getting these drivers to work properly.

1. WEP refused to work (known problem)
2. Would not detect AP on boot, however if the acx-pci driver was unloaded and reloaded, it would work...go figure.

After much futzing and hacking with the acx-pci driver I gave up and tried the ndiswrapper driver, which after a little stuffing around, works perfectly (even with WEP).

So, here are the steps required to get everything going:

First up, ensure your wlan configuration is correct. This can be found in /etc/network/interfaces. Use your favourite text editor and make it look something like this (the first comment - or line starting with # for ultranoobs - was inserted by the installer, the rest are my explanatory notes)...

[FONT=Fixedsys].
.
iface wlan0 inet <what follows will depend on whether you use dhcp>
.
.
# wireless-* options are implemented by the wireless-tools package

#
# Following comment lines are for explanatory purposes...you do not need to 
# copy them verbatim
#

# Most setups will be "Managed" mode, where all wireless clients connect to an
# Access Point (AP)

wireless-mode managed

# The ESSID is normally set up on your AP using your AP configuration tools.
# I recommend changing the default, and turning off ESSID broadcast.
# If you do not want to do this (and you would like to share your Internet 
# connetion wit your neighbours, you can simply use the line "wireless-scan"
# instead of the guff below. Caveat emptor!!

wireless-essid <Insert your AP's ESSID here>
wireless-channel <Insert your AP channel here>

# Next line is optional, most of the time it will autonegotiate

wireless-rate 54MBs

# The next lines are setting up the WEP keys, I am assuming a simple Shared
# Key arrangement where a fixed key is set up on the AP and the client.

wireless-key1 <Insert AP key here>
wireless-defaultkey 1
wireless-keymode open[/FONT]
.
.

Next we install the ndiswrapper-utils package...

[FONT=Fixedsys]sudo apt-get install ndiswrapper-utils[/FONT]

Insert the driver disk that came with your network card into the CDROM, and change to the appropriate driver directory. In my case was "/cdrom/Driver/Windows XP".

Install the drivers...

[FONT=Fixedsys]sudo ndiswrapper -i wg311v2.inf[/FONT]

Check that it worked...

[FONT=Fixedsys]sudo ndiswrapper -l[/FONT]

Next step is to test this setup. Remove the acx-pci module...

[FONT=Fixedsys]sudo rmmod acx-pci[/FONT]

Now test the ndiswrapper module...

[FONT=Fixedsys]sudo modprobe ndiswrapper[/FONT]

If all is well, at this point your AP should be detected, and you should have a connection. (Check your setup using iwconfig, and try to ping a host you know is connected to the network). The first time I did this, something went dreadfully wrong and I had to reboot, so don't be discouraged if it doesn't work the first time.

Now, next we make sure this config is all reloaded when we reboot.

[FONT=Fixedsys]sudo ndiswrapper -m[/FONT]

Then you need to stop the old acx-pci driver from being loaded by the kernel. Easiest way I could find to do this was to remove or rename the module. Here is what I did.

[FONT=Fixedsys]cd /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/acx
sudo mv acx_pci.ko acx_pci.ko.disabled
sudo depmod -a
[/FONT]

Now for some reason, the ndiswrapper driver did not load next time I booted, so you may need to add the line "ndiswrapper" to the end of /etc/modules using your favourite text editor.

Next time you boot, everything should magically work :-)

I do hope this is helpful. I would love to hear any comments or suggestions.

---

### Post by Seer on 2005-07-21
Looks like a great guide, I have had literally 6 weeks of trouble trying to get my belkin Pre-N nic working with various flavours  of linux, linuxant, ndiswrapper, and even trying to hack so drivers together myself.

In the end I gave up and got a second card (wg311 v2) that I will use when booted into Ubuntu and use the pre-n (my god I love pre-n!) in windows.

I was optimistic when my wg311v2 was detected out of the box and even the light was on (something I had never seen in linux before!!) but no amount of configuration and reconfiguration seems to get the card to actually hook up to my wlan.

So 24 hours later and I am giving up on OOB support and hope following your guide tonight I will have linux wireless at last!! I am so tired of a 25m CAT5 trailing from my living room to the office just for internet access in linux :/

---

### Post by Tommerz on 2005-07-21
For some reason, this doesn't seem to work for me  :???: , even on a clean ubuntu install.

Any ideas what I've done wrong? I posted in the main network forum with the same question.

---

### Post by Seer on 2005-07-22
Well I didn't need to follow the guide as it happens...

Before attempting I removed ubuntu 64 as the app support is not as good and put ubuntu 32 instead...

Guess what!! Card working straight away even in the installer!! :D

---

### Post by Seer on 2005-07-23
Actually - i am fretting that my router is flashing its wireless light even when both pc's are switched off .... so time to get the WEP enabled even though I aint broadcasting my ESSID there are plenty of scanners around that discover it anyway :/

Wish me luck as I enter ndiswrapper land again!

---

### Post by MBro on 2005-07-31
Wow, good work.  Worked great for me.  I had the card working out of the box in the 386 kernel but when I tried using the k7 kernel I couldn't get any support for it, the drivers were loaded but the card couldn't see any access points.  I did your method and it worked.

NOTE:
k7 and 686 users need to change the dir to the proper kernel directory in the last set of steps

---

### Post by blakeyrat on 2005-08-05
Uh, stupid question, how do you download the ndiswrapper utility if you don't have a network connection?

I mean, I have a network connection on my Mac I could use, but how do I download it and get it installed into Ubuntu on my (unconnected) PC?  Is there a website?

---

### Post by CamB on 2005-08-10
[QUOTE=MBro]Wow, good work.  Worked great for me.  I had the card working out of the box in the 386 kernel but when I tried using the k7 kernel I couldn't get any support for it, the drivers were loaded but the card couldn't see any access points.  I did your method and it worked.

NOTE:
k7 and 686 users need to change the dir to the proper kernel directory in the last set of steps[/QUOTE]

I have this same problem (after upgrading the kernel from 2.8.10-5-386 to k7), except following the instructions above didn't fix it! I need to try one more thing (uninstalling and reinstalling ndiswrapper) as - forgive the noobness here - I think the kernel change requires that.

Where I'm at:

- have done "make install" of ndiswrapper (no errors, but a warning that the "windows driver has changed")
- have removed the current driver, and reinstalled
- "ndiswrapper -l" shows the driver and device ok
- "modprobe ndiswrapper" comes up with an error "windows driver couldn't initialize the device"

iwconfig shows no wlan0.

I have confirmed that acx_pci is not running.

Thanks for anyone's help :D

PS: Blakeyrat - I just use a USB flash drive to transfer stuff

(edit) Should add that it is a USB wireless adaptor, with the Prism Frisbee chipset.
(edit again) lsusb give 09aa:1000, and I've removed and reinstalled ndiswrapper 1.2 and it still returns the same error

(edit +2) Am posting this time from booting under the 386 kernel (and I had to recompile ndiswrapper to get it to work with this version, so I don't totally suck) so can confirm that it still works under one kernel but not the other.

---

### Post by CamB on 2005-08-10
[QUOTE=CamB]I have this same problem (after upgrading the kernel from 2.8.10-5-386 to k7), except following the instructions above didn't fix it!...

...(edit +2) Am posting this time from booting under the 386 kernel (and I had to recompile ndiswrapper to get it to work with this version, so I don't totally suck) so can confirm that it still works under one kernel but not the other.[/QUOTE]
 **Potential solution?**:

Just been reading the bugs over at ndiswrapper.sourceforge.net

[http://sourceforge.net/tracker/index.php?func=detail&aid=1163732&group_id=93482&atid=604450](http://sourceforge.net/tracker/index.php?func=detail&aid=1163732&group_id=93482&atid=604450)

I missed an apparently vital piece of information - I have _1Gb of RAM_ (and presumably installing the k7 kernel automatically turned support for this on).

I'm not sure I understand the answer here (too much of a n00b):

[http://sourceforge.net/tracker/index.php?func=detail&aid=1170764&group_id=93482&atid=604450](http://sourceforge.net/tracker/index.php?func=detail&aid=1170764&group_id=93482&atid=604450)

Can anyone help? Should I just turn the highmem support off in the k7 kernel (900mb is enough :D)? How would I do that?

---

### Post by CamB on 2005-08-11
[QUOTE=CamB]**Potential solution?**:
Can anyone help? Should I just turn the highmem support off in the k7 kernel (900mb is enough :D)? How would I do that?[/QUOTE]
 OK, it is "working" now.

From what I could figure out, if I wanted to have the kernel I have, but with highmem off, I need to recompile it. This appears to be unnecessary, as I have bodged it by modifying GRUB so that the kernel line includes mem=900mb. 

So I have been "successful", only if "successful" is another way of saying that I had to reduce my RAM to get there.

FWIW, I tried 950mb and 921mb, and neither worked.

---

