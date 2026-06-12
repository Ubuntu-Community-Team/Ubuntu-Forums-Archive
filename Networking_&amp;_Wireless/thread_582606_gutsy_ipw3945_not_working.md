---
title: "gutsy ipw3945 not working"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by themusicwave on 2007-10-20
I just upgraded to Gutsy and I love it with the exception of one issue.

My wirless is a bit messed up.  I have a dell inspiron E 1505 with and Intel IP3945  wirless card.

The issue is that the wirless card is not even seen.  I cannot turn the kill switch on no matter what I do, so the card is not even seen as installed.

In the restricted modules I see teh driver for IPw3945 but it is not in use even though it is enbled.

My wireless card doesn't appear on wconfig.

Only wire ethernet works.

help would be great.

Thanks!

---

### Post by rpeters on 2007-10-20
Same problem here with an Intel IP3945 wireless card in a Toshiba Satellite laptop, running Kubuntu 7.10.
iwconfig shows the interface, and I get ping responses :), but a web browser goes nowhere, and knetworkmanager sees no active card :(

---

### Post by BC7333 on 2007-10-20
Same problem here..  I think it may have to do with the following but have no idea how to fix it..

[edit] remarked out # the last line in /etc/udev/rules.d/70-persistent-net.rules, rebooted and wireless started working!

/etc/iftab

```
# This file is no longer used and has been automatically replaced.
# See /etc/udev/rules.d/70-persistent-net.rules for more information.
#

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

##eth0 mac 00:09:5d:15:60:23 arp 1
#wlan0 mac 00:19:D2:BB:50:59 arp 1
```

 /etc/udev/rules.d/70-persistent-net.rules

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:09:5d:15:60:23", ATTRS{type}=="1", NAME="eth0"

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:D2:BB:50:59", ATTRS{type}=="1", NAME="wlan0"


# PCI device 0x8086:0x4222 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:19:d2:bb:50:59", NAME="eth1"
```

---

### Post by themusicwave on 2007-10-20
I fixed it!

Well sorta it's not perfect but it does work.

First,  reboot and go into your BIOS.  On my Inspiron E1505 this is done by hitting F2 on startup on many computers it is delete.  It should say what to press on the screen.

There was a setting in there that set the wireless kill switch up.  I changed it so that the wireless and bluetooth would always be on regardless of the switch.

Next I booted into the generic kernel instead of the 386 kernel.  I only did this because only one of my cores was showing up.  Generic sees both.  Try using kernel 2.6.22-14-generic.

Finally, I reinstalled the Linux restricted module just to be safe with this command:

sudo apt-get install Linux-restricted-modules-2.6.22-14-generic

Then I went into the restricted drivers app by going to 

System -> Administration -> Restricted Driver Manager

If the ipw3945 driver isn't enabled, enable it and reboot.  If it is enabled disable and reenable it and reboot.

For some reason after the reboot I also needed to open my network manager and change it from WEP to WPA.  Close it then open it again and change it back to WEP.  I have no idea why but it wouldn't get online till I did this, I am using WEP 128 with a linksys router.


The other issue I had is the generic kernel didn't have Nvidia drivers so I was in low hardward mode.  Don't freak ot if this happens, I can walk you through fixing that as well.

Hope this helps,

Jon

---

### Post by rpeters on 2007-10-20
It works now!

Long story: 2 days ago I started the adept-upgrade from feisty to gutsy RC.  It did all the downloads but hung part way thru the packages setup.  So I killed it (had forgotten about using dpkg --configure -a) and was left with an unsatisfactory system (no internet, no audio codecs,...).

So yesterday I got the 7.10 image and installed to a different partition - with the subsequent no-internet complaint.

Now I've just booted back into 2.6.20-16-generic (with the half-complete setup) and run sudo dpkg --configure -a ... it completed the setup, and now I can use Firefox.

So far, that is.  Let's see what happens when booting into 2.6.22-14-generic... ;-)

[edit] Works here too.  Fixing /boot/grub/menu.lst and doing grub-install helps a lot ;-)
Thanks for the responses.

---

### Post by ElVirolo on 2007-10-29
Same problem here, but that particular solution doesn't work...

---

### Post by ge0matrix on 2007-12-01
musicwave thank you so much!!

this solved my probs! My wireless card is recognized again! 

I think the trick was to disable and re-enable the card under system->administration->restricted drivers manager (although i did some other things i found in some other posts, so it may be something else or a particular combination, but it works now!) :):guitar:

---

### Post by spacetree on 2008-01-07
Hi I just upgraded from feisty to gutsy (i shall remark that in feiste wireless worked fine).

The wireless card was listed by lspci , but not working. My first approach was activating it in the restricted manager , but it complained about some package missing ( about restricted modules) The mentioned package did not exist for my kernel ( generic ), so I decided to install de i386 kerne.  Now I installed the generic modules package and reopened the restricted manager and activated it. The problem is that it stills say "not in use"  (with the red dot). 

I have also tried manually loading the module ipw3945 but it says that is not present.

Somewhere I read that I could manually compile my driver, but I had some problems. I someone has done it already , it would be good to point to some tutorial, please.

¿What should I do? ¿Why it worked fine in festy but not in gutsy?

---

