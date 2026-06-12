---
title: "I fixed my internet connection.  It might fix yours too"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by JimPennell on 2006-11-30
My Internet did NOT work after I installed Ubuntu.  All of the network configuration files looked good, and Windows worked so the hardware was OK.

After a LOT of messing around and trying things, I finally figured out apic was freaky on this machine.

So, I re-installed Ubuntu.

====================

First, at the intitial screen when the CD program is timing from 30 seconds before starting Ubuntu, hit the ESC key and then exit to the text mode.

now, type at the Boot prompt    live noapic nolapic

===================

After I did that, I was able to complete the install and now my internet works nicely.

With a little luck, this might solve some other people's internet connection problems.


   Jim Pennell

-- 

22:34 Pacific Time Zone
Nov 29 2006

International Time
06:34 UTC
30.11.2006

---

### Post by bxlinux on 2006-11-30
I will give this a try and hopefully it will work. :-k

---

### Post by bxlinux on 2006-11-30
before I try to reinstall is there a way to do this with out totally reinstalling ubuntu?

---

### Post by JimPennell on 2006-11-30
I am not familiar enough with Linux to know if there is any way to fix this short of a re-install.

It is an interesting question whether or not there is a way to fix apic problems without a re-install.  Perhaps a Ubuntu guru will jump in with suggestions.

The clue I had about apic being a problem was an error message I saw for a second or two during shutdown.  The install and everything else in Ubuntu worked fine, the only thing screwed up was the Ethernet connection.  Actually, I even got a response from the DHCP request.  It just locked up on normal attempts to get online.


    Jim Pennell



08:27 Pacific Time Zone
Nov 30 2006

International Time
16:27 UTC
30.11.2006

---

### Post by Iowan on 2006-11-30
I suspect (notice a lack of confidence...) you can edit Grub's **menu.lst** file to embed that option without re-installing.
```
gksudo gedit /boot/grub/menu.lst
```
From [https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")> 
Options can be used together such as in this example: 
/boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash noapic nolapic 


---

### Post by JimPennell on 2006-11-30
Thanks !!!

If anyone DOES fix their internet using the suggestion by Iowan, or for that matter, doing the re-install, please post here with the result.

I would like to learn if this is a common problem with Internet connections, or if it's just my particular machine. :)

  Thanks, Jim



10:34 Pacific Time Zone
Nov 30 2006

International Time
18:34 UTC
30.11.2006

---

### Post by Thumper322 on 2006-11-30
Hey Jim,

My networking (WPC54G PCMIA card) worked perfectly as soon as I set up **ndiswrapper**; is this a wired or a wireless connection?

Not sure what "apic" is; isn't "acpi" a power management tool?

---

### Post by JimPennell on 2006-11-30
Advanced Programmable Interrupt Controller (APIC)

This is a part of the motherboard.  In my case, it was not configuring the Ethernet correctly.

I do not know if this is a common problem, but I had eliminated a whole lot of possibilities before finding this.  

It may (?) be something that is screwing up some of the other people who have internet connection problems.

That puzzle is why I am curious if this solution fixes someone else's computer.  I'd like to know if it was just my system or if it's a common problem.


     Jim



16:31 Pacific Time Zone
Nov 30 2006

International Time
00:31 UTC
01.12.2006

---

### Post by JimPennell on 2006-11-30
OOOPS...  I forgot part of what you asked.  My connection is a standard wired connection.

The Ethernet port on my machine is part of the motherboard itself.


      Jim

---

### Post by bxlinux on 2006-12-01
Unfortunately after trying this I still cannot get my ethernet to pick up an IP address. I put in the live noapic nolapic as stated when booting but still nothing.

---

### Post by Thumper322 on 2006-12-01
> **bxlinux said:**
> Unfortunately after trying this I still cannot get my ethernet to pick up an IP address. I put in the live noapic nolapic as stated when booting but still nothing.
What happens if you type (just off the top of my head, I may be wrong): **sudo ifdown eth0; sudo ifup eth0**?

What's your network card model?

---

### Post by bxlinux on 2006-12-01
Here is all the info for when I ran several command codes. I cheated and took it from my other thread:) 

lspci grep controller (with ethernet connected by the way)
also figured you needed the ethernet controller info if you need the vga let me know
01:03.0 network controller: Broadcom corporation BCM4309 802.11 a/b/g (rev 03)
01:08.0 Ethernet controller: intel corporation 82801db Pro/100 VE (mob) Ethernet controller (rev 81)

