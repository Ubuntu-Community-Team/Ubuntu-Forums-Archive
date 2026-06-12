---
title: "Big Wireless problem"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by lordhaworth on 2008-06-27
Hey all
At the right of the top panel there is the networking symbol-->before when I clicked on it I would get a drop down with check boxes 'wired network','wireless network', manual configuration etc.
Well now I only get 'wired network' and 'manual configuration' My wireless options have just disappeared!

With a right click I now have the tick option by Enable Networking but again that option for wire less has now disappeared.

I dont really know what I did, but I could do with getting internet back on my other computer-is there some way I can get these options (and wireless) back?

Id rather not have to reinstall---> Oh yeah I'm using Hardy

Cheers All

---

### Post by pytheas22 on 2008-06-27
Please provide the output of:
```

lshw -C Network
iwconfig
iwlist scanning
dmesg
```

If you can't get any Internet connection on that machine (i.e. you can't plug in with a wire temporarily), then it's probably hard for you to copy all of the output of the commands above by hand.  If that's the case, let me know and I'll help you to work around that so you don't have to copy by hand.

---

### Post by lordhaworth on 2008-06-27
Heya
Cheers for the post.
I have got internet wireless working at the minute---> better than it was before, but only through connecting manually. I think for now thats ok to keep me going but it would be good to get it connecting automatically.

The result of those commands are:
lshw -C Network:
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:56:ff:d9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:4f:06:2b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.4 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g


IWCONFIG:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"SKY73129"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:2F:9A:79:BC   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=69/100  Signal level=-64 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




IWLIST SCANNING

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results



DMESG 

Is absolutely massive- do you still want this?

Thanks- By the way these commands were run while i was connected manually to my wireless

---

### Post by pytheas22 on 2008-06-27
If you can connect from the command-line, then it sounds like the problem is with Network Manager, not your card.  I'm not sure why NM would have broken suddenly, but it could have been a poorly tested update.  You might try using [wicd]("http://wicd.sourceforge.net") instead; it will do everything that NM can, but more reliably, in my experience.

---

