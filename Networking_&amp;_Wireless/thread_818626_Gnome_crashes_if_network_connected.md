---
title: "Gnome crashes if network connected"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by Peter09 on 2008-06-04
I've just upgraded my friends laptop to Hardy and I am experiencing the following problem.

The system boots ok, however logging in with the network attached leads to a black screen with a white box in the left hand corner. It appears as if Gnome has crashed. I can move the cursor but have no desktop. Control-Alt-Backspace will get me back to the login prompt.

If I disconnect the network lead before logging in I can log in ok and all works, indeed I can then reconnect the network and the system works as normal with full network performance.

I initially suspected the network card, but I replaced that with a different one and I still get it.

I have tried removing compiz but to no effect. 

Can anyone help?

PC

---

### Post by dmizer on 2008-06-04
well, i'm having difficulty imagining what could possibly be wrong.

try posting some more information on your adapter:
```
lspci
```
and
```
lshw -C network
```
network adapter chipsets are often identical even if you have a different manufacture name on the card itself, so it's possible you merely replaced a troubled card with the same card.

you might get things to work if you disable NetworkManager:
[https://help.ubuntu.com/community/NetworkManager?#head-d279c8fbfc4d1711bb8e3a03a4b71c810878b0eb](https://help.ubuntu.com/community/NetworkManager?#head-d279c8fbfc4d1711bb8e3a03a4b71c810878b0eb)

do you have a custom theme installed?

---

### Post by Peter09 on 2008-06-05
Hi,
yes I am having problems seeing where the connection is as well. 

The chip manufacturer is the same on both cards Realtek that I have used, however the driver is different.

No particular theme installed, I am using compiz and emerald, there is a low end nvidia card installed.

I'll post the details that you have asked for when I get to the machine.

I am feeling a bit embarrassed about this as I have sold him the benefits on Ubuntu over the last year only now to be in a position where I cannot get it to work.:(

PC

---

### Post by Peter09 on 2008-06-05
Here is the ninformation from the working machine.

lspci

> leonard@desktop:~$ sudo lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)


lshw -C network

> leonard@desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth2
       version: 10
       serial: 00:06:4f:5f:da:1e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.13 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s


---

### Post by dmizer on 2008-06-05
please post the contents of:
```
/etc/network/interfaces
```

just to make sure ... disabling networkmanager had no effect?

---

### Post by Peter09 on 2008-06-05
Hi,
well just found a work around which has solved it - installed Wicd.

Obviously its an issue with network manager. Is this a known bug?

Thanks for your help on this

PC

p.s. now to start a new thread on why it takes 3 or 4 min for the logout screen to appear
:-)

---

### Post by dmizer on 2008-06-05
not necessarily a known bug with networkmanager, but it does cause strange problems on login for some reason.  i've run into enough problems with it that it's often the first thing i do when i install a new system.

> **Peter09 said:**
> p.s. now to start a new thread on why it takes 3 or 4 min for the logout screen to appear
:-)
the fix for that is mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

-Bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078)
-Workaround: Reenable the gnome-power-manager in Administration-Sessions.

---

### Post by Peter09 on 2008-06-05
Well thats what I thought until another reboot. Now WiCD behaves just like networkmanager, in fact slightly worse as it needs to boot without a network connected at all to allow me to login. Once there I can connect.

Damn

PC

---

### Post by dmizer on 2008-06-05
just remove wicd and use:
system > administration > networking 

to configure your network.  there's really no need for wicd or networkmanager.  especially if you have no wireless.

---

### Post by Peter09 on 2008-06-06
update:

I removed wicd and setup the network as dmizer suggested and yes- it works. Thanks very much to dmizer.

Some theories on what was happening:

1. The fault was occurring with both wicd and network manager
2. I think the fault did not occur with wicd with no panel applet (not definitive)

So as a first guess I wonder if the machine/graphics/gnome failed at the point where the network applet was trying to be installed into the panel.

Some sort of bug in the system, but where I do not know, also it does not seem to be common as not many are suffering.


PC

---

### Post by dmizer on 2008-06-06
your problem was most likely related to compiz.  for some reason (on your computer) compiz didn't agree with your notification area (where wicd and networkmanager are located)

---

