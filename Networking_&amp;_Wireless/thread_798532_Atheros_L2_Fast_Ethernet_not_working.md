---
title: "Atheros L2 Fast Ethernet *not working*"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by varghaimani on 2008-05-18
Hi everyone

Im running ubuntu 8.04 64bit on my ASUS P5GC-MX/1333
unfortunately my wired network doesnt work, ive tried compiling the drivers on the cd but its hopeles, can anyone please help me out
thanks alot

Vargha

---

### Post by varghaimani on 2008-05-18
anyone please

---

### Post by varghaimani on 2008-05-19
can anyone please help me out

---

### Post by rijalul on 2008-07-03
> **varghaimani said:**
> can anyone please help me out
I have the same problem...

---

### Post by Master Chief on 2008-07-03
I compiled the driver v1.0.40a (from the CD) on Ubuntu (amd64) for 2.6.24-19-generic (check your kernel version with uname -r)

**Note: ***If an issue is identified with the released source code on the supported kernel with a supported adapter, email the specific information related to the issue to [email]xiong.huang@atheros.com[/email]*

[COLOR="Black"]Note:[/COLOR] [COLOR="Red"]The attached file has been reported to fail so please do NOT use it[/COLOR]

---

### Post by mpascall on 2008-07-05
This driver you compiled on an AMD cpu should work on Intel too, right?

What about with my 2.6.24-16-generic kernel? 

Thanks,
-M

---

### Post by Master Chief on 2008-07-06
> **mpascall said:**
> This driver you compiled on an AMD cpu should work on Intel too, right?

Ubuntu amd64 supports both Intel *and* AMD (I myself use Intel only).

> What about with my 2.6.24-16-generic kernel?

Any particular reason for using an older kernel?  BTW  I compiled it on 2.6.24-16-generic only two weeks ago (32 bit edition) and without any problems.

---

### Post by mpascall on 2008-07-08
Thanks for the reply!  I really appreciate that you help people out in your spare time and you aren't getting paid a dime.  Very cool of you.

> **Master Chief said:**
> Any particular reason for using an older kernel?  BTW  I compiled it on 2.6.24-16-generic only two weeks ago (32 bit edition) and without any problems.

I'm using the kernel that was included in the latest 8.04 live cd.  I've looked into upgrading it, hoping it would solve my networking problem, but haven't figured out how to do so without a live internet connection.  My linux ignorance has put me in a catch-22 situation.  

So should I be able to use the driver your compiled, or do I need to use one compiled specifically for my kernel version?

Actually, I guess I could get a generic network card that let me get on the internet so I can update the kernel and try your driver.

Thanks again!

---

### Post by Master Chief on 2008-07-08
Like I said; I know someone with a P5GC-MX13333 motherboard and he promised to walk in with it this evening.  I already compiled the new drivers (v2) on my 64 bit system, and this without any problems so it looks promising.

p.s. I'll attach the driver here as soon as I have seen it working myself!

---

### Post by Master Chief on 2008-07-08
Ok, here is it ([COLOR="Red"]for 32 bit editions only[/COLOR])   Attached you'll find a working atl2.ko module (archived). Just unpack it in to:

```
/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2/atl2.ko
```

Assuming you are in fact using the same kernel!

You can load the module with:

```
sudo modprobe atl2
```

Or unload it with:

```
sudo modprobe -r atl2
```

Do a DHCP request like this:

```
sudo dhclient ethN
```

Note: Where N is your actual adapter (NIC) (check the MAC address to be sure in case you have more than one!

---

### Post by Master Chief on 2008-07-08
And here's the [COLOR="Red"]64 bit edition[/COLOR] (don't mind the amd64 in the name if you are actually using Intel like me).

**Note:** I also attached the source code!

---

### Post by mpascall on 2008-07-08
Thanks!  I will give this a try once I upgrade my kernel.  I'll post my results.

Much appreciated!
-M

---

### Post by Master Chief on 2008-07-08
> **mpascall said:**
> Thanks!  I will give this a try once I upgrade my kernel.  I'll post my results.

Much appreciated!
-M

Are you using a 32 or 64 bits Ubuntu version?

---

### Post by mpascall on 2008-07-09
64-bit 8.04, with 2.6.24-16-generic kernel.

---

### Post by Master Chief on 2008-07-09
Can you issue a:

```
lsb_release -d
```

or:

```
cat /etc/boot/grub/menu.lst| grep 8.04.1
```

command because I am running 8.04.1 and that might not be compatible ;)

---

