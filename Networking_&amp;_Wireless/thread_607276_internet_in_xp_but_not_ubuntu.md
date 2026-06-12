---
title: "internet in xp but not ubuntu"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by XRichX on 2007-11-08
Did a wee search but couldn't find any topic on this matter so thought i'd better post it up. I have been using Ubuntu 7.04 along with XP for quite sometime now, it worked brilliantly. Although the internet stopped working in Ubuntu, for no reason what so ever. When you view the connection status all connection info is on 0 (see screenshot) and if you go into XP it works perfectly.

Ubuntu:

[img]http://www.traygon.com/myimages/internetproblem.png[/img]

XP:

[img]http://www.traygon.com/myimages/internetinxp.GIF[/img]

I thought it could be my Ubuntu so i uninstalled it and booted from Live disk just to check if it would work using live CD, no luck it just wouldn't work. By the way, the connection in Ubuntu actually states 'connection established' but theres no connection.

I waited until Ubuntu 7.10 came out to get a Live CD to try it out, it worked the first time i put the Live CD in and i browsed the internet and was all happy. Installed it, then rebooted, when i logge dinto Ubuntu.. yup it happened... the internet doesn't work. I booted into XP and wow! It works. I haven't the foggiest clue in a ll of clue land as to why it wont pick up the connection. It isn't the internet or router as it works in XP and i have used this internet in Ubuntu 7.04 for about 3 months.

Any ideas?

Oh and here is the result from ifconfig in terminal, i also can't ping any website or even my router so theres deffinately a problem within Ubuntu.

```
eth0      Link encap:Ethernet  HWaddr 00:13:8F:BA:B9:2F  
          inet6 addr: fe80::213:8fff:feba:b92f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xac00 

eth0:avah Link encap:Ethernet  HWaddr 00:13:8F:BA:B9:2F  
          inet addr:169.254.7.47  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:440 (440.0 b)  TX bytes:440 (440.0 b)

```

 have noticed this within the result from ifconfig:

eth0:avah Link encap:Ethernet  HWaddr 00:13:8F:BA:B9:2F  
          inet addr:**169.254.7.47**  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xac00 

Isnt the bold part supposed to be my router IP?

thanks guys!

XRichX

---

### Post by mpierce on 2007-11-08
Obviously, you have not connection and the  eth0:avah is a default phantom that it setups when it can't find a connection. First thing look at your /etc/network/interface file:
   sudo vi /etc/network/interface

Since you are using a LAN, you should have something in it like this:

auto eth0
iface eth0 inet dhcp

This will enable it to startup automatically and use your ISP to get it's dhcp settings. 

You will then need to restart your network with:
sudo /etc/init.d/networking restart

You can always set up the eth0 to use manual parameters from your ISP but if possible you should use auto.

Hope this helps...

---

### Post by XRichX on 2007-11-08
Hello and thankyou for you're tiem and help :)

I ran sudo vi /etc/network/interface in the terminal and it brought up a load of

```
-
-
-
-
-
-
-
-
-
-
```

No sign of:

auto eth0
iface eth0 inet dhcp

so i took the liberty of adding it in, restarted the network and it doesn't work still. It restarted the network using etho0 but still no connection, although firefox was actually looking up google.co.uk before displaying error, unlike before.

thanks

XRichX

---

### Post by mpierce on 2007-11-08
Give me the output of:
   cat /etc/network/interfaces and
   ifconfig -a

BTW, what are you using ubuntu or kubuntu?

---

### Post by XRichX on 2007-11-08
Ubuntu 7.10

Result for cat /etc/network/interfaces:

```
auto lo
iface lo inet loopback




iface eth0 inet dhcp

auto eth0
```

result for ifconfig -a:

```
eth0      Link encap:Ethernet  HWaddr 00:13:8F:BA:B9:2F  
          inet6 addr: fe80::213:8fff:feba:b92f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xac00 

eth0:avah Link encap:Ethernet  HWaddr 00:13:8F:BA:B9:2F  
          inet addr:169.254.7.47  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1408 (1.3 KB)  TX bytes:1408 (1.3 KB)
```

---

### Post by elctb on 2007-11-08
Try this:

sudo ifconfig eth0 down
sudo dhclient eth0

and then show the output of:
ifconfig eth0

---

### Post by XRichX on 2007-11-08
> **elctb said:**
> Try this:

sudo ifconfig eth0 down
sudo dhclient eth0

Sorry, where do i add that?

---

### Post by mpierce on 2007-11-08
Run the commands from a terminal.

---

### Post by elctb on 2007-11-08
From a terminal window.

Look in your menu (probably under applications) for the "Terminal" application. Then type the commands on the window that pops up.

When you use sudo to run a command, it will ask you to enter your password,

---

### Post by XRichX on 2007-11-08
oh aye i know bout that lol just got a bit confused. right i ran both commands and got the output for you both:

