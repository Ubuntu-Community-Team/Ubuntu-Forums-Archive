---
title: "LAN and Wireless problems"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by Porta-Chaves on 2007-03-19
I don´t know exactly whats going on, when i connect to the internet trough LAN i can access my router, but if i try to open a page it won´t open. However if i search a page trough the search function in the upper right corner i can open google but still i can´t access any site. There was also one ocasion where i somehow entered ubuntu.com

I´m also having problems recognizing my wireless card. 

(its a Ntech LAN108PCMCIA

0000:30:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11 abg NIC (rev 01)
Subsystems: Global Sun Technology Inc: Unknown device 7103
Fags: bus masters, medium devsel, lantency 168, IRQ 177
Memory at 34000000 (32-bit non-prefetchable) [size=64k]
Capabilities: <available only to root>

)
if anyone could get me a driver for it or sumthing like that...

i would apreciate if anyone could help me.

:)

---

### Post by dmizer on 2007-03-19
try adding:
```
blacklist ipv6
```
to the end of this file:
/etc/modprobe.d/blacklist

reboot, and you should be able to browse via your lan access.  don't know what to tell you about wireless, but there's tons of information on it.  you have an atheros chipset, so you'll probably be able to find native drivers for it.  do a google on: **atheros ar5212**

---

### Post by Porta-Chaves on 2007-03-20
i'll try that, but for the wireless card, how do i install driver for it?

---

