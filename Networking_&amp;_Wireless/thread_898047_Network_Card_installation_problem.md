---
title: "Network Card installation problem"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by buntu_guy on 2008-08-22
I just installed xubuntu 8.04 on an old laptop - Dell Lattitude C.
No built in NIC, but I had two wireless cards installed during the software install - Aironet 350, and Linksys wireless ver 3.
After the install, both cards show up in the pccardctl ident, but the /etc/network/interface file shows only the local loopback.
lsmod shows modules installed for both cards and for pcmcia.

_ifconfig shows:_
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:700 (700.0 B)  TX bytes:700 (700.0 B)

_lshw -C network shows:_
  *-network
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network
       description: Instant Wireless Network PC Card
       product: ISL37300P
       vendor: The Linksys Group, Inc.
       physical id: 0
       version: RevA
       slot: Socket 1

It would appear that though the modules are installed, no logical device is assigned to them.  I'm afraid this has surpassed my limits on linux. 

I had another card laying around - Xircom XEM5600 10/100 NIC +56k modem.  I thought maybe I could use this to gain network access.  I pulled both the wireless cards and put this one in and rebooted.  Once again _pccardctl ident_ shows the card, and lsmod shows the proper module installed, but this time _lshw -C network_ returns nothing at all.

I feel like there must be a simple fix, since the card is obviously being recognized and the proper module is being installed, but there is a missing link.
Since I have no network, I can't very well do any updates or anything.

Can someone please suggest a fix.

Thanks

---

### Post by pytheas22 on 2008-08-22
What is the output of these commands with the two cards plugged in:
```

lspci -nn
ifconfig -a
```

---

### Post by buntu_guy on 2008-08-22
Looks like they don't show up in either one.

[FONT="Fixedsys"]lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:03.0 CardBus bridge [0607]: Texas Instruments PCI1225 [104c:ac1c] (rev 01)
00:03.1 CardBus bridge [0607]: Texas Instruments PCI1225 [104c:ac1c] (rev 01)
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:08.0 Multimedia audio controller [0401]: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator [125d:1998] (rev 10)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage Mobility P/M AGP 2x [1002:4c4d] (rev 64)
[/FONT]

ifconfig -a
[FONT="Fixedsys"]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:900 (900.0 B)  TX bytes:900 (900.0 B)
[/FONT]

---

### Post by pytheas22 on 2008-08-23
Take a look at this [thread]("http://www.linuxquestions.org/questions/linux-hardware-18/problem-with-pcmcia-wireless-card-40195/") and the link mentioned in the second post.  I believe that they deal with the same kind of card as your Linksys one.  I think that the file you need to edit in Ubuntu is /etc/pcmcia/config.opts, not /etc/pcmcia as in other distributions (but I could be wrong as I've never dealt with similar stuff myself).

I also found [this page]("http://beginlinux.com/desktop_training/ubuntu/ubnet_m/ub_wirless") which purports to have instructions for the Cisco card--scroll down to the "Manual Card Install: Cisco 350 Series" section.  I'd try this before dealing with the Linksys card.

You may also want to take a look at this [bug report]("http://beginlinux.com/desktop_training/ubuntu/ubnet_m/ub_wirless"), also dealing with the Cisco card.  It says that having the card in at boot causes the system to hang, which I assume isn't happening for you or you would have mentioned it.  But the report also mentions adding some modules to the blacklist (see the post from Fred L), which may make a difference.

Hopefully between all of these things you'll be able to get one of the cards working.  Please let us know.

---

### Post by buntu_guy on 2008-08-23
I've tried the Cisco card without success.  Instructions were to add some lines to /etc/pcmcia/config.opts.  It seemed to me there was an extra " in the text to be added (first line) but I tried it both ways.
In step 3 it says to kill the cardmgr by probing in /var/run/cardmgr.pid for the process id.  I did not find that file, which indicates to me that maybe the cardmgr is not running.
I tried reboot after the changes to config.opts, but [FONT="Courier New"]lshw -C network[/FONT] showed no changes regardless.

Do you think I've a problem with cardmgr?  Looking through my running processes, I find two called pccardd (I have both wireless cards installed) which seems to be the card manager, but I'm not sure.  I'm concerned that its not running since it didn't show up in /var/run/cardmgr.pid

Thanks for your help so far.  I'll run off and try the linksys now, but if my suspicions are correct, the same problem plagues them both.

---

### Post by burnit on 2008-08-23
wlanconfig ath0 create wlandev wifi0 wlanmode sta

---

### Post by pytheas22 on 2008-08-23
> Do you think I've a problem with cardmgr? Looking through my running processes, I find two called pccardd (I have both wireless cards installed) which seems to be the card manager, but I'm not sure. I'm concerned that its not running since it didn't show up in /var/run/cardmgr.pid

I don't know too much about how cardmgr works to know if that could be the problem.  You might want to try reinstalling, or at least booting to the live CD, to see if cardmgr appears to behave any differently.  It's possible that a bad installation screwed things up--and since I wasn't really able to find evidence on the Internet of people having trouble with these two wireless cards in modern versions of Linux, I'm inclined to believe that they should be working.

Please let us know if you have any better luck with the Linksys card.

---