```
eth0      Link encap:Ethernet  HWaddr 00:13:8F:BA:B9:2F  
          inet6 addr: fe80::213:8fff:feba:b92f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xac00 
```

---

### Post by mpierce on 2007-11-08
Are you using a router or a modem and can you tell us what the output of is:
   dpkg -l | grep dhcp

---

### Post by XRichX on 2007-11-08
m using Orange Livebox, which does work with Ubuntu etc.

Here is that output:

```
  dhcp3-client                               3.0.5-3ubuntu4               DHCP client
ii  dhcp3-common                               3.0.5-3ubuntu4               common files used by all the dhcp3* packages


```

---

### Post by elctb on 2007-11-08
If you're using your home router, assign a static ip address to eth0 and verify you can connect to the router. Use the ip address xp got:
sudo ifconfig eth0 192.168.1.141 netmask 255.255.255.0

Then ping the router
ping 192.168.1.1

If the ping success, do the following again:

reset the router (physically power it down and up)
sudo ifconfig eth0 down
sudo dhclient eth0

But this time show the output of the dhclient command.

---

### Post by mpierce on 2007-11-08
From terminal:
   sudo ifdown eth0
   sudo ifup eth0
   sudo /etc/init.d/networking restart

Are you using a modem or a router?

---

### Post by XRichX on 2007-11-09
elctb: i don't know how to configure a static address on this router, i do on my old one but it keeps cutting out so i don't use it no more.

mpierce: did what you said again but still no joy, i am using a router, i have my PC wired up to it manually (im using my PC now on XP to type this) and i have my dad's PC using a wireless USB on Windows XP and they both run fine, it is just Ubuntu that just doesn't like anything to do with the term 'network'.

---

### Post by elctb on 2007-11-09
> **XRichX said:**
> elctb: i don't know how to configure a static address on this router, i do on my old one but it keeps cutting out so i don't use it no more.

Type the following from a teminal window:
sudo ifconfig eth0 192.168.1.141 netmask 255.255.255.0

and then try to ping the router using this command:
ping 192.168.1.1

---

### Post by XRichX on 2007-11-09
thankyou for you're continued support in this matter.

I carried out that command and tried to ping my router but it just kept saying it was unreachable. This is really confusing me as i have no clue to what could be stopping the internet from connecting.

---

### Post by elctb on 2007-11-09
Post the output of the commands:
netstat -rn
ifconfig
ifconfig -a

---

### Post by Sanity N/A on 2007-11-09
looks pretty much as this one
[http://ubuntuforums.org/showthread.php?t=607947](http://ubuntuforums.org/showthread.php?t=607947)
theres even a possible solution if i just knew how to try it out

---

### Post by rpinwelly on 2007-11-10
Hi all,

I have a very similar problem.  I'm a linux newbie, by the way.  Installed Ubuntu 7.04 a week ago on a new machine with a dual-boot configuration (xp on one disk, Linux on the other).  My machine connects directly to the net via the onboard Gigabyte card of my motherboard (Asus P5KE).  No other computers are connected to this machine.

Installation went well; I configured my network for the static IP address of my ISP (broadband via cable modem), added IPs for gateway and DNS, rebooted and had a functioning internet connection.  Downloaded various updates, installed automatix and a few other things.

Yesterday, I tried to install the drivers for my NVidia 8800GTX; and somehow, while I was doing that, I lost the connection to the internet.  Haven't been able to get it back since then. Internet via xp works perfectly (well, I wouldn't be posting here otherwise ...)

Today, I did a clean re-install of 7.04 (from the ISO disk); configured my network exactly the same way, but no luck.  I also tried using a live CD of 7.10 but could not establish a connection either (but it DOES recognise my 8800 GTX :)

I did run ifconfig in the terminal; can't paste the full output in here (since I had to reboot into xp, so of course my clipboard contents get lost ...), but it showed essentially a block of text for "eth1", a hardware address, but no IP address or gateway, and a block of text for "lo"

I tried out the suggestions made in this thread (and elsewhere, mostly involving stuff like "sudo ifdown eth1", networking restart etc (but to be truthful, I don't really know what I'm doing with that ...), but had no success.

I also tried "route add default gw 203.97.239.1" (this is the gateway of my ISP) but that made no difference either.

I can ping 127.0.0.1 successfully, but not any other IP address.
 
One other thing I noticed is that when I look up the hardware information under Preferences (in 7.04), most of the devices (apart from the hard disks) are "unknown"; the live disk of 7.10 on the other hand identifies all devices (including the Gigabit ethernet card) correctly.

So, I am stuck!!  Any help with this would be very much appreciated. :)  

Thanks in advance!

---

### Post by mpierce on 2007-11-10
I had to go away and I see that you still haven't resolved problem.

So, let's try something different for the minute. 

1) Can you connect to internet using the live CD?  If so, boot it and copy down the settings that it is using in all the config files that we have had you try to modify, e.g.,
   /etc/network/interfaces
  /etc/dhcp/dhcp.conf