### Post by Porta-Chaves on 2007-03-20
i just checked [http://madwifi.org/](http://madwifi.org/) and according to their list my chipset is supported but at the download page (wiki/UserDocs/GettingMadwifi) i can't find ubuntu or anything related to it

---

### Post by chili555 on 2007-03-20
The drivers are found in the package 'linux-restricted-modules' which you can find in the synaptic package manager. Be sure to install the module that matches your kernel, which you can find with:```
uname -r
```

---

### Post by Porta-Chaves on 2007-03-20
i tried inserting blacklist ipv6 to the file you indicated but it says i don't have the privileges to write there.

Also, i went to the synaptic package manager and the linux restricted module with my kernel (2.6.15-26.386) is already installed.

---

### Post by chili555 on 2007-03-20
sudo gedit /etc/modprobe.d/blacklist. At the end of the file, add:```
blacklist ipv6
```Reboot and post back to let us know.

---

### Post by Porta-Chaves on 2007-03-20
ok lan is working fine now :D ty, but my wireless still doesn't work, i tried reinstalling the synaptic module but it failed saying that it didnt exist

---

### Post by chili555 on 2007-03-20
I am afraid I may be a bit confused. > my wireless card.(its a Ntech LAN108PCMCIAHow is it you have a PCMCIA card in a conventional motherboard. Can you tell us more? Is it one of those PCI to PCMCIA adapters? Say it isn't so.

Also, please let me see: ```
lsmod | grep ath
```Thanks.

---

### Post by Porta-Chaves on 2007-03-20
It's just one of those wireless PCMCIA cards as seen here:

[http://www.fastshop.com.br/imgprod/SE220000324791_P.JPG](http://www.fastshop.com.br/imgprod/SE220000324791_P.JPG)


and for the information that you requested i will post it as soon as possible

---

### Post by Porta-Chaves on 2007-03-26
sorry for my late post chili555.

as for the info you requested, here is what i got:

```

cristiano@cristiano:~$ lsmod | grep ath
ath_pci                80540  0
ath_rate_sample        17160  1 ath_pci
wlan                  144924  3 ath_pci,ath_rate_sample
ath_hal               148816  3 ath_pci,ath_rate_sample

```


By the way I see people talking about ndiswrapper and MadWiFi and i wanted to know if that can be usefull to me in anyway...

thnx

---

### Post by chili555 on 2007-03-26
Looks like the drivers for your card are loaded just fine. Does:```
sudo iwconfig
```tell us anything? If it shows a wireless interface, ath0, perhaps, let's see if:```
sudo iwlist ath0 scan
```shows us anything. Substitute the interface you found if it's not ath0. We're making good progress.

---

### Post by Porta-Chaves on 2007-03-26
Glad to hear that... here is the info you requested:

```

cristiano@cristiano:~$ sudo iwconfig

Password:

lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:"Private CCS"
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

cristiano@cristiano:~$ sudo iwlist ath0 scan
ath0      No scan results


```

---

### Post by chili555 on 2007-03-26
Excellent! Your card is there! It's waiting for your command to associate with an access point.

What I was hoping we would find with scan is the ESSID and the MAC address of the access point as well as to confirm no encryption is in place. Here is my scan result with some details changed. I have highlighten the items we need from your access point:```
wlan0     Scan completed :
          Cell 01 - Address: **99:13:19:62:8D:F7**
                    ESSID:"**myrouter1**"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1

```In my own siuation, I have had no scan results and a few minutes later, I got a good result. Please try again, 10 or 15 minutes apart and see if we can get these details.

With this information we can confirm the ESSID is correct and include the MAC address in our request to ath0 to connect.

Incidently, a lot of people have difficulty connecting to an ESSID with a space in the name, in your case "Private CCS." It may never connect, but might connect to "PrivateCSS."

Whe we get ready to connect, we will need to disconnect the ethernet cable, so as not to try to get two different IP addresses with two different interfaces. It seldom works and often doesn't.

---

### Post by Porta-Chaves on 2007-03-27
i tried it 3 times in a row and got results:

```

cristiano@cristiano:~$ sudo iwlist ath0 scan
Password:
ath0      No scan results

cristiano@cristiano:~$ sudo iwlist ath0 scan
ath0      No scan results

cristiano@cristiano:~$ sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:15:E9:72:47:3E
                    ESSID:"Private CCS"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=15/94  Signal level=-80 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

```

I also removed the space between "Private" and  "CCS" but still got no results. I also checked Network tools and if i select my wireless card it says: "unknown interface (ath0). Is there still something wrong whith my card??

---

### Post by chili555 on 2007-03-27
We are getting very close. The scan gave us the information we need. I notice it says:```
Encryption key:on
```Do you have the WEP or WPA key? Let's assume, for the moment, it's WEP. We want the 10- or 26-character code, something similar to this: 93c8530b2df51711bad5596f91.

Please issue these commands:```
sudo iwconfig ath0 essid "Private CCS"
sudo iwconfig ap 00:15:E9:72:47:3E
sudo iwconfig key <your_wireless_key>
sudo dhclient ath0
```Hopefully, you will connect.

---

### Post by Porta-Chaves on 2007-03-27
it's a fact that i'm no expert in all this, but I can clearly see that it didn't work out:

```

cristiano@cristiano:~$ sudo iwconfig ath0 essid "Private CCS"

cristiano@cristiano:~$ sudo iwconfig ap 00:15:E9:72:47:3E
Error : unrecognised wireless request "00:15:E9:72:47:3E"

cristiano@cristiano:~$ sudo iwconfig key (hidden)
Error : unrecognised wireless request "(hidden)"

cristiano@cristiano:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ath0/00:03:2f:28:9f:91
Sending on   LPF/ath0/00:03:2f:28:9f:91
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

I also confirmed it whith the Access point, the keytype is ASCII

---

### Post by chili555 on 2007-03-27
Sorry, sir, I goofed. Please amend the commands to the following:```
sudo iwconfig ath0 essid "Private CCS"
sudo iwconfig **ath0** ap 00:15:E9:72:47:3E
sudo iwconfig **ath0** key **s:**<your_wireless_key>
sudo dhclient ath0
```This is from the manual page for iwconfig (man iwconfig):> You can also enter  the  key  as  an  ASCII  string  by  using the s: prefix.So you will need to prefix your ASCII key with s:

Sorry, again. Let's try again, now that Chili has wiped the cobwebs from his head.

---

### Post by Porta-Chaves on 2007-03-27
Yes indeed it worked!!Thank you very much!
Well here is what I got just if you wanted to see it:

```
cristiano@cristiano:~$ sudo iwconfig ath0 essid "Private CCS"
Password:
cristiano@cristiano:~$ sudo iwconfig ath0 ap 00:15:E9:72:47:3E
cristiano@cristiano:~$ sudo iwconfig ath0 key s:(hidden)
cristiano@cristiano:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ath0/00:03:2f:28:9f:91
Sending on   LPF/ath0/00:03:2f:28:9f:91
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 243480 seconds.

```

Now I sometimes use my portable on other accesspoints, all of them have no keys, would be the correct procedure to connect:

```

sudo iwlist scan ath0
sudo iwconfig ath0 essid <ESSID>
sudo iwconfig ath0 ap <MAC>
sudo dhclient ath0

```

??

---

### Post by chili555 on 2007-03-27
You could do it exactly that way. Also, some on these forums swear by NetworkManager, others, including me, like wifi-radar and others like an application called Wicd. [http://compwiz18.blackhole.cx/wicd/wb/pages/features.php](http://compwiz18.blackhole.cx/wicd/wb/pages/features.php)

The aim of all these is for you to click on the network you wish to connect to and all the iwconfigs are taken care of automatically. I suggest you start out with wifi-radar, which you can get from synaptic, and see if it meets your needs.

Glad it's working for you!

---

### Post by Porta-Chaves on 2007-03-27
I installed Wicd and it seems to work, however i couldn't find  Wifi-radar :\

---

### Post by chili555 on 2007-03-27
In synaptic, you should be able to search for wifi and scroll down and see it. However, if Wicd is working well for you, I wouldn't try to "fix" what isn't broken.

Good luck and have fun! Post back if we can help you further.

---

### Post by Porta-Chaves on 2007-03-27
Problem Solved, mods please close :KS

---

### Post by Porta-Chaves on 2007-03-29
Guess not solved, I can't insert ASCII key's on Wicd... It hangs at "Obtaining IP adress"

---

### Post by chili555 on 2007-03-29
I would start a new thread "Trouble with Wicd" if what I suggest doesn't work.

I assume Wicd is a user-friendlier front-end for iwconfig. iwconfig wants ascii keys prefaced with s: So a hex key would look like this: 096efa123..etc. and an ascii should look like this: s:ilovecoldbeer. Try the prefix.

---

