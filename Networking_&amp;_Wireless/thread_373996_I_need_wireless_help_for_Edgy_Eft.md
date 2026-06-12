---
title: "I need wireless help for Edgy Eft"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by oranguman on 2007-03-01
hi. I've been trying really hard to get on my network in Edgy. The progress I had made allowed me to get on open networks, but I had no luck on WEP or WPA. I tried to install Network-Manager most recently, and got the applet going, but I can't make it recognize my card. I think my settings may have been messed up as I tried about everything. 

Experts: please appraise my Wifi settings and give me any clues that come to mind, to help me resolve this situation.

Thanks for your time!! Here's iwconfig, ifconfig, etc/network/interfaces/, lspci, and applicable modules. 

x@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          
sit0      no wireless extensions.



x@laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:0D:C3:1F:5F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)



 /etc/network/interfaces

auto lo
iface lo inet loopback


#iface eth0 inet dhcp

lspci: 
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)

Module                  Size  Used by
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap

orinoco_cs             17412  1 
orinoco                47760  1 orinoco_cs
hermes                  9984  2 orinoco_cs,orinoco
pcmcia                 40380  1 orinoco_cs

rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
parport_pc             37796  0 
parport                39496  2 lp,parport_pc
mii                     6912  1 e100

---

### Post by Floppyjoe on 2007-03-01
I had a problem with network manager not recognizing my wireless card and my solution is here:

[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=4](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=4)

I don't know if this will work for you but it did for me.

---

### Post by oranguman on 2007-03-01
thanks for the tip. I'm trying the interface renaming strategy now.

edit: no such luck; renaming the interface in /etc/iftab didn't allow nm-applet to see my wireless card :(

---

### Post by Floppyjoe on 2007-03-01
Did you restart networking or reboot your computer?

---

### Post by oranguman on 2007-03-01
I rebooted.

I assume by restarting networking you mean "ifdown"/"ifup"?
?

---

### Post by buttyshell on 2007-03-02
just a thought try changing your ESSID to a lowercase name as I was having problems connecting to my router via wireless and when I changed it to lowercase from uppercase I started connecting, just a thought from a noob to Ubuntu but it might work

---

### Post by oranguman on 2007-03-03
thanks for the input. the "nickname" is actually an identifier for the chipset of the wireless card. the "iwconfig" above is from when I wasn't associated with a router or ESSID. 

I have an update; I got network-manager to run (and it is very nice too). it took countless edits of my interface file, and resets of all kinds.. but it seems quite stable. Finally it was a hard network reset (the 3rd or 4th one) that got the applet to see my wireless card.

this leads to the FINAL list of wireless questions I need help with; i really appreciate people's time in reading this bloggy post.. but I thought it might really help someone if I sort-of journal as I resolve my issues.. so, problems:

1. Can't resolve WEP, period. Must be missing something small here. Open networks and wired connection only.. ive tried tons of stuff. 

2. Don't know how to edit preferences in nm-applet (permissions issue)

3. nm-applet doesn't show the bars which relate to network strength.

that's it. just throwing these issues out for any insights that may arise.

---

### Post by chili555 on 2007-03-03
Here's a pretty decent WEP posting: [http://www.ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep](http://www.ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep)

Hope it helps.

---

### Post by Buster95 on 2007-03-03
Hello Chili555,
Not trying to hijack this thread but just letting you know that I'm still struggling to connect Edgy to through my wireless router to my modem. I repeated all the various steps we went over yesterday and to paraphrase the words of Omar Khyyam "I came out the same door wherein I went". I would appreciate if you could find the time to help me again in the other thread.
Regards
Buster 95

---