### Post by ssj4Gogeta on 2008-07-10
Thanks for your help, Master Chief. :)
It's very much appreciated. But the problem is I have kernel 2.6.24-16-generic, 32-bit. (kubuntu 8.04). So can you please tell me the commands to patch/compile and install the drivers? I've downloaded the patch and the source from the location you mentioned in the other thread. (i.e., [http://people.redhat.com/csnook/atl2/](http://people.redhat.com/csnook/atl2/)).

Thanks again for your time. :)

---

### Post by mpascall on 2008-07-10
> **Master Chief said:**
> Can you issue a:

```
lsb_release -d
```

or:

```
cat /etc/boot/grub/menu.lst| grep 8.04.1
```

command because I am running 8.04.1 and that might not be compatible ;)

Here's the output

```
marcus@marcus-ubuntu:/$ lsb_release -d
Description:	Ubuntu 8.04
marcus@marcus-ubuntu:/$ cat /etc/boot/grub/menu.lst| grep 8.04.1
cat: /etc/boot/grub/menu.lst: No such file or directory
```

There's no "/etc/boot" directory on my system, which is a default install from the 8.04 64-bit live cd taken downloaded from the links on the ubuntu.org website.

I also tried to load your 64-bit driver.  Here are my results:

```
marcus@marcus-ubuntu:/lib/modules/2.6.24-16-generic/kernel/drivers/net/atl2$ ls -l
total 728
-rw-r--r-- 1 root root 740633 2008-07-08 16:31 atl2.ko
marcus@marcus-ubuntu:/lib/modules/2.6.24-16-generic/kernel/drivers/net/atl2$ sudo modprobe atl2
[sudo] password for marcus: 
FATAL: Error inserting atl2 (/lib/modules/2.6.24-16-generic/kernel/drivers/net/atl2/atl2.ko): Invalid module format
```

Is that because it was compiled on a different kernel?  I'm going to get a network card this weekend and update my kernel to 2.6.24-19.  I'll also upgrate to 8.041 if you think that'll help.

Thanks,
-M

---

### Post by Master Chief on 2008-07-10
> **mpascall said:**
> 
There's no "/etc/boot" directory on my system, which is a default install from the 8.04 64-bit live cd taken downloaded from the links on the ubuntu.org website.

It should have been /boot/grub... but I got it you are indeed still using 8.04 instead of 8.04.1  You don't want to update and be safe?

> 
I also tried to load your 64-bit driver.  Here are my results:

Surely that won't work on your kernel!

> Is that because it was compiled on a different kernel?  I'm going to get a network card this weekend and update my kernel to 2.6.24-19.  I'll also upgrate to 8.041 if you think that'll help.

That'll be good for the shop, but all you need to do is to update your kernel (that'll be the 8.04.1 'automagically') and load the driver/module.

---

### Post by mpascall on 2008-07-11
I'll give it a shot once I get a working network card in it.  Hopefully this weekend.  I'll post my results.

Thanks again for your help,
-M

---

### Post by Millenium_arg on 2008-07-12
> Master Chief Re: Atheros L2 Fast Ethernet *not working*
 
--------------------------------------------------------------------------------
Ok, here is it (for 32 bit editions only) Attached you'll find a working atl2.ko module (archived). Just unpack it in to:
 
 
Code:
/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2/atl2.ko
Assuming you are in fact using the same kernel!
You can load the module with:
 
Code:
sudo modprobe atl2
 
Or unload it with:
Code:
sudo modprobe -r atl2
 
