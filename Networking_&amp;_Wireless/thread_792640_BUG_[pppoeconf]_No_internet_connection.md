---
title: "BUG [pppoeconf] No internet connection"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by Draku on 2008-05-13
In Ubuntu 7.10 LiveCD and after install
sudo pppoeconf = internet

In Ubuntu 8.04 LiveCD and after install:
sudo pppoeconf = no internet

Looking for PPPoE Access Concentrator on eth0
Looking for PPPoE Access Concentrator on eth0 (multi-modem mode)
Sorry i scanned 1 interface, but the Acess Concentrator of your provider did not respond

Using the same computer and Ubuntu 7.10 and 8.04 installed on diferent partitions.

---

### Post by superprash2003 on 2008-05-13
could you post your ifconfig output from the terminal

---

### Post by Draku on 2008-05-13
I think the 4 attachments show all the info nedeed.
2 for Ubuntu 7.10 LiveCD and 2 for Ubuntu 8.04 LiveCD

I used the LiveCD to show that the problem is from Ubuntu not me messing around config files

So again the question : Why its not working in 8.04 ?

So the output of ifconfig is :

```
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:66:54:9a:87  
          inet6 addr: fe80::219:66ff:fe54:9a87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x6000 

eth0:avahi Link encap:Ethernet  HWaddr 00:19:66:54:9a:87  
          inet addr:169.254.6.237  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:220 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17002 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:850292 (830.3 KB)  TX bytes:850292 (830.3 KB)
```
Sometimes when i boot i get only eth0 not eth0 + eth0:avahi . If i use ifconfig  eth0 down and then ifconfig eth0 up the avahi doesn't come up but no change in getting the internet to work.

More info on the screenshoots

---

### Post by ROBarber on 2008-05-13
try to boot the system using an old version of kernel with ubuntu 8.04.
andmaybe you should get the latest drive for your network card.

---

### Post by Draku on 2008-05-13
> **ROBarber said:**
> try to boot the system using an old version of kernel with ubuntu 8.04.
andmaybe you should get the latest drive for your network card.

And how do i do that ?

And by the way as you can see in the ss the r8169 driver is the same 2.2LK in 7.10 and in 8.04 so no new driver.

And about the old kernel no option here , what would be the point of installing 8.04 if i use the old kernel from 7.10.

---

### Post by superprash2003 on 2008-05-13
try this
1)go to system->administration->network and go to eth0 properties.. and set it to DHCP mode( if its in Roaming mode).. and then check if you are getting an ip address
OR
2)go to system->administration->network and go to eth0 properties.. and set it to Static ip address and type ip address as 192.168.16.197 and gateway as 192.168.16.193.. and then check if you are getting an ip address

---

### Post by Draku on 2008-05-14
I tried everything before posting the problem on forum and nothing worked.

Setting the wired network from roaming mode to DHCP gives me the same output of screenshot 3 : No DHCPOFFERS recived and the ip is showing 0.0.0.0 in connection information even if i manualy imput my ISP dns servers. By the way in Ubuntu 7.10 the dns server adress is automaticly recived.

Setting the wired network on static ip gives me an ip but the same error on pppoeconf :Sorry i scanned 1 interface, but the Acess Concentrator of your provider did not respond.

The developers should see what they changed in pppoeconf and in network-manager from 7.10 to 8.04 and fix the problem, is getting realy stupid not having an internet connection.

---

### Post by ROBarber on 2008-05-14
You can chose the kernel before the system boots. when you see the GRUB menu hit ESC and you can choose the kernel version. On Hardy I had problems with FF3 but the pppoe connection I was able to trigger it.

---

### Post by Draku on 2008-05-14
> **ROBarber said:**
> You can chose the kernel before the system boots. when you see the GRUB menu hit ESC and you can choose the kernel version. On Hardy I had problems with FF3 but the pppoe connection I was able to trigger it.

I presume you know that in an Ubuntu 8.04 installation the only kernel version avaiable is 2.6.24.16 or did you presume i've updated my Ubuntu 7.10 installation to 8.04 to get 2 kernel entryies on the grub menu.

I've already said on my first post that Ubuntu 7.10 and 8.04 are installed on diferent partitions.

Let's say you r right and with an old kernel i get pppoe connection on 8.04 now tell me how do i install an old kernel in my 8.04 installation ? (Remember I don't have internet connection , and the only kernel on the Ubuntu 8.04 LiveCD and DVD is 2.6.24.16)

---

### Post by ROBarber on 2008-05-15
Well, I think a solution will be to download from [http://www.kernel.org/mirrors/]("http://www.kernel.org/mirrors/") the archive from the version you want on Gutsy, and using a memory stick copy and paste it on your Hardy partition (if you don't have a common mounted device or partition for both Linux distributions) and compile the version of the kernel.

this link shows hot to compile the kernel, please read it carefully
[URL="http://ubuntuforums.org/showthread.php?t=311158"]http://ubuntuforums.or
g/showthread.php?t=311158[/URL].

I hope this will help you.

Anyway, have you tried to unplug the network wire from your network card? Right now I have a silly bug on my machine. The network icon has a small red X on right down side, which means that is no network connection. But somehow the connection to the internet works, even I don't have to trigger the pppoe plug-in. Unplugging the network wire restore the correct situation of the network card.

Good luck

---

### Post by Draku on 2008-05-15
Well i'm afraid that is not an option for me or others which may be in this situation.
If i wanted a customized distribution for me i would make it my self. 
I don't have time compiling kernels just beacause they break pppoe or network-manager or both in the update process.

From my point of view Ubuntu 7.10 should have been a LTS not 8.04

The unplug of the network cable don't work...

---

### Post by ROBarber on 2008-05-15
you can make a try with 'pppconfig', which can configure ppp manually and call it using pon. it has an interface like 'pppoeconf'. maybe this will help you

EDIT:
type on a terminal

sudo tail -f /var/log/messages

and show me the result.

---

### Post by Draku on 2008-05-15
I fixed the problem using this solution : [http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html)

So you where right when you said to update my network card drivers :P

The funny thing is that my network card is Realtek 8168 but Ubuntu 7.10 and 8.04 show as Realtek 8169 ....

---

### Post by ROBarber on 2008-05-21
is good to see that you are now happy :P

---

