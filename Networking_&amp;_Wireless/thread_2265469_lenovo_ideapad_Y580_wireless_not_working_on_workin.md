---
title: "lenovo ideapad Y580 wireless not working on working on 14.01"
date: 2015-02-15
forum: Networking &amp; Wireless
---

### Post by andrew199 on 2015-02-15
Hi, I've been looking through this forum for a solution to my problem without success. The wireless on my Lenovo laptop isn't working and I don't know why. I'm a slight linux noob so bear with me, with some searching online I got this far:

sudo lshw -C network:
```
*-network                      description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 08
       serial: dc:0e:a1:fa:98:42
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:d3600000-d363ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Wireless-N 2200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: c4
       serial: 9c:4e:36:3e:6c:b8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-45-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:44 memory:d3500000-d3501fff

```
sudo rfkill list all
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```iwconfig
```
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

When I go into my network settings there is an on/off switch in the wireless settings, which immediately goes back to "off" when I try to move it to "on".
Any help would be greatly appreciated, thanks Andrew

---

### Post by Bucky Ball on 2015-02-15
*Thread moved to **Networking & Wireless**.*

More chance here. Seems to be hardblocked, as shown by this output:

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

Is there an actual switch for wireless anywhere on the computer? An FN key combination perhaps (FN + F8)?  That is sometimes the case. Watch for the wireless light to go blue (is it currently not blue?). Other things look fine (I'm pretty sure that is the correct driver you have installed).

Try running this command in a terminal:

```
rfkill unblock all
```

---

### Post by Pilot6 on 2015-02-15
There is no hardware switch.
You can unblock it by

sudo modprobe -r ideapad_laptop

And also you may make a bugreport. I know how to fix it, but I am ignored in platform mailing list. So someone else can fix it.
Or I can commit it to my kernel image.

---

### Post by andrew199 on 2015-02-15
Thanks for the quick response Bucky Ball. 
There is no wireless indication light, and the FN combination (which for this machine is would be FN + F5, from the icon beneath the F5 key) does nothing (looking at the network setings-window). 
This machine doesn't have a hardware wireless switch. 
The terminal command doesn't gives any response and doesn't seem to do anything...regretfully.

---

### Post by Pilot6 on 2015-02-15
It should not give any output. Jusd do

[COLOR=#000000]sudo modprobe -r ideapad_laptop
sudo rfkill unblock all

And show 

rfkill list[/COLOR]

---

### Post by andrew199 on 2015-02-15
rfkill still gives the same response Pilot6
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

---

### Post by Pilot6 on 2015-02-15
Try to update the kernel, which in a couple of days will be in 14.04.2
Just run

sudo apt-get install linux-generic-lts-utopic

Then reboot. If it does not work, try same commands I gave before.

---

### Post by andrew199 on 2015-02-15
Done, no change...
(I'll leave it for today. Start again fresh tomorrow...thanks for the input so far, it's appreciated.)

---

### Post by andrew199 on 2015-02-16
So, does anyone have a different idea? The problem has been circumvented now because we managed to get wired access, so there is no real urgency. But I would like to be able to use the wifi when I want to...

Any new insights?

---

### Post by Bucky Ball on 2015-02-16
Try these three commands one at a time if you haven't done a full update since install:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Then restart and give us the output of:

```
sudo lshw -C network
```

... again.

---

