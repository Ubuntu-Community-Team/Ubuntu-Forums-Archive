---
title: "Access Point: Not-Associated (TrendNet TEW-421PC card, D-Link DIR 615 router)"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by spinhead on 2011-01-24
invested two days so far trying to get my TrendNet TEW-421PC pcmcia card to connect to the DLink router here. on a Sony Vaio laptop. eth0 wired connection works just fine.

interesting; the 'about' info says:

You are using Ubuntu 11.04  - the Natty Narwhal - released in April 2011

so this version will be released in three months from now. huh.

router is wide open; no security or restrictions of any kind.

iwconfig returns

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"wilson"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

also, rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

lshw -C network returns (regarding wireless)

       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 20
       serial: 00:14:d1:3a:c8:b8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 driverversion=2.6.35-24-generic firmware=N/A latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg

went through the troubleshooting tips here, and didn't resolve this.

thanks

---

### Post by cariboo on 2011-01-24
I'd suggest you try associating pcmcia card with you ap manually, I had to do this on openSUSE to get my wireless to work. Try the following commands in a terminal:

```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

For more info have a look at [this]("http://ubuntuforums.org/showthread.php?t=571188") thread.

---

### Post by the.phantom on 2011-01-24
> You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011

sounds like you downloaded the ALPHA version ( don't think it is beta yet)
the latest release of stable ubuntu is 10.10 Mavrick


might want to try that version as it is supported ?

---

### Post by spinhead on 2011-01-25
> **cariboo907 said:**
> I'd suggest you try associating pcmcia card with you ap manually, I had to do this on openSUSE to get my wireless to work. Try the following commands in a terminal:

```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

For more info have a look at [this]("http://ubuntuforums.org/showthread.php?t=571188") thread.
That thread says this, which seems to apply:

By default the r8187 and r818x drivers are blacklisted due to a know  bug.  These drivers are usuable however with a twist to the above  methods

If you want to try using these drivers, please load the kernel modules:
 	Code:
 	sudo modprobe r818x
sudo modprobe r8187 
However:

fiona@Valentia:~$ sudo modprobe r818x
FATAL: Module r818x not found.
fiona@Valentia:~$ sudo modprobe r8187
FATAL: Module r8187 not found.
fiona@Valentia:~$ 

I'm sure the solution is downgrade to a stable version of Ubuntu and use a better supported card, but my goal is to get this battered old laptop usable for my 6-year-old without spending more money I don't have (otherwise, I'd just buy a netbook with *NIX preinstalled.)

Appreciate the help . . .

---