cat /etc/network/interfaces

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

Iwlist scan

lo iterface doesnt support scanning

eth0 interface doesnt support scanning

eth1 no scan results
sit0 interface doesnt support scanning

ifconfig
Eth0
link encap:Ethernet Hwaddr 00:11:43:3c:6c:f8
inet6 addr: fe80::211:43ff:fe3c:6cf8/64 Scope:Link
up Broadcast Running Multicast MTU:1500 Metric 1
RX Packets:33314 errors:0 dropped:0 overruns:0 Frame:0
TX packets:44 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
Rx bytes:2047006 (1.9 MiB) Tx bytes:11880 (11.6 KiB)

Lo
Link encap:Local Loopback
inet addr:127.0.0.1 mask 255.0.0.0
inet6 addr: ::1/128 scope:Host
Up Loopback Running MTU:16436 Metric:1
RX packets:330 errors:0 dropped:0 overruns:0 Frame:0
tx packets:330 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
Rx bytes:24400 (23.8 KiB) Tx Bytes:24400 (23.8 KiB)

---

### Post by geekygreen on 2006-12-01
I had some issues with network not working, and when poking around  I noticed that the NIC card was inactive.  By going to system/administration/networking tools you can tell the card to be "ACTIVE".  It already is Active, try to set it to INACTIVE (Un-check the Active box), back up a couple of  menu items, and then go back and activate it.  Perhaps a reset will help things...

There may be an easier way to do that, it seems everytime I do something I get there from a different way....

---

### Post by Iowan on 2006-12-01
[QUOTE=bxlinux] Unfortunately after trying this I still cannot get my ethernet to pick up an IP address.  [/QUOTE]
A few more things to try:
1) Manually (from a terminal) run **dhclient.**
2) Disable ipv6 (link to a HowTo is in my signature).
3) In **/etc/network/interfaces**, comment out any interfaces you may not have (eth1, eth2...)

---

### Post by Thumper322 on 2006-12-01
> **bxlinux said:**
> Here is all the info for when I ran several command codes. I cheated and took it from my other thread:) 

**lspci grep controller** (with ethernet connected by the way)
also figured you needed the ethernet controller info if you need the vga let me know
```
01:03.0 network controller: Broadcom corporation BCM4309 802.11 a/b/g (rev 03)
01:08.0 Ethernet controller: intel corporation 82801db Pro/100 VE (mob) Ethernet controller (rev 81)
```**cat /etc/network/interfaces**

```
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
```**Iwlist scan**

```
lo iterface doesnt support scanning

eth0 interface doesnt support scanning

eth1 no scan results
sit0 interface doesnt support scanning

```**ifconfig**
```
Eth0
link encap:Ethernet Hwaddr 00:11:43:3c:6c:f8
inet6 addr: fe80::211:43ff:fe3c:6cf8/64 Scope:Link
up Broadcast Running Multicast MTU:1500 Metric 1
RX Packets:33314 errors:0 dropped:0 overruns:0 Frame:0
TX packets:44 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
Rx bytes:2047006 (1.9 MiB) Tx bytes:11880 (11.6 KiB)

Lo
Link encap:Local Loopback
inet addr:127.0.0.1 mask 255.0.0.0
inet6 addr: ::1/128 scope:Host
Up Loopback Running MTU:16436 Metric:1
RX packets:330 errors:0 dropped:0 overruns:0 Frame:0
tx packets:330 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
Rx bytes:24400 (23.8 KiB) Tx Bytes:24400 (23.8 KiB)
```

OK... Let me see what I can make of this.

First off, you don't need to worry about **iwconfig**--it's for wireless connections. Your **/etc/network/interfaces** file also looks fine to me.
> 
```
01:03.0 network controller: Broadcom corporation BCM4309 802.11 a/b/g (rev 03)
```That's your wireless card; have you had any success with it, and do you want to use it?

> ```
01:08.0 Ethernet controller: intel corporation 82801db Pro/100 VE (mob) Ethernet controller (rev 81)
```I Googled your Ethernet controller; nothing came up of relevance.

> ```
RX Packets:33314 errors:0 dropped:0 overruns:0 Frame:0
TX packets:44 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
```Looks like you're having trouble sending packets. Notice all 33,000 errors? :-k

If you have Network Manager installed, you should automatically connect to the network as soon as the cord is plugged in. If you're not using a network manager, plug the Ethernet cord in and  run:
```
sudo ifdown eth0; sudo ifup eth0
```This should disconnect from the network, if connected at all, then (re)connect.

