---
title: "Network Manager problems: (wired) internet dissconecting - NM showing still coneccted"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by explicitly ambiguous on 2007-05-17
Hello,

I am having problems with Network Manager;  when I log in it doesn't auto-connect -- my solution is to left-click and select 'Wired Network' -- this I can live with.  The real problem for me is that after some amount of time (which appears to be less the more load I put on the connection) the internet stops loading and torrents stop downloading, etc.

I have searched and searched on these and other forums to no avail...  Perhaps someone here would be kind enough to help me out by looking into this?  Or pointing me towards what I may have missed in the forums ;-)

Here's some of the output from various terminal commands that may help with finding the source of this problem.

Thanks for reading,

Andy W



> 
andy@8-P:~$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:80:C8:FC:6C:13  
          inet addr:77.97.231.202  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::280:c8ff:fefc:6c13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:38 txqueuelen:1000 
          RX bytes:8433171 (8.0 MiB)  TX bytes:1277632 (1.2 MiB)
          Interrupt:18 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)


> andy@8-P:~$ **sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@00:0d.0
       logical name: eth0
       version: 00
       serial: 00:80:c8:fc:6c:13
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=77.97.231.202 latency=0 multicast=yes
       resources: ioport:a400-a41f irq:18


> andy@8-P:~$ **cat /etc/network/interfaces **
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


Oh and I forgot to say -- I'm using Fiesty 7.04 (amd64)

---

### Post by blazercist on 2007-05-17
dude first comment out those million or so interfaces in /etc/network/interfaces you are only using eth0 right?  So just leave eth0 alone and comment the rest.  

Also, are you using a router?  I had this problem in windows, it was my torrent software, requests would hammer my router because I had the ports blocked and my router would freeze up and I would lose my connection.  try opening the correct port for your torrent client.

---

### Post by explicitly ambiguous on 2007-05-17
Hahahaha....the internet just went down again, just after I posted to the forum.  Here's what terminal said just after the connection failed (NM is still showing that I'm connected):

> andy@8-P:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:80:C8:FC:6C:13  
          inet addr:77.97.231.202  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::280:c8ff:fefc:6c13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114939 errors:0 dropped:1404 overruns:0 frame:0
          TX packets:7246 errors:108 dropped:0 overruns:0 carrier:0
          collisions:50 txqueuelen:1000 
          RX bytes:12724643 (12.1 MiB)  TX bytes:1618261 (1.5 MiB)
          Interrupt:18 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16274 (15.8 KiB)  TX bytes:16274 (15.8 KiB)


If I then disconnect via NM and try and reconnect after about a min it 'reconnects' and then the terminal says:

> andy@8-P:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:80:C8:FC:6C:13  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114939 errors:0 dropped:3692 overruns:0 frame:0
          TX packets:7246 errors:257 dropped:0 overruns:0 carrier:0
          collisions:50 txqueuelen:1000 
          RX bytes:12724643 (12.1 MiB)  TX bytes:1639686 (1.5 MiB)
          Interrupt:18 Base address:0xa400 

eth0:avah Link encap:Ethernet  HWaddr 00:80:C8:FC:6C:13  
          inet addr:169.254.7.20  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38359 (37.4 KiB)  TX bytes:38359 (37.4 KiB)



Although right clicking on NM and selecting 'Connection Info.' yields the screen shot I have attached below.

blazercist:  I have commented out the other interfaces and I'm unable to use any torrent clients at the moment until i can fix this problem.  There is no router in my system just the cable modem straight into my network card.

I'm at a total loose-end over this one -- no idea what to try next.....and I'm fed up rebooting my computer every time i want to use the internet :(

---

### Post by blazercist on 2007-05-17
a weird problem is yours. 

have you tried to unplug your cable modem and plug it back in after waiting about a minute?

I know it sounds dumb but many modems have internal memory which can get clogged causing irradic behaviour.

NM has been flaky lately, I suggest trying to set you connection info manually instead of using DHCP maybe that will work?

---

### Post by Demonfire on 2007-05-17
Im having the same EXACT issue as you. Its the strangest thing, it just wont hold the connection and everything else is exactly the same as you. It just seems to randomly drop, and the thing is that it works on every other computer perfectly.

THIS IS DRIVING ME INSANE!!!

if anybody wants some printouts of terminal commands, please ask.

---

### Post by explicitly ambiguous on 2007-05-17
I've tried serveral times doing the trick with the unplugging of the modem.....hmmm....

Could you elaborate about setting up manually my connection...?  I don't have a fixed IP address -- is there some way to get the IP address to change automatically if I set up manually or would I have to re-configure my settings everytime my ISP changed...appologies if these are trivial questions :$

Demonfire:  Yes it is irritating!  Nevermind, Ubuntu is very enjoyable to use otherwise ;-)  I should have clocked this problem when I installed as I had this problem from the liveCD that I installed from....mind you I don't know if it would have done any good :-D

