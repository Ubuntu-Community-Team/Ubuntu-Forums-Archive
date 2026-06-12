---
title: "Problem with my Acer laptop"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by retghy on 2007-08-11
Hello all. My first post here, after hours of reading and trying almost everything i saw in the forums I have no option but to make a new post :).

Ok. I have an Adsl Modem router connected to a Switch, 1 PC running XP connected to the switch to get access to the internet, this PC also has a wireless adapter which I use to share Internet to my Laptop using a network bridge (wired adapter and wireless adapter).

Until 2 days ago my Acer laptop was running WinXP also and I just click on found wireless networks and automatically conect to my PC and gain internet wireless access.

Now I decided to migrate to Ubuntu (only on my laptop first), installed the wireless adapter using the bcm43xx-gtk-installer-0.2.1.tar.gz found on this forum also (It is a Broadcom4306), and everything seems to work fine wile working with the wired network, but I just cannot access trough the wireless adapter now, although it detects a wireless network available (the pc running XP), it won't connect.

It doesn't even ping either the pc or the router.

I tried deleting the network bridge in my PC to check if i was able to ping the laptop, and in fact i was, seems like my laptop wont detect or wont work trough the network bridge.

So what can I do here?

I dont want to go back to Windows on my laptop, and I dont have money to buy an Access Point.

I think that if it was possible on XP It gotta be more than possible on Linux.

Here is a simple diagram of my network:
[img]http://img234.imageshack.us/img234/6430/redvs1.jpg[/img]

Also a screenshot of the network bridge: 
[img]http://img111.imageshack.us/img111/5995/bridgeee4.jpg[/img]

Thank in advance and excuse my lame english, I hope I was able to explain myself as i wanted to.

---

### Post by retghy on 2007-08-11
Anyone please?

I don't want to get back to Windows just because of  this :(

---

### Post by retghy on 2007-08-11
Here are my reports, I hope it helps:

lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge [1106:3205]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8235 PCI Bridge [1106:b168]
00:07.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
00:08.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] [1002:5c61] (rev 01)


sudo lshw -C network
 *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth1
       version: 03
       serial: 00:0b:6b:48:87:c7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic ip=192.168.0.100 latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:d0004000-d0005fff irq:11
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 74
       serial: 00:c0:9f:34:3b:2d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=half latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: ioport:1800-18ff iomemory:d0006c00-d0006cff irq:4

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Dragos"  Nickname:"Dragos"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 82:C1:AF:D3:F0:D0   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: C6:CE:CF:5F:D2:F2
                    ESSID:"Dragos"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=97/100  Signal level=-42 dBm  Noise level=-67 dBm
                    Extra: Last beacon: 84ms ago

---

