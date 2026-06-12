---
title: "wifi with ndiswrapper:  &quot;Error for wireless request&quot;"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by ferdinando_villa on 2008-04-29
I am running Ubuntu 8.04 64 on my laptop, fresh install, and i am having a lot of trouble configuring the wifi... i've installed ndiswrapper and the appropriate windows driver, and now I can see my network in Network manager, but iwconfig returns

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So, looking at ndiswrapper troubleshooting, it tells me i need to run "wconfig wlan0 essid (my essid here)", but when I type it in a terminal (even in root), i get

Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.

I am going crazy here, any ideas of what to do?
Thank you

---

### Post by chili555 on 2008-04-29
Maybe the Super User is permitted to do this operation. Please try:```
sudo iwconfig wlan0 essid ur_lil_router
```You say you tried as root; how did you do this? Perhaps there is some error there.

---

### Post by ferdinando_villa on 2008-04-29
Yes, i've tried just that... but nothing happens, no messages appear, and i just get a prompt again. But if i run iwconfig then, it returns the same result, access point not associated...

Any ideas of what might be happening?
Thank you

---

### Post by Ayuthia on 2008-04-29
It might be that you don't have all the conflicting drivers blacklisted.  Can you post your lspci -nn or lsusb (if it is a USB wireless device)?

---

### Post by ferdinando_villa on 2008-04-29
~$ lspci -nn

00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:12.0 IDE interface [0101]: ATI Technologies Inc IXP SB400 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975]
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
06:04.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530] (rev 01)
06:04.2 SD Host controller [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (rev 01)
06:04.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520] (rev 01)
06:04.4 FLASH memory [0501]: ENE Technology Inc SD/MMC Card Reader Controller [1524:0551] (rev 01)

---

### Post by Ayuthia on 2008-04-29
You might check out this link:
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

It looks like you might need to blacklist ath_pci.  I could be wrong though.

---

### Post by chili555 on 2008-04-29
> Any ideas of what might be happening?I think your card wants three things, the ESSID, any encryption details and a request for an IP address. Please try:```
sudo iwconfig wlan0 essid your_router
sudo iwconfig wlan0 key 98765xyzetc.
sudo dhclient wlan0
```This encryption example is appropriate for WEP only. Let us know.

---

### Post by ferdinando_villa on 2008-04-29
Yes, but the problem is that those commands are not doing anything...

Well, i've noticed something that might be wrong in the ndiswrapper official site. When i run ndiswrapper -l, i get

net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

This is the correct driver for my card, but the site says that the presence of the "altarnate driver" is bad, and that i must unload it with rmmod

When i run rmmod ath_pci , i get

ERROR: Module ath_pci does not exist in /proc/modules
(and in fact, that is just an empty text file)

Blacklist ath_pci is confirmed, though, being present in /etc/modprobe.d/blacklist

So why is being loaded, as ndiswrapper-l tells me? and why can't i unload it with rmmod?

---

### Post by Ayuthia on 2008-04-29
> **ferdinando_villa said:**
> Yes, but the problem is that those commands are not doing anything...

Well, i've noticed something that might be wrong in the ndiswrapper official site. When i run ndiswrapper -l, i get

net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

This is the correct driver for my card, but the site says that the presence of the "altarnate driver" is bad, and that i must unload it with rmmod

When i run rmmod ath_pci , i get

ERROR: Module ath_pci does not exist in /proc/modules
(and in fact, that is just an empty text file)

Blacklist ath_pci is confirmed, though, being present in /etc/modprobe.d/blacklist

So why is being loaded, as ndiswrapper-l tells me? and why can't i unload it with rmmod?

That can sometimes happen.  I have a Broadcom card and mine shows the alternate driver also but it works fine when I use NDISwrapper.  It might be possible that the driver that you have might not be the right driver.  Can you post your sudo lshw -C network?  This might help to see if there is a conflict.

---

### Post by ferdinando_villa on 2008-04-29
lshw -C network

*-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:15:7a:4d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,07/26/2007,5.3.0.67 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:cd:e6:41
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth1
       serial: 00:07:cb:00:00:ff
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=192.168.0.12 link=yes multicast=yes

---

### Post by chili555 on 2008-04-29
> Yes, but the problem is that those commands are not doing anything...
When you issue a command and the cursor just pops back, it means the command was accepted without complaint. That's good. But you really don't mean the command:```
sudo dhclient wlan0
```did nothing. Say it isn't so.

