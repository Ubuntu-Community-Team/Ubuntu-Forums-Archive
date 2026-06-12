---
title: "Another 3945ABG Problem"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by spadge67 on 2008-08-30
Good Evening!

After what seems like days (in reality about 8 hours) of reading through just about every post on here about the various 3945ABG issues people have had with Ubuntu Hardy (8.04 I believe) I finally admit defeat and appeal to you all for help.

I have downloaded Ubuntu Desktop (ubuntu-8.04.1-desktop-amd64.iso).

As stated above, my only issue after install is the Intel 3945ABG card does not work.  It does not show a wireless networking option in the System>Network window.

When booting to the LiveCD, it works just fine, which I find odd (but then again, I'm the one asking for help, so my opinions are moot at this point).

Results of command **sudo lshw -C network** - 

```

###@######:/etc/udev/rules.d$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:59:44:2a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945
###@######:/etc/udev/rules.d$ 


```

This is my **70-persistent-net.rules** file - 

```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:09:59:44:2a", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:3c:4f:b9:60", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

###@######:/etc/udev/rules.d$ 


```

Results of **sudo iwlist wlan0 scan** gets me the good ol does not support scanning message.

**sudo modprobe iwl3945** returns no errors.

I have tried getting ndiswrapper working, but it does not seem to work either.

I seem to have tried all the solutions put forth to others for this problem to no avail.  SO, just in case I bunked something up (entirely possible) I have installed Ubuntu again, so at this current moment, I am working from square 1.  On my previous install there were two instances where I logged in, and it worked like a charm, all to disappear to my dismay on reboot.

I'm more thank happy to post the results of any other command, I think I included most of the often-requested ones, but its very possible I missed one or two =)

Any reply is greatly appreciated.

Thanks!

**EDIT**
If it makes any difference, I have no wired connection available, I get my internet through my apartment complex via wireless (bleh).

---

### Post by cdtech on 2008-08-30
I'm sure you've been to just about every site.
> The iwlwifi project can be found in kernels 2.6.24 and up. You thus do not need a driver from this site if you are using one of these kernels.
[http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi)
> Any reply is greatly appreciated.

Just throwing something out there.......

---

### Post by spadge67 on 2008-08-30
I had read that page, but I'm lacking the know-how to implement the iwlwifi driver instead of the iwl3945.

I looked around for instructions but came up short... Any other links? =)

Thanks!

---

### Post by spadge67 on 2008-08-30
OK, well I re-read that page again, and downloaded the newest compat-wireless tarball (08-06-2008 ) and did the following...

Extracted the tarball, did a **sudo make** then a **sudo make install** followed by a **sudo make unload** then **sudo make load**.  I did not get any noticeable errors.  Only error I saw was after the **sudo make unload** it said that cfg80211 could not be unloaded for some reason, would this stop the iwlwifi driver from installing correctly?

Is that correct for installing the iwlwifi driver?

If it was, that did not fix my problem.

Thanks!

Also, after downloading the tarball from windows and then restarting into my Ubuntu install, the wireless worked!  This had happened before, so I restarted twice, and after the 2nd restart it quit again.  It just seems crazy that it would go on and off like that for no (apparent) reason.

While cruising around here are the results of a few other commands others have asked for when troubleshooting similar problems...

**lspci | grep Network**


```
###@######:~$ lspci |grep Network
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```


**iwconfig**

```
###@######:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```


**uname -r**

```
###@######:~$ uname -r
2.6.24-19-generic
```

---

### Post by spadge67 on 2008-08-30
bump

Thanks!

---

