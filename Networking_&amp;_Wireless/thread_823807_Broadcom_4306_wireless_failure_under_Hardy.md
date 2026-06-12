---
title: "Broadcom 4306 wireless failure under Hardy"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by wrknight on 2008-06-09
I have a Belkin 54g (Broadcom 4306) wireless card that was working fine under feisty and continued to work fine under gutsy.  When I upgraded to Hardy with all the new updates (kernel version 2.6.24.18) the wireless crashed and burned. The response I get to the lshw -C networks command is the following:

*-network:0
  description:  Network controller
  product:  BCM 4306 802.11b/g Wireless LAN controller
  vendor:  Broadcom Corporation
  physical id:  9
  bus info:  pci@0000:00:09.0
  version:  02
  width:  32 bits
  clock:  33 MHz
  capabilities:  pm bus_master cap_list
  configuration:  driver=b43-pci-bridge latency=32 module=ssb

*-network DISABLED
  description:  wireless interface
  physical id:  1
  logical name:  wlan0
  serial:  00:30:bd:98:5c:0d
  capabilities:  ethernet physical wireless
  configuration:  broadcast=yes multicast=yes wireless=IEEE802.11g

No, I don't have two wireless cards, but there is a wired ethernet controller listed as *-network:1 that is working fine (so I won't list its details).

On booting up, both ndiswrapper and b43legacy modules are loaded.  Removing both modules and reloading ndiswrapper removes the *-network DISABLED entry from the lshw -C network list, but continues to identify driver=b43-pci-bridge in the *-network:0 list.  Also,the wireless interface disappears from the network settings control panel.

Removing ndiswrapper and reloading b43legacy retains the *-network:0 entry and restores the *-network DISABLED entry in the lshw -C network list.  It also restores the wireless interface entry in the network settings control panel.

Everything I have tried ends with "network is down" and/or "unknown hardware address type 801"

This controller continues to work well under Windows XP in the same computer (which is dual booted) and worked well under feisty and gutsy before I upgraded.

Please, someone, give me a hand here.

---

