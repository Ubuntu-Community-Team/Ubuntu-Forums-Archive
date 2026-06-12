---
title: "WireShark on Intel PRO/Wireless 3945ABG"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by suby-luby on 2008-06-08
Hi All,

I am trying to gather some statistics about my wireless connection for a period of time (e.g., how many control/management packets were exchanged, how many arrived corrupt and hence discarded, etc.).

I installed wireshark and following the documentation have it set to promiscuous mode. However, it does not show me any wireless link details (only http, tcp, etc.).

I know I can set it to monitor mode, but that would prevent me from communicating (I have to be passive and listen to someone else's communications).

My wireless card is intel pro/3945ABG on a Sony Vaio laptop running Ubuntu 8.04.

This is for a research project that I am working on and would like to plot these number (if I can ever get them).

Please help if you know, please please.

---

### Post by pytheas22 on 2008-06-08
I'm not an expert, but I'm pretty sure that monitor mode is the same as promiscuous mode.  If you want to be sniffing the traffic around you, you have to be in monitor mode; it's not possible to sniff and have the card in managed mode for normal TCP/IP networking at the same time.

Also I'm not sure exactly what kind of packets you're looking for, but Wireshark wasn't developed for wireless sniffing exactly so it may not be able to pick up the kind of stuff you want.  You'd probably have better luck using kismet or airodump-ng (part of the aircrack-ng suite), which are both designed expressly for capturing wireless packets.  Once you've captured them in kismet or airodump-ng, you can still view the in Wireshark.

---

### Post by suby-luby on 2008-06-09
> **pytheas22 said:**
> I'm not an expert, but I'm pretty sure that monitor mode is the same as promiscuous mode.  If you want to be sniffing the traffic around you, you have to be in monitor mode; it's not possible to sniff and have the card in managed mode for normal TCP/IP networking at the same time.

Also I'm not sure exactly what kind of packets you're looking for, but Wireshark wasn't developed for wireless sniffing exactly so it may not be able to pick up the kind of stuff you want.  You'd probably have better luck using kismet or airodump-ng (part of the aircrack-ng suite), which are both designed expressly for capturing wireless packets.  Once you've captured them in kismet or airodump-ng, you can still view the in Wireshark.


Thanks Pytheas22,
Here is what I am trying to get

Turn sniffer on at time 0
sniff
Turn sniffer off at time x

Give me how many data packets were transmitted, received, receiver in error, collided, RTC/CTS/ACK packets exchanged.

I tried airodump and it seems it gives a reasonable level of detail. However, I have to run in in monitor mode, which means my computer cannot be an active transmitter/receiver.

Do I have to be an outsider to the connection to get statistics about it?

Thank you for your help

---

### Post by pytheas22 on 2008-06-09
> Do I have to be an outsider to the connection to get statistics about it?

As far as I know, yes, because you can't be sniffing and transmitting your own normal data on the same interface at the same time.  If you had two wireless interfaces, you could use one to sniff and have the other up for a normal connection, but I don't think you can do that if you only have one card.  I think it's possible to do advanced things and create multiple virtual interfaces, which might allow you effectively to sniff and transmit data on the same card, but I don't know about that; you could search around Google for instructions if you really want to try, but I don't think it's very easy.  If you could get your hands on a second wireless card, that would be the simplest solution.

---

### Post by suby-luby on 2008-06-10
I purchased a new wireless card, Belkin G+ MIMO, downloaded the driver from [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

I installed the driver successfully, turned my built-in wireless card off (i.e., wlan0), and executed the following commands to turn of USB-wireless (the external one): 

ifconfig wlan1 up
iwlist scan | more

scanning was successful, so I issued
iwconfig wlan1 mode managed
iwconfig wlan1 essid "network-name-here"
dhclient wlan1

I got an IP address,

ping bbc.co.uk

successful transmissions, but then I cannot browse the Internet, and I cannot see a list of detected APs  in the network manager in the corner.

Can you please tell me what would have done wrong? Does have anything to do with the fact that I now have two wireless cards?

Thanks

---

### Post by pytheas22 on 2008-06-10
That's strange behavior...if you can ping, you should be able to also access the Internet.  Are you sure that you chose the right driver from serialmonkey for your card--if you don't know, what is the lspci output for it?  Are you sure that you brought the first card down before bringing the second one up (i.e. using ifconfig wlan0 down) and that you don't have any other network devices up (i.e. ethernet)?

Also keep in mind that the serialmonkey drivers should be great for sniffing, so if you want, instead of troubleshooting your new card, you could use that one in monitor mode and use your original device for normal Internet connectivity.  I've played with aircrack/airodump on lots of different kinds of chipsets, and rt73 or rt2570 with serialmonkey drivers are the best I've had.

---

### Post by suby-luby on 2008-06-10
You will find this very interesting.

To bring wlan0 down, I used to simply turn off the wireless switch that my computer has. It turned out that this (somehow) used to give applications the impression that no wireless is running (even though wlan1 was up).

What I did now was to leave the switch on, issue
ifconfig wlan0 down
ifconfig wlan1 up

and things worked just fine.

At the beginning I thought somehow it was still using wlan0, but issuing iwconfig showed me only lo and wlan1

what threw me off was that wavemon still reported signal statistics for wlan0.

so, I decided to turn on wlan0 in monitor mode. This threw wavemon off and it gave a segmentation fault.

sharkwire, on the other hand, had no problem with it, it monitored on wlan0 and was extracted from wlan1 just fine.

Any ways, I thought you may find this interesting, and thank you so much for your help.

---

### Post by pytheas22 on 2008-06-10
It is weird, but I've heard of similar things happening.  I think the system sometimes doesn't know which interface it should be routing TCP/IP traffic through if ifconfig thinks that more than one interface is up.  And it seems that sometimes shutting the power off doesn't cause ifconfig to update what it thinks is going on, so it was probably still trying to route through wlan0 instead of wlan1 until you explicitly told ifconfig to bring wlan0 down.

Anyway, good luck with this project.

---

### Post by nater1111 on 2008-08-23
what driver did you install for wireless sniffing via wireshark?  i have the same wifi card and cannot find what to install to enable wifi sniffing.  i know in windows its airpcap.

---

### Post by pytheas22 on 2008-08-23
> what driver did you install for wireless sniffing via wireshark? i have the same wifi card and cannot find what to install to enable wifi sniffing. i know in windows its airpcap.

Please post the output of:

```
lshw -C Network
sudo iwconfig eth1 mode monitor
sudo iwconfig wlan0 mode monitor
```

so we know exactly which driver you're using.  With that we can tell you how to enable sniffing mode.  Airpcap is only for Windows, so don't try to install that.

---

### Post by Esqulax on 2008-08-31
Just a quick newbie Question...
I have a 3945ABG in my MSI Wind, running Hardy.

What commands do i do to:
A> Put it in Monitor Mode
B> Put it in Normal Mode

Merci!

---

### Post by pytheas22 on 2008-08-31
> What commands do i do to:
A> Put it in Monitor Mode
B> Put it in Normal Mode

To put the card in monitor mode, generally you use:
```

sudo iwconfig wlan0 mode monitor
```

But most programs (Wireshark, airodump) will automatically put the card in monitor mode anyway when you tell them to start capturing traffic, so using iwconfig is probably not necessary.

Also, I'm not sure whether the build of the iwl3945 driver in Hardy supports monitor mode.  If you get an error--or if iwconfig says that the card is in monitor mode but it doesn't seem to be able to sniff properly, which happens, because iwconfig sometimes lies--you may need to recompile the driver with support for promiscuous mode.

By the way, how do you like your Wind?  I was thinking of buying one but need to be able to do serious work on it...is it fast enough and the screen large enough for heavy-duty word processing and extended web browsing?  In other words, I need it to be comparable in functionality to a full-size laptop, not more of an oversized PDA.

---

### Post by Esqulax on 2008-09-01
To be honest, its a bit small for "serious" work..like you would use it as your day-to-day computer
It defintaly has the power for it.

The standard wifi card is a bit of a bugger the get going in Ubuntu, so i just bought the 3945ABG, and popped it in (might void your warrenty, so careful)
Everything works with hardy .. apart from the wifi and suspend mode.. i havnt tested the webcam though. 
Suspend can be fixded fairly easily.
I relly only got it cos my macbookpro is a bit pricey, and bulky to be lugging everywhere!

---

### Post by Esqulax on 2008-09-01
Also, my original Question.. worked ut aswell..

To do it manually one must

```

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo ifconfig wlan0 up

```

It cant change modes while its running.
To change it back... exactly the same, cept mode is managed.

Thanks for your help pytheas22!

---

