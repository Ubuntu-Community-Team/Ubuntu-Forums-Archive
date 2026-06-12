---
title: "BCM4306 chipset, D-Link Router will not network"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by ex_tour_director on 2006-12-27
I am trying to set up wireless connection (for my father) on an older Dell computer to a windows based wireless network.  The computer has Ubuntu 6.06 installed as the operating system.  It has a Belkin F5D7000 wireless card which uses the BCM4306 chipset.  The router I am trying to connect to is a D-Link DI-524 with the latest firmware installed.  I followed the various suggestions in the forums and used ndiswrapper and the bcmwl5.inf driver.  The network is set up on a newer Dell computer running Windows XP Media Center Edition.  I know that the network is set up correctly because a Dell laptop also running Window XP can connect to it.  I was also able to connect to it with my own laptop.
  
I was able to set up a similar wireless connection on an older Gateway running Ubuntu 6.06 using the same model number Belkin card connecting to a Belkin router.  The Gateway computer connected instantly to the Belkin network.  In fact the the Dell computer will connect to my Belkin network so I am pretty sure that I have the card set up and the drivers installed correctly.  But it will not connect to my father's D-Link network.

For some reason the wireless connection on my Gateway computer is named eth1 but the wireless connection on the Dell (that I cannot get to work with the D-Link router is called eth0.  I don't know if that means anything or not. 

The following is the output from the Dell computer when I tried to connect to the D-Link network.  The network I am trying to connect to is Cell 01 with an essid of “dlink”.  The other network listed is my network which is located next door and I can connect to it if the weather conditions are right.  But I did bring the computer over to my house to connect to my network so that I could update Ubuntu and the other programs previously.


bob@bob-desktop:~$ sudo iwlist eth0 scan
eth0      Scan completed :
          Cell 01 - Address: 00:15:E9:1B:02:BA
                    ESSID:"dlink"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:0/100  Signal level:-31 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:11:50:1B:0F:29
                    ESSID:"al1"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:0/100  Signal level:-70 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

bob@bob-desktop:~$ sudo iwconfig eth0 essid dlink
bob@bob-desktop:~$ sudo iwconfig eth0 key XX-XX-XX-XX-XX
bob@bob-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:11:50:18:f5:a3
Sending on   LPF/eth0/00:11:50:18:f5:a3
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
Trying recorded lease 192.168.2.7
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
 
I am very new to Ubuntu and do not know how to do very many things so if you are able to help me please give specific and complete instructions.  Thank you.

---

### Post by dbott67 on 2006-12-27
I would recommend trying to simplify the situation:

1.  Turn off encryption & try connecting.
2.  If it works, re-enable WEP and use a simple ASCII password.
3.  Try connecting again, if it still works, try a more sophisticated password.

To use an ASCII WEP key instead of HEX, place an s: in front of the key.  If you router that only uses HEX keys, you can convert them here: [http://www.dolcevie.com/js/converter.html](http://www.dolcevie.com/js/converter.html)

```
dbott@dapper:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key **[COLOR="Red"]s:[/COLOR]**mysecretwepkey
```

-Dave

---

### Post by ex_tour_director on 2006-12-28
Dave:
I disabled the WEP at the router.  I am still unable to connect.  I get the exact same output as I did previously.  I restarted the computer hoping that would help.  But it did not seem to do any good.  I did notice that after I turned the computer back on the Channel which I had previously set as Chennel 5 using sudo iwconfig eth0 channel 5 reverted back to Channel 11.  I don't know if this tells you anything. Do you have any other thoughts or suggestions?
Thank you for your help.
Al

---

### Post by dbott67 on 2006-12-28
On my laptop I had a heck of a time getting ndiswrapper working.  I eventually had to resort to compiling ndiswrapper from source:

1. Remove any existing versions of ndiswrapper.

2. Install **build-essential** from Synaptic (for compiling ndiswrapper)

3. Download latest stable version of **ndiswrapper** from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

4. Compile **ndiswrapper** according to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

5. Be sure to use the listed driver for your card: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

[COLOR="Red"]Note: any kernel updates will require that ndiswrapper be recompiled[/COLOR]

-Dave

---

### Post by ex_tour_director on 2007-01-01
Dave:
Sorry that I have not responded sooner but I had my foot operated on and am now just getting back to my computer.
I thought that it would be a good idea to begin with a clean install which I just did.
I want to try what you suggested. However, I am so uninformed about how to do things in ubuntu that I do not even know how to remove any other versions of ndiswrapper.  I thought that I just had to go to synaptic package manager and mark it for removal  but it did not come up there so I guess that is wrong.
Would you please tell me how to remove the version of ndiswrapper that is installed on the computer to get me started?  I am sure that I will have lots of other questions as I go so please be patient with me.
Thank you,
Al

---

