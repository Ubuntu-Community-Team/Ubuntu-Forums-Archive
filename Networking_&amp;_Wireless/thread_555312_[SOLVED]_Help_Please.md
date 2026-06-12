---
title: "[SOLVED] Help Please"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by deroldj on 2007-09-20
I installed Ubuntu ultimate 1.4, and could not connect to internet. I then tried ubuntu 6.06 and same problem.I have a DSL connection with  Nettopia Caymon 3300 modem, useing ethernet. Both programs say my eth0 is active, but DHCP is unsuccesful. I tried setting it manually, but still not working.
I ran ppppoeconf, said network card found, but no reply from access concentrator.
I ran /etc/network/interfaces:
  Auto lo
  iface lo inet loopback

  Auto eth0
  iface eth0 inet dhcp

  auto eth1
  iface eth1 inet dhcp

  auto eth2
  iface eth2 inet dhcp

  auto ath0
  iface ath0 inet dhcp

  auto wlan
  iface wlan inet dhcp

dont know what to try. The modem works on same computer, different drive with windows xp

---

### Post by noob12 on 2007-09-20
Can you post the output of these commands run on that box
```

lspci -nn

sudo lshw -C network

ifconfig -a

```

---

### Post by deroldj on 2007-09-22
ifconfig I ran this am, so have now, will post others soon


etho
link encap:eternet hwadder 00:11:D8:73:62:bb
up broadcast running mult.cast mtu:1500 metic:1
rx packets:0 error:0 dropped:0 overruns:0 frame:0
tx packets:0 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:1000
rxbytes:0 (0.0b) txbytes:0 (o.ob)
interupt:21 base address 0x2400

etho:avah
linkencao:ethernet  hwaddr 00:11:D8:73:62:bb
inet addr:169.254.8.74 bcast:169.254.255.255 mask: 255.255.0.0
up broadcast running mulicast mtu:1500 metric:1
interupt:21 base address 0x2400

lo
linkencap:local loopback
inet addr:127.0.0.1 mask 255.0.0.0
up loopback running mtu:16436 metric:1
rx packets:436 errors:0 dropped:0 overruns:0 frame:0
tx packets:436 errors:0 dropped:0 overruns:0 frame:0
collision:0 txqueuelen:0
rx  bytes:34444 (33.6kib)  tx bytes:34444(33.6kib)

---

### Post by deroldj on 2007-09-22
lSPCI -nn

00:if.0 ISA bridge[o6o1]:Intel corporation 8280/FB/FR 9ich6/ich6r) lpc
   interface bridge [8086:2640] (rev03)
oo:if.1 IDE interface [0101]:Intel Corporation 82801/FB/FBM/1FR/FW/
   FRW (ich6 family) IDE controler [8086:266F] (rev 03)
oo:if.2 IDE controler [0101]:Intel Corporation 8280/FB/FW (ich6/
   ich6w) sata controler [8086:2651] (rev03)
03.02.0 ethernet controler [0200] Realtek semi conductor co. RTL-8139/
   813 9c/8139 c+ [10ec:8139] (rev10)



sudo LSHW -C NETWORK   only produced errors, asking for more info. I tried to add more but couldnt get it to work

I just read another post about problems with the 8139 realteks after upgradeing, and that seems to be when my problems started, but I have tried all suggested steps and they dont seem to work. I can see the moden through the ethernet, but cant get ubuntu to talk to it.

---

### Post by noob12 on 2007-09-22
When you type the commands the capitalization has to exactly match the ones posted.  Also, it looks you are trying to transcribe the output back.  See if you can find a USB jump drive so that you can save the output to text files on the drive and post from them.

You have a Realtek 8139 card.  Are you dual booting Windows on this box?  Is Windows working fine with the modem?

Boot with the card plugged into the ADSL modem.  Once you have booted, check this

```

sudo ethtool eth0

```

Look for the 'Link detected' line.  If it says no.  Then try this thread [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

If it says yes, then first try **sudo /etc/init.d/networking restart**.  See if you are connected by pinging your router.

If you aren't, then if you do have a Windows box working through this modem/router, then boot that
and post the output of **ipconfig /all** and **route print** from the Windows box.  They'll be useful.

---

### Post by deroldj on 2007-09-22
As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this option through Windows' device manager.
windows at fault...NO way:confused:

---

### Post by noob12 on 2007-09-22
Yes, that's the thread I posted.

---

