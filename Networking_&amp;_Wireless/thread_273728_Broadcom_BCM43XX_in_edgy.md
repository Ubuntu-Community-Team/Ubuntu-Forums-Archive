---
title: "Broadcom BCM43XX in edgy"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by devoncatt on 2006-10-08
I followed all the instructions and actually got my Belkin to work and actually got a DHCP IP address from my Linksys router.

 I then tried to change the ip address to static and now it won't work even if I go back to dhcp?? 

I have had problems getting the networking to work with a static address with my wired ethernet as well. I tired this with an open (no WEP key) and had the same problem

I have entered the wep key. I tried all 4 wep keys and networking can't read the interfaces file.

It's suppossed to work with 2.6.17+

Any suggestions ????

Devoncatt 

Generic Desktop   1.8 P4 512 MB Ram PCI Belkin wireless Updated edgy release (same problem other Ubuntu releases and SUSE)

dmesg gives:
[17179595.184000] bcm43xx: TODO: Incomplete code in keymac_write() at drivers/net/wireless/bcm43xx/bcm43xx_main.c:1132

lspci gives
02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)


/etc/network/interfaces

iface eth1 inet dhcp
wireless-essid dcatt
wireless-key ********* not displayed by  me here 


iwconfig gives:

eth1      IEEE 802.11b/g  ESSID:"dcatt"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.442 GHz  Access Point:              00:13:10:12:1F:E1
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=90/100  Signal level=-38 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:8008  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




when I try to restart the network I get Listening on 

LPF/eth1/00:30:bd:92:a7:4b
Sending on   LPF/eth1/00:30:bd:92:a7:4b
Sending on   Socket/fallback
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.






Kernel 2.6.17-10-386


$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:13:10:12:1F:E1
                    ESSID:"dcatt"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:7
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-28 dBm
                    Extra: Last beacon: 96ms ago
The BCM43XX software is in /lib/firmware

$ ls  /lib/firmware
  bcm43xx.cat           bcm43xx_initval04.fw  bcm43xx_initval08.fw   bcm43xx_microcode4.fw  bcmwl5a.inf
bcm43xx_initval01.fw  bcm43xx_initval05.fw  bcm43xx_initval09.fw   bcm43xx_microcode5.fw  bcmwl5.inf
bcm43xx_initval02.fw  bcm43xx_initval06.fw  bcm43xx_initval10.fw   bcm43xx_pcm4.fw        bcmwl5.sys
bcm43xxa.cat   bcm43xx_initval03.fw  bcm43xx_initval07.fw  bcm43xx_microcode2.fw  bcm43xx_pcm5.fw

---

### Post by kngcrntrd on 2006-10-08
I have only one problem with bcm43xx.  On my home network, no problems.  However, when wardriving, I pick up nothing.  I'm pretty sure it has something to do with changing the 'RadioState' setting, but I can't find the files to change.  I have used Ndiswrapper in the past (i.e. other releases...Breezy, Dapper, etc...)  without this problem.  Then again, I was changing the RadioState from 1 to 0 (or vice versa, I can't remember).  Thanks in advance!

P.S. - I'm using Airsnort to scan for wireless networks.

---

### Post by fuoco on 2006-10-27
I upgraded to edgy and bcm43xx stopped connecting to my AP. It worked with dapper, anyone knows what could be the problem ?

---

### Post by vfm on 2006-10-28
I got exactly the same problem...does anyone knows how to fixe this?

---

### Post by andrinho on 2006-10-28
Hi there!

I'm new to this forum and have the same problems. I installed Kubuntu edgy on my HP nx6125 and can't get my wlan working. Looking  at the poll above, there must be someone who got it working and doesn't have problems without NDIS.

I haven't tried NDISwrapper yet 'cause I thought the bvm43xx is supposed to be working with the 2.6.17 kernel.

So if this person could tell us how he/she got it working without NDIS, that'd be great!

If anybody has another suggestion I would be happy!

Thanks a lot!
andrinho

---

### Post by markkun on 2006-10-28
I have an old Thinkpad 600E with Asus WL-103B that includes 4301 chip. I tried to update my xubuntu from dapper to edgy, but it didn't go well at all so I needed to install it fresh. This is what I did to get the WLAN working.

enabled the Universe repository
sudo apt-get install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh

And that's all... then it works like a charm :)

(Thanks to the one who wrote this: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper))

---

### Post by trubblemaker on 2006-10-28
I know the upgrade to dapper 'caused issues as ndiswrapper and the native driver both dried to access the same piece of hardware.

BE AWARE if you had NDISWRAPPER before in DAPPER, and upgraded you will have driver issues, the proper way to fix it is to blacklist one of the drivers, by adding "ndiswrapper" or "bcm43xx" in ```
/etc/modules.d/blacklist
```
I installed ndis from source and could connect fine. but then on reboot I ran into issues at school.  I get an ip address and can see networks, but can't connect to the net.  I think it's got something to do with the IP6 routing in edgy.  
When I installed dapper I ran into a similar issue, turned off IP6v and the issue went away. same issue is coming up again and the same old tricks aren't working.  For the people that this isn't working for are you getting an ip address at all? Can you see the networks?

---

### Post by Jbweld on 2006-12-06
IN TERMINAL Program...
sudo apt-get install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
sudo apt-get install network-manager
sudo apt-get install network-manager-gnome
sudo apt-get
sudo apt-get install wpasupplicant
--------------------------------------------------------------------------
sudo gedit /etc/network/interfaces
# Comment out everything other than “lo” entries in that file and save the file 
USE # to comment out!
((Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file
Sudo Gedit /etc/default wpasupplicant))) add ENABLE=0 into it and save file.
-----------------------------------------------------------------------------
sudo touch /etc/default/wpasupplicant
YEAH RE_Boot
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
Then set it all up with wpa/network names etc..and your done.

---

### Post by trubblemaker on 2006-12-06
Jbweld I know that your excited, but please don't post that your howto on each forum that you see, it would be great if you would add it to the broadcom wiki: see my signature for a link to it.

---

