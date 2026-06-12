---
title: "wireless card get IP but do not function - edgy"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by orengabay on 2007-02-28
Hello,
I install a new Edgy computer with TP-LINK TL-WN550G wireless card.  After a lot of work I managed to get an IP address from the wireless connection. The problem is that the network is not functioning - ping is not working even to the default getaway. Please help me understand this problem.

I disabled IPV6, but it did not help.

Thanks,
Oren

Some information (the eth0 is well functioning - the problem is only with the wireless)

oren@gms:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:78:77:0D:C9  
          inet addr:10.0.140.224  Bcast:10.0.140.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:962 (962.0 b)  TX bytes:7258 (7.0 KiB)

eth0      Link encap:Ethernet  HWaddr 00:19:DB:23:D9:8A  
          inet addr:172.35.9.93  Bcast:172.25.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17509003 (16.6 MiB)  TX bytes:759713 (741.9 KiB)
          Interrupt:193 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29113 (28.4 KiB)  TX bytes:29113 (28.4 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-78-77-0D-C9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:7
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:6548 (6.3 KiB)  TX bytes:6744 (6.5 KiB)
          Interrupt:185 Memory:dca00000-dca10000 

oren@gms:~$

Network interfaces
----------------------------

oren@gms:~$ more /etc/network/interfaces 
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


iface ath0 inet static
wireless-essid fff
wireless-key ffffffffffffff
address 10.0.140.224
netmask 255.255.255.0
gateway 10.0.140.252

auto wlan0
iface wlan0 inet dhcp










auto ath0

auto eth0
oren@gms:~$ 

oren@gms:~$ more /etc/modprobe.d/aliases


# network protocols ##########################################################
alias net-pf-1  unix
alias net-pf-2  ipv4
alias net-pf-3  ax25
alias net-pf-4  ipx
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
alias net-pf-10 off #ipv6
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI

---

### Post by n00b@linux on 2007-02-28
To eliminate hardware issues, did you try it with dhcp and no encryption?
 
btw, it wouldn't hurt to clean up your /etc/network/interfaces config file (it's quite messy).

---

### Post by orengabay on 2007-02-28
Thanks for your response.
I managed to connect with DHCP to this secured network and also managed to connect to a non-secured network but at that time I did not tried to access the internet. I just managed to see that I got an IP address and I thought it's fine.

I tried to clean the interfaces file and now it's not connecting at all- I don't get an IP addess now.

Best Regards,
Oren

---

### Post by orengabay on 2007-02-28
When I run /etc/init.d/networking restart i get the messages:

wifi0: unknown hardware address type 801 

But with the original interfaces file I managed to get an IP address.

Maybe this information can help...

---

### Post by orengabay on 2007-02-28
Another information is that in ifconfig I see many errors in:
TX packets: 4055 
and it increase as I do ifconfig.

Is that a hardware problem?

---

### Post by n00b@linux on 2007-03-01
1. Disable any encryption (WEP or otherwise) on your ADSL modem/router.
2. Make sure your /etc/network/interfaces configuration file is like this:```
### 'lo' is your loopback interface
auto lo
iface lo inet loopback
 
### 'eth0' is your ethernet card, ie. your fixed-line internet connection interface
auto eth0
iface eth0 inet dhcp
 
### 'ath0' is your wireless card, ie. your WiFi internet connection interface
auto ath0
iface ath0 inet dhcp
```
3. Restart the networking init script```
sudo /etc/init.d/networking restart
```
4. Post the results of the following commands to this thread:```
lspci
ifconfig
iwconfig
iwlist ath0 scan
```

---

### Post by orengabay on 2007-03-01
Hi,
Thanks for your latest post but yesterday after spending another few hours (and before this last post...).  I removed the card and managed to find a weired connection.
Before that I managed to verify that this card is also not working with a non-secured network.
I also tried Knoppix live CD but it also managed to get the same results: getting IP but not functioning.
I will be able to retry this card on another machine in few days - then I will post the results.
Thank you,
Oren

---

### Post by orengabay on 2007-04-21
Just for the information the card was recognized without any configuration with faisty - also connected to the internet automatically without any configurations
Thanks

---

### Post by einstein007 on 2008-02-28
Look it's a real shame that this wasn't sorted out because I am getting the same problem...and this probably means there r others out there too.

My situation is:

1) connected my TP-Link TL-WN550G wireless.
2) ''Seems'' to work out-of-box. That is without installing any drivers Network Manager picks up my local router and assigns me an IP address. I believe this is a result of Ubuntu having already got the drivers for the Atheros chipset my wireless uses (but not sure).
3) Yet even though the signal is shown with good strength and I have an IP address, I can not establish a WEP connection, Or use internet

I would really appreciate any feedback if anyone knows a solution to this.

---

### Post by einstein007 on 2008-02-28
OK, after a little more searching on the Web I found this solution by Adam Pierce.

It worked for me ;)

[http://www.doctort.org/adam/nerd-notes/tp-link-tl-wn550g-in-ubuntu.html#comment-13954](http://www.doctort.org/adam/nerd-notes/tp-link-tl-wn550g-in-ubuntu.html#comment-13954)

---

