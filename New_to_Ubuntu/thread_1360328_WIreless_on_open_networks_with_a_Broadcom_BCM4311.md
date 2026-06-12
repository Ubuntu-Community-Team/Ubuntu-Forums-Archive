---
title: "WIreless on open networks with a Broadcom BCM4311?"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by Robthxbrosti on 2009-12-20
This forum is so big I get lost. The issue is having installed ubuntu 8.04 I can"t get connected wireless to the net. Reading the pocket guide from Keir Thomas it looked not that difficult but... Additionally some reading on [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
And no straight forward explanations found on the forum.
So all help is welcome since I hope to get this Acer aspire5310 wireless on the net for my wife's christmas, since raising two kids and studying midwivery she deserves maximal mobility

These things I've found out by 
putting in the commandline
lspci -v | less
My wirelass card is:
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0422
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at d0100000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

I performed 
sudo apt-get install linux-backports-modules-hardy
which gave no error messages but from the network manager(the icon in upper right corner) still no wireless networks are seen. In window$
(Vista on this Acer, XP on my company's dell) about 4 to 5 networks, with 2 of them unsecured (also mine is unprotected (:( once the card is up I'll hope to find out how to secure it) are detected.

Since no response, I installed the firmware driver B43 that was suggested in the task menu but still dead. I assured myself that I've the card turned on but the light on the top left of my keyboard (acers users - pls check if this is the right place to look since acer is new to me)

Then while typing this thread I clicked further on the previuosly mentioned site, finding out that the card is supported and that it should work by the firmware driver. There is also ndiswrapper to get it working but that seemed a bridge to far for me being noob. Then there was even a method mentioned to work out of the box - something called WL restricted. 

Following the mentioned links i finally got to a place to download a tarball. But that is also completely new. The readme txt was not instructive enough so I didn't dare to start on that tarball thing. 

So
-Which commandlines can I run to see my WLAN card is running?
-Which method is preferred for getting the card running (see my try outs)? (If the tar-thing is (WL restricted) is, pls point give me some clearification on how i should that tarball unwrapped (???) 
-How to connect to open networks (like mine at home, but also like libraries, university, ...) - maybe out of the box when the card is running...

I hope I made clear i did inform myself and tried several things but I really don't want to put another 8 hours in to it...

Have nice holidays and merry christmess

---

### Post by sandyd on 2009-12-20
either install *bcm43xx*-[I]fwcutter
or compile the linux broadcom STA drivers
their avalible in the hardware drviers thingy. (not sure for 8.04 tho)
[/I]

---

### Post by Robthxbrosti on 2009-12-21
Thx for the reply however I saw this cutter-thing passing by when i installed the firmware.

So i think it is on my HD.
i ve run ifconfig, and iwconfig but since my wife is using the wired network i post this from my office wireless connected windows PC and I was not able to interchange the file (off course,, if necessary, I post it later on.

I guess he card is detected since now there is nw text appering in the networkmanager mentioning "connect wireless networks". 

Somehow i got the Wireless connection in the "network settings"set on Roaming mode, whatto e seems exactly the mode i was looking for.
I've chosen "connect to other", typed the name as it is displayed in Vista and a barchart poppud up indicating connection was 0% 

So questions from my original post keep standing. I have one more:
 * how do I startup the wireless card when booting? 
now i'm pressing the button that i think is the activation but it seems to be a buggy key. Sometimes the LEDlight goes on immediately ,othertimes after only 6 attempts.

I hope some answers or link to one will be posted because if this takes too long I'll remember long time it gave me hardtimes setting it up.

---

### Post by Robthxbrosti on 2009-12-22
reading [http://ubuntuforums.org/showthread.php?p=6183681]("http://ubuntuforums.org/showthread.php?p=6183681") and this [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#steps]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#steps") i think i can say my driver of the wlan card is OK. But still; when I started, suddenly the available networks popped up in networkmanager. But I couldn't connect to my network. It kept on searching and came up with nothing. Troubleshooting this these networks disappeared and I was not able to get them back. Here below I've pasted the information from the common troubleshoot commands. 
I also got a message in the network tools saying "the interface does not exist" when I tried to configure. Might there be something wrong with my interfaces?? How to check?
I hope somebody recognizes my issue and comes with that golden command line fixing it. 

[SIZE="1"]$ lspci | grep Network
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:26:d8:90
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.22 latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:26:26:29:cf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

$ dmesg | grep wlan0
[   46.484470] ADDRCONF(NETDEV_UP): wlan0: link is not ready

$ iwlist wlan0 scanning
wlan0     No scan results

$ lsb_release -d
Description:	Ubuntu 8.04.3 LTS

~$ uname -mr
2.6.24-26-generic i686

$ sudo /etc/init.d/networking restart
[sudo] password for vinnie: 
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:8: option with empty value
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:8: option with empty value
ifup: couldn't read interfaces file "/etc/network/interfaces"

$ ping -n 4.2.2.2 -c 4
connect: Network is unreachable

$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1c:26:26:29:cf
Sending on   LPF/wlan0/00:1c:26:26:29:cf
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

**Edit made by s.fox on behalf of Robthxbrosti**

Hi all,

Restarting Evolution after applying changes did the trick!

After trying a dozen of the suggestions on getting email sent by gmail/hotmail via Evolution (all possible combinations) I left it on the suggestion with the 587 as port and TLS as encryption on the hotmail account. I closed Evolution and restarted Evolution and. Finally the messages in the outbox left it. Nevertheless the emails sent via the gmail account were stuck in the outbox. I changed the settings as wel for the gmail account, but no succes after clicking apply. But then again, leaving the settings like that, closing and reopening Evolution did the trick. The Evolution version on my machine is 3.2.3.
I wanted to add this to the thread but since it was closed I decided to email to you guys. Might save another person his Saturday afternoon ;)

Thanks a lot for making the Ubuntu experience work.

KR,
Rob

---