Andy

---

### Post by strixy on 2007-05-17
I had teh same problem every time I tried to use Ktorrent. I was able to work around it by powering down the computer - right down to unplugging the computer's power supply or turning off the power bar. I also don't use Ktorrent anymore, but I'm having a hell of a time trying to get any torrents to download as nothing works.

---

### Post by aristotlewilde on 2007-05-18
I am having the same issue.  Posted elsewhere, but no responses.  

Here's the deets:

I recently installed Feisty on the following setup:

Asus A8v-vm Motherboard
Amd64 3500+ CPU
1 gig of RAM
BFG Geforce 6600gt videocard

I am hooked up to the internet through a Linksys WRT54gs Router with a WIRED CONNECTION.

The computer sits right next to my windows PC which is also connected to the same router (wired).

This occurs whether I have programs actively using the internet or not.

After a few hours, my internet connection on the Feisty box just goes bye bye. I have to restart to enable it. The windows box does nto lose connection.

Anyone have ideas?

---

### Post by Demonfire on 2007-05-20
How is it possible that the wired connection doesnt technically get dropped but you wont be able to connect to websites?! It doesnt make any sence to me!

It worked flawlessly before, and it seems that this is becoming a fairly common issue among ubuntu users and shoud be addressed.

---

### Post by jba6511 on 2007-05-22
same issue here guys. WIRED connection with a static ip behind a linksys router. WIndows boxes have no troubles at all but after a few minutes I loose internet with ubuntu. Anyone figure it out?

---

### Post by explicitly ambiguous on 2007-05-25
I'm really confused over this issue now......

As a work around for the problem I've been having I set up a wireless network to get my internet over that instead.  As I was setting it up, I wired the router between the modem and the network card -- and low-and-behold my internet connection is more stable......??  It stayed connected for almost 24 hours......which is alot longer than the 1-2 hours before disconnection I was experiencing previously.  Still however, NM does not detect the connection automatically on boot.

I thought I'd try my luck a bit further by starting up ktorrent and trying a download, but this did crash the internet connection (although NM still shows me as connected)....

....so I guess I'll continue with my original plan of setting up the wireless network.....

Any ideas on how to solve this anybody?  I'm completely and utterly confused :-(

Andy

---

### Post by explicitly ambiguous on 2007-05-25
OK -- strike that last comment. My internet was no more stable.....it went down after only a few mins the second time.  

I have set up a wireless network now, with no problems.  It seems a shame to have failed to set up  a solid wired connection with Network Manager......

I hope that someone can find a solution, as I don't like running a wireless network if I don't have to.    I do love Ubuntu -- but this has absorbed a vast amount of time for me, which is dissapointing.

Anyhoo, I don't like being dissapointed so i guess i can go back to enjoying Ubuntu now that i have found a workaroud ;-) \\:D/

---

### Post by cor2y on 2007-05-26
i have the same problem random disconnects on a WIRED connection i am using a linksys wrt54g router which connects to my dsl modem.
When i get my disconnect (the network manager disappears then reappears) i also get a system lockup/slowdown.
Its very annoying, i have not found a work around yet except to kill and restart gnome network manager.
I am afraid to mess with /etc/network/interfaces since i don't know what i am doing there.

I have to say this problem only exists in Feisty, Hoary, Dapper and Edgy did not give this problem.

---

### Post by explicitly ambiguous on 2007-06-04
I'm pleased to say that I have solved this.

I removed the PCI network card that I had (RTL-8029(AS) Realtek Semiconductor Co., Ltd.) and connected the LAN to my motherboard's own network interface ( Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller).  I also pulled out the wirless PCI card I was using as a workaround.

Connected directly to my cable modem (Motorola MSB5101E) the Ubuntu LiveCD (7.04 amd64) would not automatically connect -- via a router (Belkin F5D7231-4) it would!

I've no idea why this works but I would love to hear from anyone who knows.

Andrew

---