Do a DHCP request like this:
Code:
sudo dhclient ethNNote: Where N is your actual adapter (NIC) (check the MAC address to be sure in case you have more than one! 

 
 
Sorry... Not Work !
 
[COLOR=red]/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2/atl2.ko [/COLOR][COLOR=black]OK !!![/COLOR]
[COLOR=red]sudo modprobe atl2 [/COLOR][COLOR=black]OK !!! (and sudo modprobe -r atl2 also)[/COLOR]
[COLOR=red]sudo dhclient eth0 [/COLOR]Not work !!!
 
Not find DHCP
No obtain IP directión 
If I assing manually (ej) 192.168.0.200, no trafic (in/out) detected.
Using Network Tools, eth0 appears formed, but I cannot accede to its properties. It says that the card does not exist.
 
Some idea?
 
 
 
:(:(:(
 
(Sorry for my english......:frown: )

---

### Post by apelly on 2008-07-13
> **Master Chief said:**
> And here's the [COLOR="Red"]64 bit edition[/COLOR] (don't mind the amd64 in the name if you are actually using Intel like me).

**Note:** I also attached the source code!

This has been a SERIOUS pain in the ***! Solved for 8.04 with Asus motherboard P5GC-MX

Had a slightly older kernel, but your source compiled sweetly, allowing me to finally get on the 'net and install patches. 6 hours wasted by this n00b!

---

### Post by Master Chief on 2008-07-13
> **Millenium_arg said:**
> Sorry... Not Work !
 
Not find DHCP No obtain IP directión 
If I assing manually (ej) 192.168.0.200, no trafic (in/out) detected.
Using Network Tools, eth0 appears formed, but I cannot accede to its properties. It says that the card does not exist.
 
Some idea?

Let's start by getting clues as to what you are using by adding the output of:

```
uname -a
lsb_release -d
sudo lshd -C network
ifconfig
dmesg|grep atl ([COLOR="Red"]after sudo modprobe atl2[/COLOR])
```

---

### Post by inspired7 on 2008-07-13
> **Master Chief said:**
> Let's start by getting clues as to what you are using by adding the output of:

```
uname -r
lsb_release -d
sudo lshd -C network
ifconfig
dmesg|grep atl ([COLOR="Red"]after sudo modprobe atl2[/COLOR])
```

Hi I am experiencing the same problems of my wired nic saying it does not exist.

Here are the details of my configuration:

2.6.24-19-generic
Ubuntu 8.04.1

I have two Linksys LNE100TX nics in my system. Here is the ifconfig output:

eth0   Link encap:Ethernet HWaddr 00:a0:cc:32:06:ff
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:50 dropped:0 overruns:0 carrier:50
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
       Interrupt: 11 Base address:0xd400

eth1   Link encap:Ethernet HWaddr 00:a0:cc:32:07:1a
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:149 errors:58 dropped:0 overruns:0 carrier:72
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 B) TX bytes:12953 (12.6 KB)
       Interrupt: 5 Base address:0xd800

eth1:avahi Link encap:Ethernet HWaddr 00:a0:cc:32:07:1a
       inet addr:169.254.3.109 Bcast 169.254.255.255 Mask 255.255.0.0
       UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
       Interrupt: 11 Base address:0xd400

...

Running lshw -C network returns all the specs of my 2 network cards being a LNE100TX and also says I am using tulip as my driver with driver version=1.1.15

I have been searching for answers and have tried many things and have just reinstalled and still have the same problem.  I am also dual booting with windows xp and it runs both network cards with no problems.  Thanks in advance for any help.

---

### Post by chili555 on 2008-07-13
@inspired7--

Your problem has nothing to do with Atheros L2. Please start a new thread referencing LNE 100TX and tulip in the title and I'm certain you will be helped. The tulip guys aren't likely to find you here.

---

### Post by Kaesikkiya on 2008-07-14
**I've haven't been able to get your 64-bit driver working. My system has the Asus P5GC-MX/13333, 4GB RAM, a SATA DVD Burner, and a 500GB SATA Hard Drive w/WinXPSP2C dual boot. I tried compiling the source code first, couldn't get that to work, then tried the module you supplied:**

[SIZE=1] kae@Kickaha-lnx:/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2$ sudo modprobe atl2[/SIZE]
[SIZE=1] kae@Kickaha-lnx:/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2$ sudo dhclient eth0[/SIZE]
[SIZE=1] There is already a pid file /var/run/dhclient.pid with pid 5847[/SIZE]
[SIZE=1] killed old client process, removed PID file[/SIZE]
[SIZE=1] Internet Systems Consortium DHCP Client V3.0.6[/SIZE]
[SIZE=1] Copyright 2004-2007 Internet Systems Consortium.[/SIZE]
[SIZE=1] All rights reserved.[/SIZE]
[SIZE=1] For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)[/SIZE]

[SIZE=1] Listening on LPF/eth0/00:1f:c6:59:99:36[/SIZE]
[SIZE=1] Sending on   LPF/eth0/00:1f:c6:59:99:36[/SIZE]
[SIZE=1] Sending on   Socket/fallback[/SIZE]
[SIZE=1] DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4[/SIZE]
[SIZE=1] DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5[/SIZE]
[SIZE=1] DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8[/SIZE]
[SIZE=1] DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14[/SIZE]
[SIZE=1] No DHCPOFFERS received.[/SIZE]
[SIZE=1] No working leases in persistent database - sleeping.[/SIZE]
 
** At this point, I tried the connection, but failed to get anywhere. Here is the debug info you asked [B]Millenium_arg **for earlier:[/B]

[SIZE=1] kae@Kickaha-lnx:/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2$ uname -a[/SIZE]
[SIZE=1] Linux Kickaha-lnx 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux[/SIZE]
[SIZE=1] kae@Kickaha-lnx:/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2$ lsb_release -d[/SIZE]
[SIZE=1] Description:    Ubuntu 8.04.1[/SIZE]
[SIZE=1][COLOR=Red] kae@Kickaha-lnx:/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2$ sudo lshd -C network[/COLOR][/SIZE][COLOR=Red]
[/COLOR] [SIZE=1][COLOR=Red] sudo: lshd: command not found[/COLOR][/SIZE]
[SIZE=1] kae@Kickaha-lnx:/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2$ ifconfig[/SIZE]
[SIZE=1] eth0      Link encap:Ethernet  HWaddr 00:1f:c6:59:99:36  [/SIZE]
[SIZE=1]           UP BROADCAST MULTICAST  MTU:1500  Metric:1[/SIZE]
[SIZE=1]           RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/SIZE]
[SIZE=1]           TX packets:0 errors:0 dropped:0 overruns:0 carrier:1[/SIZE]
[SIZE=1]           collisions:0 txqueuelen:1000 [/SIZE]
[SIZE=1]           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/SIZE]
[SIZE=1]           Memory:dffc0000-e0000000 [/SIZE]

