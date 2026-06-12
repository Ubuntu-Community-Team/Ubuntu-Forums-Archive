---
title: "I messed around and now I can't connect..."
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by notesetter on 2008-06-14
Computer:

Compaq Presario 2170US Laptop

Wireless Card:

Lynksys Wireless G Model WPC54G ver.3

Symptom:

After playing with a program called "WiFi Radar," I can no longer connect to the the network either through wireless or through ethernet direct from the router. I've uninstalled "WiFi Radar" and set all my settings within System>Aministration>Network as I do normally. My network never comes up and I can't connect. The secured network shows that it's getting a good signal from the router in the network settings.

Long story short: I had previously managed to connect using ndiswrapper and the Network Settings dialog from above. I deleted the Gnome Network Manager applet and instead was using the "Network Selector" application which enabled me to switch between ethernet and wireless without entering the passkey over and over. Now, in the notification area (where I usually can select between "eth0" and "lan0") only shows a red "X" and displays the text "Disconnected." I can still select the network I want, but it never shows anything other than "Disconnected"

Anyone have any tips?

Thanks,

Dave

---

### Post by pytheas22 on 2008-06-14
What is the output of:

```
ifconfig

```
What happens if you type:
```

ping google.com
```

If you plug in your cable and type:
```

sudo ifconfig eth0 up
```

does the Internet work again?

By the way, Network Manager should not be asking you for your password every time you connect.  You can save the password in a keyring and it should only ask you once each time you log in to Gnome, I think.  But let's solve the larger problem and then deal with NM.

---

### Post by notesetter on 2008-06-14
First, thanks for the response. Here goes...

I ran ifconfig in a terminal and got:

```
david@ubuntudavid:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:a7:89:ba  
          inet6 addr: fe80::20b:cdff:fea7:89ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:184060 (179.7 KB)  TX bytes:468 (468.0 B)
          Interrupt:10 Base address:0x2000 

wlan0     Link encap:Ethernet  HWaddr 00:18:39:5e:90:14  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:24000000-24002000
```

When I typed: 

```
ping google.com
```

I got:

```
ping: unknown host google.com
david@ubuntudavid:~$ 
```

When I typed:

```
sudo ifconfig eth0 up
```

nothing seemed to happen. Afterwards, I brought up firefox and got the "Page Load Error" message. I tried configuring the eth0 properties and tried firefox again. still nothing.

---

### Post by pytheas22 on 2008-06-14
You don't have an IP address, so that's the most obvious problem.  With your cable plugged in, type:

dhclient eth0

and please post the output.  If your router serves IP addresses via dhcp, this should get you one.

---

### Post by notesetter on 2008-06-14
```
david@ubuntudavid:~$ dhclient eth0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
david@ubuntudavid:~$ 
```

---

### Post by pytheas22 on 2008-06-14
sorry, forgot about permissions.  Run this instead:
```

sudo dhclient eth0
```

---

### Post by notesetter on 2008-06-14
Right...

```
david@ubuntudavid:~$ sudo dhclient eth0
[sudo] password for david: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0b:cd:a7:89:ba
Sending on   LPF/eth0/00:0b:cd:a7:89:ba
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.101 from 192.168.1.1
DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.101 from 192.168.1.1
bound to 192.168.1.101 -- renewal in 38718 seconds.
david@ubuntudavid:~$ 
```

This gets me a wired connection. I'll probably take the next suggestion "off the air" so to speak. I'll be away from the machines for the next several hours. Can I reply to this thread tomorrow?

Thanks for the help.

Dave

---

### Post by pytheas22 on 2008-06-14
Alright, it's good that you can get a connection; this problem should be easy to solve now that we know that it's just the IP issue.  The next thing to do is try "sudo dhclient wlan0" (after connecting to the wireless network using Network Manager or another utility) to make sure that it works for the wireless connection as well.  Then we can set it up so that the system runs dhclient automatically.

But yeah, get back tomorrow on the results of dhclient wlan0 and we'll go from there.

---

### Post by notesetter on 2008-06-15
Hi again,

I've tried to connect to the network through wireless and haven't been able to. I've tried several different ways.

My network automatically appears in the network settings dialog, and it is marked as enabled. When I configure it and type in the passkey, it acts like it's connecting, but I still don't have wireless. When I check to see if I typed the passkey incorrectly, I notice that there are several more characters in the passkey field than I originally entered. This happens over and over again.

I went ahead and tried "dhclient eth0" and here are the results:

```
david@ubuntudavid:~$ sudo dhclient wln0
There is already a pid file /var/run/dhclient.pid with pid 11811
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wln0: ERROR while getting interface flags: No such device
wln0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
david@ubuntudavid:~$ 
```

thanks.

Edit:

Here's the output from the correct code: dhclient wlan0

```
david@ubuntudavid:~$ sudo dhclient wlan0
[sudo] password for david: 
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:39:5e:90:14
Sending on   LPF/wlan0/00:18:39:5e:90:14
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
david@ubuntudavid:~$
```

sorry

---

### Post by pytheas22 on 2008-06-15
I forgot, but you won't be able to connect wirelessly with Network Manager if dhclient is not running properly on its own.  You could get on the network using the command line and then run dhclient, but I think it would be easier if you just used [wicd]("http://wicd.sourceforge.net").  Try installing that utility and see if it will allow you to connect.  wicd usually works a lot better than Network Manager.

