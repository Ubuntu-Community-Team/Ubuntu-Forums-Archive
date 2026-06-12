---
title: "Atheros AR5212/5213 Connection Drop Problem"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by blackfly on 2008-02-02
Hi, I have an Atheros AR5212/5213 wireless card in my PCMCIA slot in my laptop, but I'm having problems.  I can connect fine, but after a few minutes it loses it.  I have to reconnect before I'm able to get online again.  

I checked online for some information on this and I read that it may have to do with the card constantly rescanning for networks using different channels because of confusion, and thus losing connection.  I have tried some different things online, but either they don't work or I wasn't doing the right thing (not really a Linux expert...)

Here is my lspci output (while kind of being online with Ubuntu 7.10):

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)




iwconfig output:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"BBUser"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:CE:17:F3:F5   
          Bit Rate:2 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=7/70  Signal level=-78 dBm  Noise level=-85 dBm
          Rx invalid nwid:101  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


When in Windows, I usually get about 1 out of 5 bars and the same is for Linux (although using two different wireless cards).  Because of that, I believe it to be the way that Linux handles my wireless card and not distance so much.

Any other commands I should do in the shell for you guys to check out?

Thanks for all of the help and sorry if it's been covered before, but the threads that I have seen were for different Atheros chipsets other than AR5212/5213.

---

### Post by ounas on 2008-02-03
Have you tried wicd, after removing network-manager


:popcorn:

---

### Post by psyburn on 2008-02-03
You signal quality is really poor

My Atheros 5212's (a mini-pci, and a PCMCIA adapter) prefer a link quality of 10/70 or better to keep a good link

You'll need to work on positioning to get less material between you and the AP

@ounas
Changing from network-manager to wicd won't really solve this one because the link will keep dropping out from time to time.

---

### Post by forceofnature on 2008-02-03
I am having trouble with my Atheros PCI card as well.  It dropped off when installing ubuntu studio packages.    Here is my message. 

-network:0 DISABLED    
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wifi0
       version: 01
       serial: 00:1b:2f:c0:d2:1f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11b


I reinstalled the network-manager but it did nothing.  Strange thing is when I go in and disable the roaming I can select active networks but still cannot enable the card.

---

### Post by forceofnature on 2008-02-03
Ok after rebooting my wireless connected back up.  I guess removing the network-manager and reinstalling it seems to work.  Weird.

---

### Post by blackfly on 2008-02-04
Thanks for the responses.

I'll try uninstalling and reinstalling networkmanager.  Any instructions handy?
If that doesn't work, than I'll try with a different wireless card or just try to get closer to it.  Too bad there's not some kind of Cantenna I could attach to this wireless card :P

---

### Post by blackfly on 2008-02-05
I'm not sure, but I don't think it's because of signal strength.  I read online that people have problems with it because it rescans again and again.  When I'm connected, it's as good as Windows, but just suddenly loses connection.

---

### Post by Cappy on 2008-03-08
Same problem. Using the restricted drivers.

Usually happens 30 seconds after
```

Mar  8 19:52:17 cappy-lappy dhclient: DHCPREQUEST on ath0 to 7.7.7.7 port 67
Mar  8 19:52:17 cappy-lappy dhclient: DHCPACK from 7.7.7.7
Mar  8 19:52:17 cappy-lappy dhclient: bound to 128.61.122.117 -- renewal in 806 seconds.

```

Also sometimes I get this message when it happens:
```

Mar  8 19:58:56 cappy-lappy avahi-daemon[5368]: Invalid response packet.
Mar  8 20:01:02 cappy-lappy avahi-daemon[5368]: Invalid legacy unicast query packet.
Mar  8 20:01:02 cappy-lappy last message repeated 5 times
Mar  8 20:01:03 cappy-lappy avahi-daemon[5368]: Recieved repsonse with invalid source port 61352 on interface 'ath0.0'
Mar  8 20:01:03 cappy-lappy avahi-daemon[5368]: Recieved repsonse with invalid source port 61353 on interface 'ath0.0'
Mar  8 20:01:04 cappy-lappy avahi-daemon[5368]: Recieved repsonse with invalid source port 61352 on interface 'ath0.0'
Mar  8 20:01:04 cappy-lappy avahi-daemon[5368]: Recieved repsonse with invalid source port 61353 on interface 'ath0.0'
Mar  8 20:01:06 cappy-lappy avahi-daemon[5368]: Recieved repsonse with invalid source port 61352 on interface 'ath0.0'
Mar  8 20:01:06 cappy-lappy avahi-daemon[5368]: Recieved repsonse with invalid source port 61353 on interface 'ath0.0'
Mar  8 20:01:10 cappy-lappy avahi-daemon[5368]: Recieved repsonse with invalid source port 61352 on interface 'ath0.0'
Mar  8 20:01:10 cappy-lappy avahi-daemon[5368]: Recieved repsonse with invalid source port 61353 on interface 'ath0.0'
Mar  8 20:01:18 cappy-lappy avahi-daemon[5368]: Recieved repsonse with invalid source port 61352 on interface 'ath0.0'
Mar  8 20:01:18 cappy-lappy avahi-daemon[5368]: Recieved repsonse with invalid source port 61353 on interface 'ath0.0'
```

---

### Post by Sunflower1970 on 2008-05-30
gah. I just wrote out a long question to this thread because I'm having the same thing happen to me and I lost it due to a connection drop...(grr)

So, I'll try again.
I'm having something similar happen. It just started in the last week after an update over the weekend. I've been trying to look for an answer all week. I'm on Hardy, and  using the D-Link WNA-2330 which uses the Atheros 5212/5213 chipset. I use MadWifi drivers. I really thought the card was going bad, or even my router. The router is fine, since this dropping of the network is  happening at a free wifi spot I'm at right now. (Guess it could be the card...but I'm not sure what to look for iff a PCMCIA card goes bad)

I use Wicd to connect, and NM is not installed on this computer any more. When the connection is dropped, I will open up wicd and it shows that I'm still connected with good signal strength, but there is no activity when trying to browse. If I lose connection too often, and use wicd  to reconnect, it will completely freeze. Once that happens and I kill the gui. I'm unable to use it again unless I reboot. 

One thing I did do that seemed to allow  the connection to stay up longer was to edit the /etc/modprobe.d/aliases file. I changed the line which said alias net-pf-10 ipv6 to alias net-pf-10 off ipv6.

If this is a scanning issue, is there a way to turn it off? 

Or, would a different card work, perhaps?

---