[SIZE=1] eth0:avahi Link encap:Ethernet  HWaddr 00:1f:c6:59:99:36  [/SIZE]
[SIZE=1]           inet addr:169.254.6.41  Bcast:169.254.255.255  Mask:255.255.0.0[/SIZE]
[SIZE=1]           UP BROADCAST MULTICAST  MTU:1500  Metric:1[/SIZE]
[SIZE=1]           Memory:dffc0000-e0000000 [/SIZE]

[SIZE=1] lo        Link encap:Local Loopback  [/SIZE]
[SIZE=1]           inet addr:127.0.0.1  Mask:255.0.0.0[/SIZE]
[SIZE=1]           inet6 addr: ::1/128 Scope:Host[/SIZE]
[SIZE=1]           UP LOOPBACK RUNNING  MTU:16436  Metric:1[/SIZE]
[SIZE=1]           RX packets:1486 errors:0 dropped:0 overruns:0 frame:0[/SIZE]
[SIZE=1]           TX packets:1486 errors:0 dropped:0 overruns:0 carrier:0[/SIZE]
[SIZE=1]           collisions:0 txqueuelen:0 [/SIZE]
[SIZE=1]           RX bytes:75468 (73.6 KB)  TX bytes:75468 (73.6 KB)[/SIZE]

[SIZE=1] kae@Kickaha-lnx:/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2$ dmesg|grep atl[/SIZE]
[SIZE=1] kae@Kickaha-lnx:/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2$[/SIZE]
  
**Any help would be greatly appreciated!**

---

### Post by Millenium_arg on 2008-07-14
[FONT=Arial][SIZE=3]**Master Chief:**[/SIZE][/FONT]
 
root@Linux-PC:~# uname -a
Linux Linux-PC 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
 
root@Linux-PC:~# lsb_release -d
Description: Ubuntu 8.04.1
 
root@Linux-PC:~# sudo lshd -C network
sudo: lshd: command not found [SIZE=3][COLOR=red]([/COLOR][COLOR=red]??????)[/COLOR][/SIZE]
 
 
 
_[SIZE=3][COLOR=red]**Before sudo modprobe atl2**[/COLOR][/SIZE]_
 
root@Linux-PC:~# ifconfig
lo Link encap:Bucle local 
[INDENT]inet dirección:127.0.0.1 Máscara:255.0.0.0
dirección inet6: ::1/128 Alcance:Anfitrión
ARRIBA LOOPBACK CORRIENDO MTU:16436 Métrica:1
RX packets:1458 errors:0 dropped:0 overruns:0 frame:0
TX packets:1458 errors:0 dropped:0 overruns:0 carrier:0
colisiones:0 txqueuelen:0 
RX bytes:76058 (74.2 KB) TX bytes:76058 (74.2 KB)
[/INDENT]root@Linux-PC:~# dmesg|grep atl
root@Linux-PC:~# 
 
 
 
_[SIZE=3][COLOR=red]**After sudo modprobe atl2**[/COLOR][/SIZE]_
 
root@Linux-PC:~# ifconfig
eth0 Link encap:Ethernet direcciónHW 00:1f:c6:04:2c:d7 
[INDENT]ARRIBA DIFUSIÓN MULTICAST MTU:1500 Métrica:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
colisiones:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Memoria:dffc0000-e0000000 
 
[/INDENT]eth0:avahi Link encap:Ethernet direcciónHW 00:1f:c6:04:2c:d7 
[INDENT]inet dirección:169.254.6.155 Difusión:169.254.255.255 Máscara:255.255.0.0
ARRIBA DIFUSIÓN MULTICAST MTU:1500 Métrica:1
Memoria:dffc0000-e0000000 
[/INDENT]lo Link encap:Bucle local 
[INDENT]inet dirección:127.0.0.1 Máscara:255.0.0.0
dirección inet6: ::1/128 Alcance:Anfitrión
ARRIBA LOOPBACK CORRIENDO MTU:16436 Métrica:1
RX packets:1450 errors:0 dropped:0 overruns:0 frame:0
TX packets:1450 errors:0 dropped:0 overruns:0 carrier:0
colisiones:0 txqueuelen:0 
RX bytes:75306 (73.5 KB) TX bytes:75306 (73.5 KB)
[/INDENT]root@Linux-PC:~# dmesg|grep atl
root@Linux-PC:~# 
 
 
 
