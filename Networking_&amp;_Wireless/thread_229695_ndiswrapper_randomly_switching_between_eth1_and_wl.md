---
title: "ndiswrapper randomly switching between eth1 and wlan0"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by diamond on 2006-08-04
I'm running Dapper on a Dell Inspiron 600m. I have ndiswrapper 1.21 installed, and generally it works fine.

However, it has a habit of sometimes switching the name of the wireless interface between "wlan0" and "eth1", and when it does it usually breaks wireless networking. This usually happens anytime I reboot after a configuration change (the last time was when I made a change to xorg.conf), and it *always* happens when I wake up from a hibernate.

Usually the fix is easy: just go to the "connection properties" dialog, click the drop-down menu, and select the correct interface (which is sometimes wlan0, sometimes eth1). Occasionally, this isn't enough and I have to reboot. Sometimes I have to reboot twice.

Does anyone have an idea what might be causing this? When I first set up ndiswrapper, I had a hell of a time getting it to work and the interface was originally called eth1. When I upgraded to ndiswrapper 1.21 and played around with it enough to get it to work, the interface was renamed to wlan0. So I suspect there's some vestigial setting laying around somewhere in a configuration file that's confusing ndiswrapper. But I just don't know where to look.

---

### Post by mdmarmer on 2006-08-04
You need to identify your wireless -- ipw2100, ipw2200 or Broadcom
If ipw2100 or 2200 --
There are native drivers for these which probably should work easily in Ubuntu Dapper.  You don't need ndiswrapper.  I suggest removing the ndiswrapper driver 
ndiswrapper -e xxxxx
and getting the native driver to work.

The wireless card has irq problems but can be fixed with pci=noacpi in grub or by disabling the parallel port in the bios.
=====
If Broadcom -- you need to blacklist bcm43xx

Search in this forum on 600m wireless

(on some laptops the native bcm43xx works better than ndiswrapper -- then you need fwcutter, your Windows drivers and blacklist ndiswrapper)

Mike

---

### Post by diamond on 2006-08-05
> **mdmarmer said:**
> You need to identify your wireless -- ipw2100, ipw2200 or Broadcom
If ipw2100 or 2200 --
There are native drivers for these which probably should work easily in Ubuntu Dapper.  You don't need ndiswrapper.  I suggest removing the ndiswrapper driver 
ndiswrapper -e xxxxx
and getting the native driver to work.

The wireless card has irq problems but can be fixed with pci=noacpi in grub or by disabling the parallel port in the bios.
=====
If Broadcom -- you need to blacklist bcm43xx

Search in this forum on 600m wireless

(on some laptops the native bcm43xx works better than ndiswrapper -- then you need fwcutter, your Windows drivers and blacklist ndiswrapper)

Mike

I have the Broadcom chip, and I did blacklist bcm43xx -- that was the only way to get the thing to work.

What configuration files are involved in networking and wireless networking?

---

### Post by ariel on 2006-08-07
I have a very similar problem, with ndiswrapper randomly switching after reboot between wlan0 and ra0 interface names. In my case, the driver always works with no problems and I always have a working connection, the annoyance is just the name change, which spoils the network applets.

I have a ralink 2500-based card (linksys wmp54g), and the native drivers don't work well in my configuration, a P4 with HT, and SMP kernel. I suspect the native driver has problems with smp; the wireless connection stops working every now and then.  Ndiswrapper doesn't have this problem.

Anyways, the random interface name change has been going on since I did my dapper fresh install. Since then I upgraded ndiswrapper to 1.19, but the problem persisted. I am using the latest available ubuntu stock (smp) kernel.

Any hint on how to stop this from happening would be greatly appreciated.

Thanks!

---

### Post by Aramis on 2006-08-07
> **ariel said:**
> I have a very similar problem, with ndiswrapper randomly switching after reboot between wlan0 and ra0 interface names. In my case, the driver always works with no problems and I always have a working connection,

Hi there,

I do have the same problem. However, when the name changes I do not have any connection whatsoever. How did you configure your wireless card so you can have connection despite the name swithc? I also have problem having the "link" light coming up, and I noticed if I dont have the light at startup I will not get wireless connection.

Gosh this all wireless nonsense is really a drag.

Ar@mi$

PS: my wireless network requires WPA.

---

### Post by ariel on 2006-08-09
> **Aramis said:**
> Hi there,

I do have the same problem. However, when the name changes I do not have any connection whatsoever. How did you configure your wireless card so you can have connection despite the name swithc? I also have problem having the "link" light coming up, and I noticed if I dont have the light at startup I will not get wireless connection.

Gosh this all wireless nonsense is really a drag.

Ar@mi$

PS: my wireless network requires WPA.

Hi Aramis,

   In my /etc/interfaces, I have two identical entries, one for the wlan0 "flavor", and another one with the ra0 "flavor" of my wireless card. Both were done by network manager, and are the same, both include the same ssid, wep, etc.

In my case the card always comes up and seems to work fine. The only weirdness is that the interface changes names every now and then.

Ari

---

### Post by Aramis on 2006-08-11
Hello Ariel!
> **ariel said:**
> Hi Aramis,

   In my /etc/interfaces, I have two identical entries, one for the wlan0 "flavor", and another one with the ra0 "flavor" of my wireless card. Both were done by network manager, and are the same, both include the same ssid, wep, etc.

Ah this is foundamentaly different from my setup. Since my Wireless configuration requires WPA (home) or LEAP (work) I followed various HOWTO and for WPA for a while I was successful. But none of the tutorial required the modification of the /etc/network/interfaces file. I recently learn that you can include any odd command in that file. Could you post yours?
> **ariel said:**
> 
In my case the card always comes up and seems to work fine. The only weirdness is that the interface changes names every now and then.

Ari
For the past few days, my card consistenly comes up as ra0 and consitently refuses to work. I have become an expert in following the HOWTO in 5 minutes flat. What trouble me the most is that in the past (when it was detected as wlan0 ???) the "link" LED of my wireless card always came up. And from then on I could configure the card manually or debug the configuration (wrong WPA key and so on). But nowadays, this LED hardly ever blink... I am starting to wonder if my PCMCIA interface isn't dead... Having said that the card would not be listed in the "lspci" command is that was the case.
Hence I can only assume that in your case your wireless card always indicates that it is active regarless of its name in the OS...

Deseparate Computer User Ar@mi$ (tm)

---

### Post by ariel on 2006-08-26
Hi Aramis,

this is the the /etc/networks/interfaces entry:

iface wlan0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid YOURSSID
wireless-key AAAAAAAAAAAABBBBBBBBBBBBCC
wireless-channel 6
auto wlan0

ra0 entry is the same, mutatis mutandi

---