Your *iwconfig* is not going to show your ESSID and encryption details until you connect. The *dhclient* command is the request to connect.

Please issue all of the commands in order and let us know. Amend the *key *command as needed to agree with your encryption system.

---

### Post by ferdinando_villa on 2008-04-29
You're right, now I am getting somewhere! I've ran the commands, and sudo dhclient wlan0 gave me:

There is already a pid file /var/run/dhclient.pid with pid 7085
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:19:7e:15:7a:4d
Sending on   LPF/wlan0/00:19:7e:15:7a:4d
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

But i guess the problem is with the second command, 'key'... you've said, 

"Amend the key command as needed to agree with your encryption system"

How do i find out about that? I am sorry to ask all this dumb questions, but I guess why i switched to Linux was to learn all the stuff that I just did automatically in windows before...

So before all i needed to connect to my wireless network was my WAP password, so how do i configure the iwconfig wlan0 key command?

Thank you very much for all the patience in dealing with newbies like me! :)

---

### Post by chili555 on 2008-04-29
Indeed you are getting there. Based on what I see, I don't think anything needs changing in your ndiswrapper install. You've done well!> I am sorry to ask all this XcensoredX questions, but I guess why i switched to Linux was to learn all the stuff that I just did automatically in windows before...A very good reason to do it. Another is to realize you don't have to robotically do things the way Windows dictates, You can amend your configuration files and do what you please, even it it's wrong! You can experiment. You can, after you make a back-up, learn by trial and error. You can extend your understanding of what computers do and why. You can install a goofy theme, move your taskbar to the left side, instead of top or bottom; in short, you can make your computer yours and yours alone. You can politely ask Chili to calm down and take a deep breath.

There are two main types of encryption, WEP and WPA. They, in turn, have their own variants. WPA2, Leap, etc., etc. Each must be set up correctly in your computer for your router to say, 'OK, you know the secret code, here is an IP address. Now go get those torrents!' Do you know if you have encryption in place? Here is one thing that will help us; let's ask the router.```
sudo iwlist wlan0 scan
```This may take two or three tries. You may get something like:```
eth1      Scan completed :
          Cell 01 - Address: 88:0C:41:19:58:77
                    ESSID:"GBR009"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=80/100  Signal level=-54 dBm  Noise level=-91 dBm
                    **Encryption key:on**
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000016f950caefd
```See, it says it has encryption turned on and by implication, if you don't know it, please go away.

Did you set up WEP or WPA in your router? If not, skip the *key* command altogether. If so, tell us what kind.

---

### Post by ferdinando_villa on 2008-04-29
Yes, that was precisely the arguments that made me come to Linux, and one other reason is community support, it is really amazing. I hope i can also be of help once I get more used to the way the OS works.

And yes, i have encryption on... and (i think, since i've moved not too long ago and it was already set up) encription is WPA, TKIP... was that your question, or by 'type of encryption' you mean something else I am not aware?

---

### Post by chili555 on 2008-04-29
This guy is the king of WPA: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)  and, modestly, I am the king of WEP: [http://ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep](http://ubuntuforums.org/showthread.php?t=172810&page=2&highlight=wep)

---

### Post by ferdinando_villa on 2008-04-29
Here are the specifications i got from iwlist wlan0 scan, pertaining to my network:

          Cell 10 - Address: 6E:A3:3B:2C:8D:7C
                    ESSID:"freebox_hs"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

---

### Post by ferdinando_villa on 2008-04-29
...and duh!, it is obviously, WPA1(TKIP)

---

### Post by chili555 on 2008-04-29
> encription is WPA, TKIP... was that your questionExactly so! You probably need to get the details from the administration page of your router, passwords, etc. and then see the WPA post I referred to above.> it is obviously, WPA1(TKIP)Yessir! When you get the passwords, codes, etc. in place, you should connect.

Good luck. You are doing well, so far! Actually, you have made a great deal of progress in the last hour or so!!!

---

### Post by ferdinando_villa on 2008-04-29
Ok, I can feel it is almost in place!
It still needs a touch or two, probably on the ip, gateway, and things like that, which i need to figure out, but it's almost there!

I will try it more carefully soon, and i'll get back to you.

Thank you so much for all the help and patience, it's been really helpful!

---