_[SIZE=3][COLOR=red]**Forming manually the IP (192.168.15.211)**[/COLOR][/SIZE]_ 
 
root@Linux-PC:~# ifconfig
eth0 Link encap:Ethernet direcciónHW 00:1f:c6:04:2c:d7 
[INDENT]inet dirección:192.168.15.211 Difusión:192.168.15.255 Máscara:255.255.255.0
ARRIBA DIFUSIÓN MULTICAST MTU:1500 Métrica:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
colisiones:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Memoria:dffc0000-e0000000 
[/INDENT]lo Link encap:Bucle local 
[INDENT]inet dirección:127.0.0.1 Máscara:255.0.0.0
dirección inet6: ::1/128 Alcance:Anfitrión
ARRIBA LOOPBACK CORRIENDO MTU:16436 Métrica:1
RX packets:1453 errors:0 dropped:0 overruns:0 frame:0
TX packets:1453 errors:0 dropped:0 overruns:0 carrier:0
colisiones:0 txqueuelen:0 
RX bytes:75570 (73.7 KB) TX bytes:75570 (73.7 KB)
[/INDENT]root@Linux-PC:~# dmesg|grep atl
root@Linux-PC:~#

---

### Post by mpascall on 2008-07-15
> **Master Chief said:**
> but all you need to do is to update your kernel (that'll be the 8.04.1 'automagically') and load the driver/module.

Well guess what...  I downloaded the 8.04.1 CD, installed it, and it recognized my network adapter automatically and here I am on the forums.  PROBLEM SOLVED!!  :D

I didn't need to load the driver you provided.  Thanks for your help!!

-Marcus

p.s. for some reason, using the same 8.04.1 cd, doing a live boot it didn't correctly use my network adapter.  I had to install it to a hard drive first.  Strange, huh?

p.p.s. for those wondering, this is for the asus p5gc-mx motherboard's onboard lan adapter.

---

### Post by Kaesikkiya on 2008-07-15
> **mpascall said:**
> Well guess what...  I downloaded the 8.04.1 CD, installed it, and it recognized my network adapter automatically and here I am on the forums.  PROBLEM SOLVED!!...

p.s. for some reason, using the same 8.04.1 cd, doing a live boot it didn't correctly use my network adapter.  I had to install it to a hard drive first.  Strange, huh?

p.p.s. for those wondering, this is for the asus p5gc-mx motherboard's onboard lan adapter.

Funny, I think my P5GC-MX onboard lan worked from the live CD but not after installing. And I am using 8.04.1. I'll try booting from the live CD again, then maybe doing a re-install. . . Could the cd image I downloaded be different from yours?

The lan works fine when I boot to Windows.

~ Kaesikkiya

---

### Post by Master Chief on 2008-07-15
@mpascall:

Good to see you got it working. I will ask my friend to do a fresh installation on a second HD to confirm this.

@Millenium_arg:

Please don't login as root, and that command should have been:

```
sudo lshw -C network
```

Sorry for that typo.

Note: Anyone having problems compiling this driver should open a new thread and add a link here.  Thank you.

p.s. I am one of these developers with limited amount of time to spare so if anyone else is able to jump in; swell.

---

### Post by mpascall on 2008-07-16
> **Kaesikkiya said:**
> Funny, I think my P5GC-MX onboard lan worked from the live CD but not after installing. And I am using 8.04.1. I'll try booting from the live CD again, then maybe doing a re-install. . . Could the cd image I downloaded be different from yours?


Are you using the AMD64 CD?  The x86 CD is different.

I downloaded it from here: [http://releases.ubuntu.com/8.04/ubuntu-8.04.1-desktop-amd64.iso]("http://releases.ubuntu.com/8.04/ubuntu-8.04.1-desktop-amd64.iso")

-M

---

### Post by ssj4Gogeta on 2008-07-16
> **mpascall said:**
> Well guess what...  I downloaded the 8.04.1 CD, installed it, and it recognized my network adapter automatically and here I am on the forums.  PROBLEM SOLVED!!  :D

Thanks for telling that. :D I think I'll do the same. lol, I've been searching on the net for last few days how to compile and patch a driver. But none of the methods worked.

Thanks. I'll see if this works.

---

### Post by Millenium_arg on 2008-07-18
[SIZE=4]Master Chief:[/SIZE]

> @Millenium_arg:
Please don't login as root, and that command should have been:
Code:
sudo lshw -C network
Sorry for that typo.
[INDENT][COLOR=DarkRed]root@Linux-PC:~# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: a0
       serial: 00:1f:c6:04:2c:d7
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL2 driverversion=1.0.40.2 firmware=L2 latency=0 link=no module=atl2 multicast=yes port=twisted pair
  
*-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth1
       version: 10
       serial: 00:e0:7d:dc:25:21
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.15.51 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
[/COLOR][/INDENT][COLOR=Black]I'have a second NIC (Realtek), [/COLOR]in order to access internet.
[COLOR=Black]Nic  [/COLOR][COLOR=DarkRed][COLOR=Black] L2 100 Mbit Ethernet Adapter  [/COLOR][COLOR=Black]don't work

Thank you for your help

[/COLOR][/COLOR]

---

### Post by mpascall on 2008-07-19
> **mpascall said:**
> Well guess what...  I downloaded the 8.04.1 CD, installed it, and it recognized my network adapter automatically and here I am on the forums.  PROBLEM SOLVED!!  :D

Well it's not working again.  

I was enjoying Ubuntu, installing the software I needed, and then suddenly the network link light would not come on.  Same as before.  I tried the driver Master Chief compiled, but that didn't work.

I figured it was something I installed over the last few days, so I completely re-installed 8.04.1 from scratch.  Still doesn't work, which makes no sense to me.

All this time XP is having no problems.

How incredibly frustrating.  I've been enjoying Ubuntu a lot, but I just don't have time to waste on these kinds of issues.  I have work to do, and for the time being I guess I'm going to have to stick with XP.  I can't afford any more downtime.

-M

---

### Post by Master Chief on 2008-07-22
> **Millenium_arg said:**
> 
[INDENT]root@Linux-PC:~# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: a0
       serial: 00:1f:c6:04:2c:d7
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL2 driverversion=[COLOR="Red"]**1.0.40.2**[/COLOR] firmware=L2 latency=0 link=no module=atl2 multicast=yes port=twisted pair

You are using the _wrong driver_!  The correct driver version is 2.0.4 (see source tar in one of my previous posts).

---

### Post by Master Chief on 2008-07-22
> **mpascall said:**
> Well it's not working again.  

I was enjoying Ubuntu, installing the software I needed, and then suddenly the network link light would not come on.  Same as before.  I tried the driver Master Chief compiled, but that didn't work.

I figured it was something I installed over the last few days, so I completely re-installed 8.04.1 from scratch.  Still doesn't work, which makes no sense to me...

Never do a complete re-installation for small issues. Yes, it might be very frustrating, but there is always the Synaptic Package Manager's history, which can help. clue you in as to what you have been installing. You probably just forgot to check it. And I am pretty sure that it was another kernel update. All you had to do in that case is to issue another make install.

p.s. I called my friend (the one with this specific Asus board) and asked him to check for new updates to see if that kills the NIC driver (v2.0.4). I will report new findings when available!

---

### Post by Millenium_arg on 2008-07-22
[FONT=Times New Roman][SIZE=3]I installed the driver who published in this thread.[/SIZE][/FONT]
 
> 
Ok, here is it ([COLOR=red]for 32 bit editions only[/COLOR]) Attached you'll find a working atl2.ko module (archived). Just unpack it in to:
 
Code:
/lib/modules/2.6.24-19-generic/kernel/drivers/net/atl2/atl2.ko
Assuming you are in fact using the same kernel!
 
You can load the module with:
 
Code:
sudo modprobe atl2
Or unload it with:
 
Code:
sudo modprobe -r atl2
Do a DHCP request like this:
 
Code:
sudo dhclient ethN
Note: Where N is your actual adapter (NIC) (check the MAC address to be sure in case you have more than one!
Attached Files[IMG]http://ubuntuforums.org/images/attach/gz.gif[/IMG][[COLOR=#000000]atl2.ko.tar.gz[/COLOR]]("http://ubuntuforums.org/attachment.php?attachmentid=76942&d=1215557395") (212.3 KB, 31 views) 
*Last edited by Master Chief; 1 Week Ago at 08:01 PM. *

 
[FONT=Times New Roman][SIZE=3]And I can not find in any other. [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Could you tell me where is it?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Tkz !!![/SIZE][/FONT]

---

### Post by mpascall on 2008-07-22
> **Master Chief said:**
> Never do a complete re-installation for small issues. 

Well the purpose of the re-install was to instantly give me a system that I know worked with my onboard NIC: the default 8.04.1 Ubuntu install.  The fact that it's now not working for me is very confusing.  I suppose that means that the problem is not software related.

But how can I blame the hardware if XP continues to work fine?  

*shrug*

Thanks for your help.  You've been great.  But as much as I despise windows, I've wasted too much time trying to get Ubuntu working on my system and have to give up for now.

---

### Post by Master Chief on 2008-07-23
I'm currently working on a new archive which will include all source files, three diff files and two modules (one for 32bit and one for 64bit kernels).

A simple README with clear instructions will also be included, but like I said I am a busy developer so please be patient with me.

---

### Post by Johnrandom on 2008-07-25
I'm experiencing the same problems, too. I followed the instructions for amd64 carefully and even compiled atl2.ko myself. Funny thing is, that there had been an atl2 module before I even started:

lsmod | grep atl
atl2 37272 0

I unloaded the module with modprobe -r atl2, compiled the new one and moved it the position mentioned above in /lib/...
Actualy there hasn't been a atl2/ just a atl1/, so I created atl2/ and copied the freshly compiled atl2.ko to that location. Reloading the atl2 module yieldet:

lsmod | grep atl
atl2 37272 0

So, there seems to be some non-working atl2 module on the actual snapshot install CD. Replacing this module with a newer one apperantly doesn't work cause sudo dhclient fails to get an IP. Any suggestions for me?

---

### Post by NineseveN on 2008-07-25
If this is the same Atheros chip as in the Asus P5Q, then this thread put me on the right path:
[http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)


Specifically, the instructions posted by pdelahun (edited by me for clarity):

1) From a PC with a working internet connection, download the linux driver from: [http://support.asus.com/download/download.aspx?product=1&SLanguage=us-en&type=map&model=P5KPL-CM](http://support.asus.com/download/download.aspx?product=1&SLanguage=us-en&type=map&model=P5KPL-CM). Hit the "drivers" page and find the linux driver in the list of files (will download a .zip archive named LinuxDrivers.zip).

2) Inside the zip file is a .rar archive that you'll need to extract, so you'll need to be able to open .rar archives. If you're working from a Windows PC to download the driver, there are a number of applications out there to do this. If you're using a Linux PC to download the driver, then just get &#8220;unrar&#8221; (it's in the Ubuntu the repositories).

3) The .rar archive is inside the **L1e_Lan** folder (l1e-l2e-linux-v1.0.0.4.rar), you'll want to extract the contents to a folder named  **l1e-l2e-linux-v1.0.0.4** &#8211; so your newly created folder (named l1e-l2e-linux-v1.0.0.4) should contain a folder named **src** and 4 individual files (atl1e.7, copying, ldistrib.txt and readme). Make sure you put the **l1e-l2e-linux-v1.0.0.4** folder inside the **L1e_Lan** (your folder structure should look like this; **LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src**.

4) Install Ubuntu hardy (32 or 64bit), make sure you also install the build-essential package from the CD (you can do this through synaptic after choosing the CD as the source).

5) Transfer the folders from your PC with the working internet connection (where you did the work with the .rar file) via usb stick, external USB drive or whatever to the PC you installed Ubuntuu 8.04 on (you can zip the file before you transfer or just transfer the entire **Linux Driver** folder. Just put it in your /home directory.

6) Open a terminal and cd (change directory) into that folder by running: cd <HOME_DIR>/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src (where <HOME_DIR> is your home directory, i.e. /home/username/

7) run: sudo KBUILD_NOPEDANTIC=1 make

