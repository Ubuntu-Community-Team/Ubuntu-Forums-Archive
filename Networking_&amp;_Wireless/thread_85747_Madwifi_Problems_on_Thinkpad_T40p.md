---
title: "Madwifi Problems on Thinkpad T40p"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by suRoot on 2005-11-03
Hi -

I originially posted this here:  [http://ubuntuforums.org/showthread.php?t=75451&page=2]("http://ubuntuforums.org/showthread.php?t=75451&page=2"), but I'm going to repost it here in hopes that this is a more appropriate forum.

Any suggestions??

My /etc/network/interfaces file (put together based on another how-to that I read)

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
#       script grep
#       map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp
# wireless-mode managed
# wireless-essid foo

# auto eth1

auto eth0

# Wireless
auto ath0

# static
#iface ath0 inet static
#    address 192.168.1.66
#    netmask 255.255.255.0
#    broadcast 192.168.1.255
#    up /sbin/iwpriv ath0 mode 3
#    up /sbin/iwconfig ath0 essid "blabla" rate 54M key 14929429325878194789834632

# dhcp

        iface ath0-dhcp inet dhcp
                pre-up modprobe ath_pci || true
                post-down rmmod ath_pci ath_hal wlan || true
                wireless-essid any
                wireless-mode Managed
                wireless-ap any
                wireless-nick "Zodiac"
                # Note: this is powermanagemnt off, not power off
                wireless-power off
                wireless-txpower auto

```

Output of dmesg:

```
ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
ath_rate_onoe: 1.0
ath_pci: 0.9.6.0 (EXPERIMENTAL)
```

ORIGINAL POST:

I seem to be having some trouble getting this to work on my thinkpad (t40p).  I've followed the instructions here as well as the official madwifi site, but no dice.

I've built my own kernel based on 2.6.12 from kernel.org.  I built the modules base d on the instructions here:  [http://www.marlow.dk/site.php/tech/madwifi]("http://www.marlow.dk/site.php/tech/madwifi"), and I had no problems building the module.  It seems to load fine with my kernel:

```
$ lsmod | grep ath
ath_pci                70172  0
ath_rate_onoe           7432  1 ath_pci
wlan                  131612  2 ath_pci,ath_rate_onoe
ath_hal               146832  1 ath_pci
```

I've added

```
ath_pci
```

to the end of /etc/modules

I can find no trace of ath0, though!

```
$ ifconfig ath0
ath0: error fetching interface information: Device not found

$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:09:6B:3F:54:95
          inet addr:192.168.99.62  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe70::209:6bff:fe3f:5495/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1373 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1056 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:925233 (903.5 KiB)  TX bytes:162069 (158.2 KiB)
          Base address:0x8000 Memory:c0220000-c0240000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3608 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:328066 (320.3 KiB)  TX bytes:328066 (320.3 KiB)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

Under redhat, we'd always add an entry to /etc/modules.conf with something like "alias ath0 ath_pci", but that doesn't seem applicable with Debian / Ubuntu?  From what I read, it looked like you might do something similar under /etc/modules.d/, create a file with the name of the module, but that didn't make a bit of difference for me.

If I boot the default Breezy kernel, my wireless NIC does show up - it loads the ipw2100 module & shows up as eth1.  However, even though I can see the ssid of any of the access points I've tried, I never associate... never get an address, never get squat.  Based on the reading I've done about the T40P, I suspect that this is the wrong driver, anyway (everything I've read has said to use madwifi).

Can anyone offer any suggestions?  This is the only part of my laptop not working since installing Breezy.

Thanks!

---

### Post by suRoot on 2005-11-14
I hate to bump my own thread, but I'm kind of in a bad way here.  Going out of town next week & know I'll need wireless at the hotel.  Anyone have any ideas?

Thanks!

---

### Post by Lambert on 2005-11-14
Is this an internal device or a card in a slot?

Run this command and post output of just the wireless device part

```
sudo lshw -C network

```

If it doesn't show up then try running just

```
sudo lshw
```.

---

### Post by suRoot on 2005-11-14
Thanks for the reply.

This is an internal wireless card  - it's an Intel 2100 3B.  Prior to installing Ubuntu, most of the sites I visited regarding Linux on the T40p said to use the madwifi driver with this card.  That was what I'd been trying, but wasn't getting anywhere, per the post above.

The base Ubuntu install seemed to be using ndiswrapper, as the card showed up  in all the network config tools.  As such, I've fallen back to trying to get ndiswrapper to work.  Like I say, the card shows up in the network config tool & I can even see the ssid's of the wirless nets I have in range.  However, I never get an address from the DHCP server.  If I statically assign an address, I can ping myself, but nothing else on the LAN.

```
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: wlan0
       version: 04
       serial: 00:04:23:86:70:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper ip=192.168.3.18 link=no multicast=yes wireless=IEEE 802.11b
       resources: iomemory:c0210000-c0210fff irq:11
```


```
iwlist wlan0 scanning

wlan0     Scan completed :
          Cell 01 - Address: 00:0B:85:09:6D:20
                    ESSID:"foo"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-35 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

---

### Post by Lambert on 2005-11-14
Where did you see this uses madwifi driver? I show it uses the ipw2100 driver.

[http://www.thinkwiki.org/wiki/Intel_PRO/Wireless_LAN_2100_3B_Mini_PCI_Adapter](http://www.thinkwiki.org/wiki/Intel_PRO/Wireless_LAN_2100_3B_Mini_PCI_Adapter)

Look to see if ipw2100 is loaded by running 

```
lsmod
```

You can grep to limit the output.

There may be a conflict with the two drivers.

---

### Post by suRoot on 2005-11-16
I'm sorry, I really haven't had any time to even look at this the past few days.  As it turns out, I found an old DWL-650 PCMCIA card in one of my "junk" drawers & it works perfectly.  Works for me until I have time to figure this one out.  Thanks for your help.

---