### Post by retghy on 2007-08-11
bump :(

---

### Post by retghy on 2007-08-12
What do I have to do to get an answer here?

I see every one else get at least ideas/advices for their problems :(

Didn't I explain myself well? If you can't understand my problem I can try to explain better.

Thanks in advance.

---

### Post by retghy on 2007-08-14
Last Bump

---

### Post by ugm6hr on 2007-08-14
I don't know what's up - but the difficulty is potentially 2 problems:
The BCM4306 card or the internet connection sharing.
[I]
iwlist scan[/I] shows the wifi card is scanning OK, and detecting your SSID.  But it doesn't seem to be connected.

If XP managed to connect - then presumably the internet sharing issue was working OK.  Which means it must be the Broadcom?

I'm afraid I don't have that wifi card, so I'm not sure that I can help.

Some other information that might be helpful (for someone else to help you):
What security do you use (Open/WEP/WPA)?
Have you managed to connect to any wifi access points?

---

### Post by retghy on 2007-08-14
> **ugm6hr said:**
> I don't know what's up - but the difficulty is potentially 2 problems:
The BCM4306 card or the internet connection sharing.
[I]
iwlist scan[/I] shows the wifi card is scanning OK, and detecting your SSID.  But it doesn't seem to be connected.

If XP managed to connect - then presumably the internet sharing issue was working OK.  Which means it must be the Broadcom?

I'm afraid I don't have that wifi card, so I'm not sure that I can help.

Some other information that might be helpful (for someone else to help you):
What security do you use (Open/WEP/WPA)?
Have you managed to connect to any wifi access points?

Thanks for taking the time to reply.

With both computers running XP everything works OK, internet sharing, file sharing, printer sharing everything.

Now when using ubuntu, Wireless adapter seems installed and working, but I cannot by any manner to connect to my PC with windows XP and network bridge.

As i mentioned above, i tryed everything and even deleted the network bridge in XP leaving the wireless conections alone and I was then able to connect from ubuntu and even ping the XP machine.

But of course leaving the wireless adapter out of the bridge in XP causes no shared internet trough wireless and that is precisely what I need, internet.

I tryed every possible security config,WEP and even Open without any kind of key, but nothing seemed to work.

I dont know anyone that owns an Access Point to test that out, I believe that should work, sadly I cannot afford an AP so instead I use winXP as one, to share internet wireless in my house to the laptop.

Thanks in advance.

---

### Post by ugm6hr on 2007-08-15
I think I misunderstood.  It sounds like you were able to ping from Ubuntu to Gateway (XP), so the wifi clearly works on Ubuntu.

It is an issue with the network settings.  I suspect what is important is that you just need to set the Gateway (XP) IP address as the gateway.  If you connect with Network Manager, I can't remember if that's possible.  Might be worth uninstalling NM, and installing Wicd (see my signature link).

I'm afraid I have no experience with this kind of setup - but if that doesn't work, some of these might have the right information for you:
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)
[http://wikisos.org/wiki/Ubuntu_7.04:How_to_setup_Internet_connection_sharing](http://wikisos.org/wiki/Ubuntu_7.04:How_to_setup_Internet_connection_sharing)
[http://ubuntuforums.org/showthread.php?t=73406](http://ubuntuforums.org/showthread.php?t=73406)
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by retghy on 2007-08-15
Hello **ugm6hr**, thanks again for your reply (the only one i got so far btw) :-S.

In fact, the wireless adapter is working, as I mentioned when I deleted the network bridge in Windows XP Ubuntu seems to detect the PC wireless adapter and even able to ping, but, I'm guessing it is some kind of bug or something that blocks the signal when the network bridge is enable.

The only rol that the windowsXP machine is playing here is to let the laptop comunicate with modem/router in a wireless way, through the use of a network bridge.

Thinking it might be the network manager I tried installing "Wi-Fi Radar", and in fact I like it most than NM, but the problem persisted, Thinking of a missconfiguration in the windows machine is hard because it is a simple network bridge between 2 adapters.

I will install WICD and see what happens.

BTW, If I configure the laptop to see the winxp machine as Gateway, I dont think it will be able to get internet, because the internet gateway is the modem/router (a different IP).

Again, I apreciate your replys.

---

### Post by ugm6hr on 2007-08-15
> **retghy said:**
> BTW, If I configure the laptop to see the winxp machine as Gateway, I dont think it will be able to get internet, because the internet gateway is the modem/router (a different IP).


I am not sure, since I have never had to do this myself.  But I think as far as the laptop is concerned, the Gateway is the XP Desktop.  Can't do any harm to try....

One other thing comes to mind - the Ubuntu firewall.  It might be worth installing Firestarter (from Synaptic) - you will have to use a "download script" to work out where to get the files from on the XP Desktop, then transfer them with USB to laptop (see post #5 and #6 here: [http://ubuntuforums.org/showthread.php?t=512364](http://ubuntuforums.org/showthread.php?t=512364)).  Then run Firestarter (once installed on Ubuntu), and disable the firewall.  Then see what happens.  If it works - then it will just be a case of editing the firewall settings to get it to work (or, if you have faith in your XP firewall - leaving the Ubuntu firewall open).

The only other thing that might be helpful is to know what the settings to get it to work with XP on the laptop were.  Obviously, XP sets its defaults to work with itself...

---

### Post by retghy on 2007-08-15
I finally managed to make it work, I believe it was a problem with drivers, even though it seemed installed ok.

I switched from fwcutter to ndiswrapper and now it works.

Thanks for your replys.

---

### Post by ugm6hr on 2007-08-16
> **retghy said:**
> I finally managed to make it work, I believe it was a problem with drivers, even though it seemed installed ok.

I switched from fwcutter to ndiswrapper and now it works.

Thanks for your replys.

Glad you got it to work.... Very bizarre...  But I suppose it doesn't matter if it now works :)

---