8) run: sudo KBUILD_NOPEDANTIC=1 make install

9) This should put a driver in /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/. The driver is the at1le.ko file. Keep in mind, if you are running a different kernel, the **2.6.24-16-generic** folder will be named after that kernel (i.e., mine is 2.6.24.19-generic because that's the kernel I'm running), so when you CD into the directory below, make sure you use the right kernal number for the folder name.

10) From the terminal, cd into that directory (/lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/) and run: sudo insmod ./atl1e.ko (again, since I was running a different kernel, I cd'd into /lib/modules/2.6.24-19-generic/kernel/drivers/net/atl1e/)


That's it. The driver should be up and running. Whenever you update to a new kernel, you'll have to do this all over again, but it works for now until the kernel actually supports this chip by default. To me, it's not that big of a deal, I just kept the folders with the drivers inside my home directory for later use.

---

### Post by Master Chief on 2008-07-26
> **NineseveN said:**
> If this is the same Atheros chip as in the Asus P5Q, then this thread put me on the right path:
[http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)


-> Same chip but that is the old and crippled driver.

---

### Post by NineseveN on 2008-07-26
> **Master Chief said:**
> -> Same chip but that is the old and crippled driver.

Crippled?

---

### Post by rehin on 2008-07-28
> **NineseveN said:**
> If this is the same Atheros chip as in the Asus P5Q, then this thread put me on the right path:
[http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)


Specifically, the instructions posted by pdelahun (edited by me for clarity):

1) From a PC with a working internet connection, download the linux driver from: [http://support.asus.com/download/download.aspx?product=1&SLanguage=us-en&type=map&model=P5KPL-CM](http://support.asus.com/download/download.aspx?product=1&SLanguage=us-en&type=map&model=P5KPL-CM). Hit the "drivers" page and find the linux driver in the list of files (will download a .zip archive named LinuxDrivers.zip).

2) Inside the zip file is a .rar archive that you'll need to extract, so you'll need to be able to open .rar archives. If you're working from a Windows PC to download the driver, there are a number of applications out there to do this. If you're using a Linux PC to download the driver, then just get “unrar” (it's in the Ubuntu the repositories).

3) The .rar archive is inside the **L1e_Lan** folder (l1e-l2e-linux-v1.0.0.4.rar), you'll want to extract the contents to a folder named  **l1e-l2e-linux-v1.0.0.4** – so your newly created folder (named l1e-l2e-linux-v1.0.0.4) should contain a folder named **src** and 4 individual files (atl1e.7, copying, ldistrib.txt and readme). Make sure you put the **l1e-l2e-linux-v1.0.0.4** folder inside the **L1e_Lan** (your folder structure should look like this; **LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src**.