---

### Post by notesetter on 2008-06-15
Thanks. will try wicd later today, and post back this evening.

Thanks for the assistance, I'm learning my way around GNU/Linux, after many years as a Windows user.

Dave

---

### Post by notesetter on 2008-06-16
Hi there,

I've got Wicd working for wired connection and it automatically connects when I boot into UbuntuStudio 8.04. I can't get it to connect to the wireless network though. The network is automatically detected and I can even enter the passkey, but when I click "connect," it goes through the process of trying to obtain an IP address, but when it's done, it displays "Not connected." Curious that there isn't some kind of error message.

When I run "sudo dhclient wlan0" this is the result"

```
david@ubuntudavid:~$ sudo dhclient wlan0
[sudo] password for david: 
There is already a pid file /var/run/dhclient.pid with pid 10724
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:39:5e:90:14
Sending on   LPF/wlan0/00:18:39:5e:90:14
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
david@ubuntudavid:~$ 
```


Thanks,

Dave

---

### Post by pytheas22 on 2008-06-16
Thanks for the information.  Could you please try to connect to the wireless with wicd and then post the output of:
```

iwconfig
```

immediately after?

Also, if you post the output of:
```

iwlist wlan0 scan
```

 I can tell you the commands to try to connect from the command line, which might be the only solution to getting the wireless working at this point.

---

### Post by notesetter on 2008-06-16
pytheas22,

I double-checked the passkey in Wicd and checked that ndiswrapper was selected as the driver in preferences, and then clicked connect. Wicd went through its routine trying to connect and then displayed "Not connected" I immediately ran "iwconfig" and here are the results:

```
david@ubuntudavid:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@ubuntudavid:~$ 
```

Here is the result of "iwlist wlan0 scan"

```
david@ubuntudavid:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:55:9E:EA
                    ESSID:"linksys_SES_35475"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

david@ubuntudavid:~$ 
```

Thanks again,

Dave

---

### Post by pytheas22 on 2008-06-16
Your AP is in Managed mode according to the scan, which is very curious.  APs should almost always be in Master mode if they're serving as the hub of a wireless network, unless they're serving as repeaters or you have a special setup.  Did you change your router's settings in any way in between when you were able to connect and when you couldn't?  Are other computers able to connect wirelessly to your network?  In any case, checking the router's settings and rebooting it couldn't hurt.  That could be the source of the whole problem.

Here are the commands to try connecting manually:
```

sudo -s
iwconfig wlan0 mode Managed essid "linksys_SES_35475" key YOUR-PASSWORD channel 6
dhclient wlan0
```

Does this work?  If not, what does iwconfig look like after running the command above?

---

### Post by notesetter on 2008-06-16
Hi again,

Well, I haven't done anything to the router besides turn it off and on again, so I don't think that would be it. I don't even know how to change it from "Managed" to "Master" mode. My wife's Vista machine can connect to internet, and this laptop (the one I'm working on) can connect fine when I boot into XP. I think it's odd that when I try the code you suggested, Ubuntu seems to think that the passkey is incorrect:

```
david@ubuntudavid:~$ sudo -s
root@ubuntudavid:~# iwconfig wlan0 mode Managed essid "linksys_SES_35475" key g1lu2u9ludjkwg2m channel 6
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "g1lu2u9ludjkwg2m".
root@ubuntudavid:~# 
```

I'll fool around with the router and see if I can reset it as an unsecured network or set it up with a fresh passkey, to see if that's the problem. I'll refer to the router and wireless card documentation.

Thanks,

Dave

---

### Post by pytheas22 on 2008-06-16
Yes, see if you can connect to the network when it's unsecured.

Also putting the key in quotes might help (i.e. iwconfig wlan0 key "yourpasskey") but I doubt it.

You were definitely able to connect to this network in Ubuntu originally, right?  Do you remember what you did between then exactly?

---

### Post by notesetter on 2008-06-17
Hi again,

Yeah, I installed hardy, and the 2nd thing I did was set up the wireless. It worked well until I fooled with wifi radar.

Here's an update: I've removed ndiswrapper from the system and now no wireless networks are discovered in Wicd. I'm going to try updated drivers and maybe bcm43xx-fwcutter. I'll keep the thread updated with my progress, in hopes that others may find it useful (especially if I get connected again).

Thanks again.

Dave

---

### Post by kevdog on 2008-06-17
turn off the encryption at the router for right now -- reinstall ndiswrapper and give it another shot -- you have wpa installed

---

### Post by pytheas22 on 2008-06-17
> I'm going to try updated drivers and maybe bcm43xx-fwcutter. 

I didn't know you had a Broadcom chipset, but in that case, you shouldn't need ndiswrapper.  Depending on which specific kind of Broadcom chip you have, you might be able to get it to work with the b43 driver, following [these]("http://ubuntuforums.org/showpost.php?p=4793983&postcount=1") instructions.  Otherwise you can revert to bcm43xx and it should work, but you need to blacklist b43 first.  I think there are still some Broadcom cards that aren't supported by the native drivers, but only a few.  If you don't know what the status of your card is, run lspci to get the model and then Google for it.

This isn't necessarily going to solve the problem with being unable to connect--I suspect that the issue there is not related to the fact that your card uses ndiswrapper--but it's usually preferable to have native drivers where possible, so it couldn't hurt to try b43/bcm43xx if you're supported.

---

