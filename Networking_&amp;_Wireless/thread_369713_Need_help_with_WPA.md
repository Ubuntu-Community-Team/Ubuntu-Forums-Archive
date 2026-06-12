---
title: "Need help with WPA"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by tato97 on 2007-02-24
I'm a new Ubuntu/Linux user. I have therefore limited experience with the system but I've worked with computers for a long time. 

Today I installed Ubuntu 6.10 in my son's computer which I was about to discard because it runs so slow in Windows. I was impresed with how the system runs with Linux. However, I have reached a rough spot in the setup. I've been trying for over 7 hours straight to setup the wireless card/network. I have read all the help files and treads but have been unable to figure this out.

Once I do the changes to the interface file the computer locks up and it will not boot again into Ubuntu. 

Any help on this will be appreciated. 

Here are some screen shots that might help:

**This is the results of running iwconfig once the software is installed:**

*******leo@Chris-Desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"STAF50A1F"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=31/100  Signal level=4/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

**This is how I have edited the interfaces file several times...**

*******Edited /etc/network/interfaces file:

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid 19stumbler64
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 2846ec10d17b184d42634622e5171cfbb85bbe62afe468bf123fc1bdcd1edce8



************

**This is re-starting network after editing the interfaces file. Once this is run, the machine will lock up and it will not reboot back.**

leo@Chris-Desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4429
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:e0:98:f5:0a:1f
Sending on   LPF/wlan0/00:e0:98:f5:0a:1f
Sending on   Socket/fallback
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.

---

### Post by tgalati4 on 2007-02-24
What is the output of lspci?
Unfortunately, WPA can be tricky with some cards.  Have you tried WEP or open to see if basic wireless networking is OK.

Do you get a kernel panic or does the machine just freeze with mouse and keyboard lockup?  Run "top" in another console during this testing so that when the machine freezes at least you will have a snapshot of the processes that were running.

Post interesting output from dmesg and /var/log/messages
Also a brief description of the hardware:  processor, memory, and network card.

Do you have a normal (wired) network card to use in the meantime?

---

### Post by wieman01 on 2007-02-25
What card have you got? Perhaps the Windows driver that you are using does not support WPA2. A thought.

---

### Post by alexrudd on 2007-10-25
My wireless (using WPA) took some configuring with /etc/network/interfaces, but eventually I got it to work under Feisty.  After upgrading to Gutsy, however, I get the exact same problem as here.

No kernel panic, but the screen and mouse freeze.  My CAPS LOCK and SCROLL LOCK keys also start blinking.

When I restart the machine I'll post any interesting logs I can find, and the Wi-Fi configuration (It's a broadcom card, but I don't remember which method I used way back when)

---

### Post by sefs on 2007-10-25
slightly off-topic but ... 

wlan0 IEEE 802.11b+/g+ ESSID:"STAF50A1F" Nickname:"acx v0.3.21"

AND

wpa-ssid 19stumbler64


should the ssid not match there?

Also try removing this line "wpa-conf managed"  and try setting "wpa-ap-scan 2" to "wpa-ap-scan 1"

---

### Post by sefs on 2007-10-25
alexrudd  ... might you be using an rt73 based card and drivers? If so are you using WPA/WPA2

If so down grade to no security and wep respectively and see if you can connect without a lock up.

There seems to be a problem with gutsy+rt73+wpa/wpa2

---

### Post by alexrudd on 2007-10-26
Oops, I got my cards mixed up.  The problem computer is a Realtek.
"Realtek RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)"

Ndiswrapper (or "Windows Wireless Drivers" in the GUI) says I'm using "net8185", which I copied over from a Windows install.

I'm connecting to my university's network, so I can't change the security.   I deactivated NetworkManager, and (used to) connect by issuing "sudo /etc/init.d/networking/restart."  That's what freezes.  

Here is the relevant portion of my manually-configured /etc/network/interfaces.
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid Villanova
wpa-ap-scan 1
wpa-eap TTLS
wpa-anonymous-identity anonymous
wpa-key-mgmt IEEE8021X
wpa-phase2 auth=PAP
wpa-identity name
wpa-password password

---

### Post by alexrudd on 2007-10-31
Well, I uninstalled the Windows wireless driver, and it still locks up.  I'm fairly sure this means the problem is not with ndiswrapper, then.

This computer is now effectively useless; I should have stayed with Feisty. >_>

---

### Post by mattgaunt on 2007-10-31
Im havin the same symptons as alexrudd

I need my wireless for university work too but when i try to connect using WPA my computer freezes up and the caps lock and num lock lights blink

Im using a netgear PCMIA card - think its the MA5281 card (Something like that)

Matt

---

### Post by alexrudd on 2007-11-02
I've had a bit more time to waste on this, so I experimented a bit more.

Using an older kernel (2.6.20 something instead of 2.6.22) the lockup did not occur.  I had problems with nvidia graphics, and it didn't connect or anything, but at least it doesn't lock up.

Then I found [this post](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/108558), so I swapped out "wpa-driver wext" for "wpa-driver ndiswrapper" in /etc/network/interfaces as suggested and the lockup no longer occurs.  It still can't get a DHCPOFFER and gives the following error:
iotrl[SIOCSIWENCODEEXT]: Operation not supported

I'm thinking of editing that bug report.  However, "wext" doesn't seem to be an Ubuntu package.  Should I change it to wpa-supplicant?

---