4) Install Ubuntu hardy (32 or 64bit), make sure you also install the build-essential package from the CD (you can do this through synaptic after choosing the CD as the source).

5) Transfer the folders from your PC with the working internet connection (where you did the work with the .rar file) via usb stick, external USB drive or whatever to the PC you installed Ubuntuu 8.04 on (you can zip the file before you transfer or just transfer the entire **Linux Driver** folder. Just put it in your /home directory.

6) Open a terminal and cd (change directory) into that folder by running: cd <HOME_DIR>/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src (where <HOME_DIR> is your home directory, i.e. /home/username/

7) run: sudo KBUILD_NOPEDANTIC=1 make

8) run: sudo KBUILD_NOPEDANTIC=1 make install

9) This should put a driver in /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/. The driver is the at1le.ko file. Keep in mind, if you are running a different kernel, the **2.6.24-16-generic** folder will be named after that kernel (i.e., mine is 2.6.24.19-generic because that's the kernel I'm running), so when you CD into the directory below, make sure you use the right kernal number for the folder name.

10) From the terminal, cd into that directory (/lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/) and run: sudo insmod ./atl1e.ko (again, since I was running a different kernel, I cd'd into /lib/modules/2.6.24-19-generic/kernel/drivers/net/atl1e/)


That's it. The driver should be up and running. Whenever you update to a new kernel, you'll have to do this all over again, but it works for now until the kernel actually supports this chip by default. To me, it's not that big of a deal, I just kept the folders with the drivers inside my home directory for later use.

I have Asus P5Q mainboard and I have done all the things above. First of all thanks because it worked.

However my problem is that I have to run 'sudo insmod ./atl1e.ko' after each boot because modprobe does not recognize atl1e and gives the error: FATAL ERROR: Module atl1e not found. 

atl1e.ko file is already under the required right places like /lib/modules. Why does not modprobe recognize atl1e although insmod recognizes and loads atl1e? Please Help.](*,)