### Post by pytheas22 on 2008-06-09
The driver for Broadcom wireless changed between Gutsy and Hardy--Ubuntu now uses b43 by default instead of bcm43xx.  bcm43xx should be able to drive your card without an issue (I'm not sure whether you were using ndiswrapper or bcm43xx before, but either way, bcm43xx should work).  You should do this:

1. open a terminal and type:

sudo gedit /etc/modprobe.d/blacklist

look for a line that says "blacklist bcm43xx."  Delete this line and add the lines "blacklist b43", "blacklist ssb" and "blacklist ndiswrapper"

2. run:

```
sudo bcm43xx-fwcutter
```

You should be asked to download firmware; tell it yes.

Then reboot and see if the card works again.

---

### Post by wrknight on 2008-06-09
In the past, bcm43xx never worked at all with this controller.  I had to blacklist it under feisty and gutsy and install bcmwl5 which is the windows driver that came with it.

In the current version of Hardy, there is no b43.  It was replaced with b43legacy which also doesn't work with this card.

Since the first posting, I have found that executing the following commands
  rmmod b43legacy
  rmmod ssb
  rmmod ndiswrapper
  modprobe ndiswrapper
will give me the proper results when executing lshw -C network. Iwconfig now recognizes the card, shows that it has transmit power but fails to recognize the ESSID or associate with an access point. It also identifies the correct WEP code for the network.  I don't know why this does what it does and I don't like it, but it does.

---

### Post by pytheas22 on 2008-06-09
My Broadcom 4306 device has worked great with bcm43xx (b43 is another story) since Feisty, so I would encourage you to give it another shot if you get a chance.

Otherwise, you could try reverting ndiswrapper to the build that came with Gutsy, since card worked there.  I'm not sure how many other packages that might affect but I don't think ndiswrapper depends on very many.

Don't forget that no matter what you do, you'll need to add b43legacy to the blacklist.  That's probably the reason that lshw doesn't see your wireless card until you rmmod b43legacy.

---

### Post by wrknight on 2008-06-09
We're almost there.

I removed bcm43xx from the blacklist and blacklisted b43legacy, ssb and ndiswrapper.  (There is no b43.)  Installed bcm43xx-fwcutter, executed it and rebooted per your instructions.  Upon rebooting, network card does not work.  However, it turns out that the module ssb gets loaded at each boot even though it is blacklisted and the module bcm43xx does not get loaded.  

I can get the card started by first manually removing ssb and then loading bcm43xx.  (Reverse order fails.)  This must be done after each reboot.  So the remaining question is how to keep ssb from loading (blacklisting it doesn't do it) and how to load up bcm43xx automatically without manual intervention.

---

### Post by pytheas22 on 2008-06-09
Glad it's working with bcm43xx.  I don't know what ssb actually does it why it won't stay blacklisted, but you could try just deleting it and hopefully nothing will respawn it.  On my system it's located at /lib/modules/2.6.24-18-generic/kernel/drivers/ssb/ssb.ko.  I would keep a backup copy of it on hand though just in case something does need it.

---

### Post by Ayuthia on 2008-06-09
> **wrknight said:**
> We're almost there.

I removed bcm43xx from the blacklist and blacklisted b43legacy, ssb and ndiswrapper.  (There is no b43.)  Installed bcm43xx-fwcutter, executed it and rebooted per your instructions.  Upon rebooting, network card does not work.  However, it turns out that the module ssb gets loaded at each boot even though it is blacklisted and the module bcm43xx does not get loaded.  

I can get the card started by first manually removing ssb and then loading bcm43xx.  (Reverse order fails.)  This must be done after each reboot.  So the remaining question is how to keep ssb from loading (blacklisting it doesn't do it) and how to load up bcm43xx automatically without manual intervention.
I have not tested this, but this is a modified version of the ssb workaround for ndiswrapper:
```
echo -e '#Hardy ssb workaround, added' `date` '\ninstall bcm43xx modprobe -r b43legacy ssb bcm43xx; modprobe --ignore-install bcm43xx;' | sudo tee -a /etc/modprobe.d/bcm43xx
```
What this should do is back out the b43legacy, ssb, and bcm43xx modules and reload the bcm43xx module.  This will be executed every time you do a sudo modprobe bcm43xx.  If this does not work, all you have to do is remove the script:
```
sudo rm /etc/modprobe.d/bcm43xx
```

---

### Post by wrknight on 2008-06-10
Well, last night it was working.  This morning, it apparently didn't get much sleep last night and is very tired or something because it will no longer connect to the network. Responses to iwconfig indicate that it should be working except that it shows a very high noise level and an average signal to noise ratio of 0 db.  (Noise level about -65 dbm and signal level about the same.)  Booting the system up on windows, I get an average signal to noise ratio of about +20db (noise level about -85 dbm and signal level about -65 dbm).  As a result, I can't get it to connect to the network under linux, but it connects fine under windows. 

Any ideas?

---

### Post by pytheas22 on 2008-06-10
That's really strange.  Was noise-to-signal alright last night?  Was the machine suspended or hibernated in between the time it started and stopped working (I've had some trouble with suspend and the bcm43xx driver)?  Did you try a clean reboot?  Is the rate alright (also an issue with bcm43xx)?

---

### Post by wrknight on 2008-06-11
I didn't look at S/N the night before, but assumed that it had to be good.  However, I got really tired of fighting the battle and bought a cheap ($20) Zonet ZEW 1620A wireless card and installed it using ndiswrapper to load the windows drivers that came with it.

Fired it up, entered the WEP key and bingo!

I did find something interesting along the way.  I had to open my network (disable wireless encryption) for another purpose and found to my dismay that when I reset the encryption, I couldn't make the wireless connect.  On examination, I found that my router (D-Link DI-624) has the following security options:

Authentication:
  Open
  Shared Key
  WPA
  WPA-PSK

WEP:
  Enabled
  Disabled

When I chose Authentication = Open and WEP = Enabled, I found no corresponding option in linux (at least not in the gui interface) and the network wouldn't connect.  I had to set the router security to Authentication = Shared Key and WEP = enabled.

Anyway, thanks for your help even if I couldn't get the Belkin card running.  I learned a lot.

---

### Post by wrknight on 2008-06-11
OK, new but related problem.  Same el-cheapo card works fine until I re-boot.  After re-booting, the network monitor shows the card working fine, but firefox will not reach beyond the router.  Running dhclient fixes everything.  But the question is why doesn't dhclient automatically load in the boot process.  It always did in the past and it does on every other computer in the network.  (This is the only one with the latest updates.)

---

### Post by Ayuthia on 2008-06-11
> **wrknight said:**
> OK, new but related problem.  Same el-cheapo card works fine until I re-boot.  After re-booting, the network monitor shows the card working fine, but firefox will not reach beyond the router.  Running dhclient fixes everything.  But the question is why doesn't dhclient automatically load in the boot process.  It always did in the past and it does on every other computer in the network.  (This is the only one with the latest updates.)

You might check dmesg to see if any message comes up for your wireless.  It might have been possible that it connected and then lost the connection.  You might even check and see what is in /etc/network/interfaces and see if dhcp is set.

---

### Post by pytheas22 on 2008-06-11
> After re-booting, the network monitor shows the card working fine, but firefox will not reach beyond the router. Running dhclient fixes everything. But the question is why doesn't dhclient automatically load in the boot process. It always did in the past and it does on every other computer in the network. (This is the only one with the latest updates.)

If you're using dynamic IP, then I think the only way for things to work normally is for dhclient to run and fetch an IP address every time the interface is brought up (i.e. whenever the computer reboots).  Maybe for some reason however your card is keeping the IP address that it had before the reboot and is able to use it to send traffic out to the router, but the router thinks the card is dead and so doesn't know how to forward Internet traffic back to the card.  In other words, the card thinks it has a valid IP address, but the router doesn't recognize it, so it has to wait until dhclient is run again before both parties sync.

In either case, you could run dhclient whenever you log in to Gnome by adding an entry to the System>Preferences>Sessions list.  Or put a script in /etc/init.d to run dhclient whenever the machine boots.

---