Post these so we can take a lot at what it is using. In addition, post the output of ifconfig:
  ifconfig > ifconfig.txt
  vi ifconfig.txt (to see contents in terminal)

We are still here trying to help you!

---

### Post by rpinwelly on 2007-11-10
further to my previous post:

after having run "route add default gw" etc, ifconfig now shows the gateway as an address for eth1; still no connection, though.

I also ran a traceroute to my gateway 203.97.239.1 and got the following otuput:

hop     hostname        IP                                       time 1
1        rp-1.local         203.97.239.113                 0.061ms
1        no                    reply                                   *
1       rp-1.local          203.97.239.113                 2004.001ms

The iP address above is my static IP assigned by my ISP ... so something is happening, but not quite enough to get me out to the internet ...

(Minor correction to my post above: 7.04 reports most devices as unknown, but does in fact recognise the Gigabyte  ethernet card)

Cheers, and thanks for any suggestions.

---

### Post by mpierce on 2007-11-10
Let's try putting info in your /etc/network/interfaces files and see what happens. Make a backup of the current file before you edit it:
  cd /etc/network
  sudo cp interfaces interfaces.original
  sudo vi interfaces

auto eth0
iface eth0 inet static
   onboot=yes
   netmask=255.255.255.0
   ipaddr=203.97.239.113
   gateway=203.97.239.1
   dns-nameservers=208.67.222.222 208.67.220.220

The dns-nameservers are open. You can use your ISP's as the 1st or 2nd one if you want

---

### Post by rpinwelly on 2007-11-10
MPIERCE,

thanks for your help; :)  okay, I've added the "onboot=yes" and "dns-nameserver" lines to the  interfaces file, and now it looks as follows:


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
onboot=yes
address 203.97.239.113
netmask 255.255.255.0
gateway 203.97.239.1
dns-nameservers=203.96.152.4 203.96.152.12

auto eth1
iface eth1 
inet static
address 203.97.239.113
netmask 255.255.255.0
gateway 203.97.239.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

I rebooted but got no connection.  I then ran ifconfig and got the following output:

root@rp-1:~# ifconfig
eth1      Link encap:Ethernet  HWaddr 0A:64:68:E3:7A:71  
          inet6 addr: fe80::864:68ff:fee3:7a71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94099 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:5646820 (5.3 MiB)  TX bytes:468 (468.0 b)

root@rp-1:~# 

(Note: I logged on as root to make those edits with "gedit"; I understand this is bad practice, but I was having great difficulties editing the file with "sudo vi"; hard to control the cursor, the arrow keys, insert, deleted, backspace keys etc all produced fairly unpredictable results)  

Anyway, I then tried to run some of the network tools, but could now not even ping my local host 127.0.0.1  (send failed).

If I interpret what you've told me to do correctly, we've tried to configure the interface eth0 at boot to connect to the network card; however, the ifconfig does not show eth0 at all: it only gives us eth1.  Is that where the problem could lie?

Thanks again for your help!

---

### Post by rpinwelly on 2007-11-10
while I'm here ... since there doesn't appear to be an easy quick fix for restoring the internet access which I had in 7.04, and since the live CD for 7.10 has the same problem, do you think I might as well just make a clean install of 7.10 now and we fix the problem there? Otherwise, I may ahve to go through all this again when I upgrade to 7.10.  Are there any disadvantages or known major bugs with 7.10?

---

### Post by rpinwelly on 2007-11-12
Solved ... hopefully, until further notice anyway :-)

I did a clean install of 7.10; while the live disc did not give me internet access, the installed version now does.  I haven't tried to re-boot yet - I fear I might loose the connection; maybe tomorrow when I'm feeling a bit more courageous.

ifconfig putput now shows:

rp@rp-1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:60:18:9A:F2  
          inet addr:203.97.239.113  Bcast:203.97.239.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fe18:9af2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:811588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19530 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:87180651 (83.1 MB)  TX bytes:1664343 (1.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


I wonder whether the problem has something to do with Ubuntu having difficulty recognising my network adapter; I have an Asus 5PK-SE with an onboard Attansic L1 gigabit adapter and I read in another thread that Attansic dirvers might be a problem.  The mobo comes with a disk which includes Linux drivers - however, the installation instructions are sadly way beyond my current (noobie) Linux capabilities.  I'm on a steep bendy educational thingie here :)

---

### Post by rpinwelly on 2007-11-13
Looks like the installation of 7.10 has definitely solved the problem. :-)  Connection running for two days now, and has survived rebooting as well as booting into xp.  

7.10 (kernel 2.6.22.14 - generic) evidently now recognises the Attansic L1 ethernet adapter (onboard Asus P5K-SE); there was no need to install drivers from the Asus disk.  Also no problem with the video card (8800GTX).

Now if only I could get my Canon MF8180C to print ... but from what I have read in the forums, that is a hopeless endeavour; will have to buy a new printer.

---