---

### Post by DeinosG on 2008-07-29
Many thanks to Master Chief for instructions.

I got the same problem with my ASUS P5GC, but solved it with his driver and tips.

Thanx again:

---

### Post by vinichc on 2008-07-31
I first install ubuntu 8.04 and didn't get install the driver, so I install ubuntu 7.10  kernel 2.6.22-14 and get install the drive correctly, using this tips. perhaps the lights of the network card doesn't turns on.
The card is working correctly in windows.

Someone knows what could be????


pS.: Motherboar Asus P5gc-mx 1333

---

### Post by agitdd99 on 2008-08-27
the first time i installed hardy 8.04 at my Asus P5GC-MX, and i have found that onboard network didn't work at all. i've tried so many times, and i gived up. I thought maybe someday it will be solved by days to come.

Then i downloaded the new release 8.04.1, and i installed it on Asus Machine again, with pre-condition : The internet connection must be connected from the start. I've realized this pre-condition when i saw the progress of ubuntu instalation, when it come to 82% numbers, it scan the repo automaticly. And that's how the attansic L2 worked from the start. It was just my prediction. maybe anyone can give you more acceptable reason for this.

I've installed 8.04.1 in my internet cafe's clients (all of them are ASUS P5GC-MX...man, i love this board! :-) ), and it works fine until now.

---

### Post by andrewkirk on 2008-09-02
Thanks heaps Master CHief. Fixed my eth0 in a jiffy. You are a dead-set legend!:)

---