If this fixes your problem, then you have three options, to my knowledge:[LIST]
[*]Whenever you want to connect to the network, issue **sudo ifdown eth0; sudo ifup eth0**
[*]Install Network Manager (it's in Add/Remove Applications)
[*]Plug in the Ethernet cord before booting[/LIST]

Good luck, and sorry for the long post.

---

### Post by bxlinux on 2006-12-01
Tried to follow your thread on turning off ipv6 but not sure what you mean by comment out. Is that the # sign. Also trying the ifdown ... I get msg no working leases. Forgive the abbreviations but using my blackberry. I also tried to install network mgr but it is not supported by i386. Any other suggestions.

---

### Post by Thumper322 on 2006-12-01
> **bxlinux said:**
> Tried to follow your thread on turning off ipv6 but not sure what you mean by comment out. Is that the # sign. Also trying the ifdown ... I get msg no working leases. Forgive the abbreviations but using my blackberry. I also tried to install network mgr but it is not supported by i386. Any other suggestions.

Um, I didn't say anything about ipv6... Maybe you're thinking of something else? I don't see why ipv6 would be causing trouble.

Network Manager works fine on my PC, and it's an i386... As far as "no working leases," that simply means that you're not connected.

So, here's what I'd do:
[LIST]
[*]Turn off the computer.
[*]Plug in the Ethernet cord.
[*]Turn on the computer.
[*]Run **sudo ifup eth0**.
[*]Try pinging Google: **ping google.com**. (Ctrl-C will stop it.)
[/LIST]

Try that, and post back with what happens.

---

### Post by bxlinux on 2006-12-01
Oh by the way I am not using the wireless as I do not have a wireless router.

---

### Post by robertrej on 2006-12-01
I really need help with my wireless network adapter
connection !to access the internet.
I have a asus p4p 800 vm mother board.
         SMC2862W-G EZ CONNECT 2.4 802.G WIRELESS USB 2.0 ADAPTER 
and can not figure out how to install the necessary driver  . I did install ndiswrapper ok
but after that I am lost .
 If any one can help it would make an old man happy.       Thanks bob

---

### Post by bxlinux on 2006-12-01
I've tried rebooting with and without ethernet connected but still nothing. Only problem I am having with ubuntu. Video works music works everything except networking. I do appreciate all the help. Really do like ubuntu and won't stop till I get it to work. How can check link speed.

---

### Post by bxlinux on 2006-12-01
I am trying everything posted not sure why my i386 network manager is not installing. I am a newb at this so bare with me. I am getting link lights. I get packets. just not sure what else I can try. Reinstalling didnt work. ifup ifdown not working. Driver install may be what I need. Is there a specific way I can install a driver with unix. (newb)](*,)

---

### Post by robertrej on 2006-12-03
Well I got tired of looking for the right driver
and just went out and bought some cat.5 cable
and am running the internet that way.
I know !I know !its a bit lazy but it fast and easy
and ha it works ! 

                      Thanks just the same
                      Bob



> **robertrej said:**
> I really need help with my wireless network adapter
connection !to access the internet.
I have a asus p4p 800 vm mother board.
         SMC2862W-G EZ CONNECT 2.4 802.G WIRELESS USB 2.0 ADAPTER 
and can not figure out how to install the necessary driver  . I did install ndiswrapper ok
but after that I am lost .
 If any one can help it would make an old man happy.       Thanks bob

---

### Post by bxlinux on 2006-12-03
I havent been so fortunate. I tried about everything and about to give it up and go and see if windows will work. Even tried another brand of linux and the samething occurs so I am pretty sure its not a hardware issue.

---

### Post by Thumper322 on 2006-12-04
> **bxlinux said:**
> I havent been so fortunate. I tried about everything and about to give it up and go and see if windows will work. Even tried another brand of linux and the samething occurs so I am pretty sure its not a hardware issue.

I did a little research. Try this:
[LIST]
[*]Turn on your computer without the Ethernet cord plugged in, then run **sudo modprobe eepro100**.
[*]Plug in the Ethernet cord, and run **sudo ifup eth0**.
[/LIST]

If this works, then run (Alt+F2) **gksudo gedit /etc/modules**, and add **eepro100** to the end of the document.

Good luck...

---

### Post by bxlinux on 2006-12-04
Tried that Thumper and that didnt work either. Still unable to pull an ip address for eth0.

---

