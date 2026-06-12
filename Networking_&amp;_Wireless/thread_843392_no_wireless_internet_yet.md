---
title: "no wireless internet yet"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by groundnut on 2008-06-28
Hallo,

I've installed Ubuntu on a Pentium 4 computer.

I can see two neighboring WiFi networks.(thanks to the networking icon at the top right corner on the desktop). But I cannot see my own network. I've disabled all securities. But even that did not show my network. 
What more can I do in order to "see" my network?
So this is the first part of my story.

The second part concerns ndiswrapper.

So far I didn't install the following packages:

ndisgtk (0.8.3-1)
ndiswrapper-utils-1.9 (1.50-1ubuntu1)
ndiswrapper-common (1.50-1ubuntu1)

Because I'm not sure whether it is necessary when you can already see WiFi networks.

So do I still have to install these packages?

If so, how do I install them from a cd?

kind regards,
Tony

---

### Post by stringkarma on 2008-06-28
If you can already see the networks I would imagine that the wireless card is working already and that you shouldn't need ndiswrapper etc. As far as you network not showing are you sure that the router is set to broadcast the name? Under the discovered wireless networks there is an option to connect to other network. This will let you connect by entering in the SSID and other details of your wireless network. This is not always easy. If you have another computer that is using the network you may want to go to the router's configuration page and be sure that it is set up to broadcast correctly.

To summarize it sounds to me like you computer is set up fine and that your network is odd somehow.

---

### Post by groundnut on 2008-06-28
Thank you very much stringkarma.

So I have one remaining problem.
Even after broadcasting the SSID my access point does not show up. I also tried to connect to other network (discovered networks). This also does not work.
So far I did not use the wireless possibilities of the adsl modem. I have only one computer connected to the modem and that is wired.

Any other suggestions why I cannot see my WiFi access point?

kind regards,
Tony

---

### Post by stringkarma on 2008-06-28
I am not quite sure what else I can say. Is it possible to have another friend with a laptop come by and ensure that the wireless is broadcasting. 

Perhaps you can post the output of "sudo iwlist scan" this can help to see that the wireless card is detecting all the proper information from the other networks in your area.

While you are at it why don't you also post the output of "sudo ifconfig" and "sudo lshw -C network"

Maybe we can find something out of place.

---

### Post by groundnut on 2008-06-29
thank you very much stringkarma again.

I've done the three commands you asked for.



tony@xp:~$ sudo iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



wmaster0  Interface doesn't support scanning.



wlan0     Scan completed :

          Cell 01 - Address: 00:90:D0:DE:C2:C3

                    ESSID:"SpeedTouch884867"

                    Mode:Master

                    Channel:6

                    Frequency:2.437 GHz (Channel 6)

                    Quality=46/100  Signal level=-82 dBm  

                    Encryption key:on

                    IE: WPA Version 1

                        Group Cipher : TKIP

                        Pairwise Ciphers (2) : CCMP TKIP

                        Authentication Suites (1) : PSK

                    IE: IEEE 802.11i/WPA2 Version 1

                        Group Cipher : TKIP

                        Pairwise Ciphers (2) : CCMP TKIP

                        Authentication Suites (1) : PSK

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s

                              12 Mb/s; 48 Mb/s

                    Extra:tsf=000001970b778a70



tony@xp:~$ 




tony@xp:~$ sudo ifconfig

eth0      Link encap:Ethernet  HWaddr 00:01:80:32:60:f1  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:22 Base address:0xc000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1204 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1204 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:60200 (58.7 KB)  TX bytes:60200 (58.7 KB)



wlan0     Link encap:Ethernet  HWaddr 00:16:0a:12:88:d2  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wmaster0  Link encap:UNSPEC  HWaddr 00-16-0A-12-88-D2-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



tony@xp:~$ 



tony@xp:~$ lshw -C network

WARNING: you should run this program as super-user.

  *-network               

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: c

       bus info: pci@0000:00:0c.0

       logical name: eth0

       version: 10

       serial: 00:01:80:32:60:f1

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes

  *-network

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:16:0a:12:88:d2

       capabilities: ethernet physical wireless

       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

tony@xp:~$

---

### Post by stringkarma on 2008-06-29
Well I don't immediately see anything that would point to your wireless not working. I still point to the wireless network not working correctly. Can you confirm that it can be seen and/or connected to by some other computer?

---

### Post by groundnut on 2008-06-29
thanks again stringkarma,

Well that sounds positive to me. Hopefully it is already working.

At the moment it is not possible for me to find another (WiFi enabled) computer in order to try to connect to my access point. 

Tuesday I will buy an 5 meter USB extension cable. That will bring my wireless adapter very close to the modem (access point).

So by Tuesday I will know more.

kind regards,
Tony

---

### Post by stringkarma on 2008-06-30
You are welcome to try that, but the access point ought to have a range that a 5 meter cable shouldn't change. BTW most cables including USB cables and peticularly the long ones are greatly overpriced in stores. Look online for deals. I know that shop4tech.com has been good for me in the past (not spamming, just recommending).

---

### Post by groundnut on 2008-06-30
hello again stringkarma,

The five meter length is used to bypass the ceiling.
Because I think the ceiling is blocking the signal.

kind regards,
Tony

---

### Post by groundnut on 2008-07-01
Actually I have two Linux computers net to each other. I have a Pentium 4 computer with Ubuntu and a Pentium 3 computer with Xubuntu. Now a Sweex wireless adapter is connected directly with the Ubuntu computer. I can see the two neighboring networks most of the time. The Xubuntu computer is connected with a Linksys wireless adapter and a 5 m USB extension cable. This system sees the same to networks, but not my own network. Since I bought 2 USB extension cables (one for each computer) I connected them so I could lay the Linksys wireless adapter on top of the modem (access point) The first time I tried that, I did receive a wireless signal from my own modem. Later I could not repaeat that.
The sweex wireless adapter does not function with an extension cable.

So now I have to figure out how to contunue.

kind regards,
Tony

---

### Post by groundnut on 2008-07-03
hello,

I bought two 5 meter USB repeater cables. When I combine these two I can sometimes see my own network. The 10 meter length brings the wireless adapter into the same room as the modem(LAN router).

However once I receive a signal from my network I am not able to login. Not even with the WEP security disabled.

kind regards,
Tony

---

### Post by groundnut on 2008-07-03
hello,

I have changed the wifi radio channel from auto to 13. This resulted in a stable wifi signal reception.

The login problem remains.

kind regards,
Tony

---

