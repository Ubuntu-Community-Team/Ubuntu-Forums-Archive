---
title: "Can't connect to network after upgrading to 8.04"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by antz321 on 2008-05-04
Hi,

Using my wired network connection in 7.10 was never a problem, it worked out of the box. But now I have upgraded to 8.04, it cannot seem to connect to my home network using my wired ethernet connection. It says it is connected, yet I know it isn't because internet pages do not load and I cannot connect to my network

Any ideas? I'm fairly new to Ubuntu so please keep your replies easy to understand :)

Thanks very much

---

### Post by antz321 on 2008-05-05
Any ideas? I can't really use Ubuntu without the internet... and I'm not sure how to fix this. Thanks.

---

### Post by antz321 on 2008-05-05
Okay, I thought I might post the results of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:09:14:64  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:134 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:28637 (27.9 KB)
          Interrupt:213 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:1b:fc:09:20:46  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:214 Base address:0x4000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1b:fc:09:14:64  
          inet addr:169.254.4.115  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:213 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2545 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:130408 (127.3 KB)  TX bytes:130408 (127.3 KB)

Please help, I can't get the internet to work at all, even though it says its connected :(

Thanks.

---

### Post by koma77 on 2008-05-05
try running:

sudo dhclient

in a terminal window. 
What happens?

---

### Post by antz321 on 2008-05-05
Ok, after running sudo dhclient I get the following:

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1b:fc:09:20:46
Sending on   LPF/eth1/00:1b:fc:09:20:46
Listening on LPF/eth0/00:1b:fc:09:14:64
Sending on   LPF/eth0/00:1b:fc:09:14:64
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Iowan on 2008-05-05
I'm probably not telling you anything you don't already know: your machine is not getting IP address from DHCP server. Instead, its getting an address via avahi.  There have been several threads showing these symptoms - but I don't remember seeing a solution... yet.

---

### Post by yskchu on 2008-05-05
> **Iowan said:**
> your machine is not getting IP address from DHCP server. Instead, its getting an address via avahi.

Ignore that address from avahi; it's whats called a "link-local address", like the ones that WinXP by default give the interface if nothing is plugged in. For more info, read up (wikipedia?) on link local addresses.

It looks like you don't have a dhcp server in the environment... it's trying to do a DHCP discover over the eth0 and eth1 and nothing is being found...

Do you definately have a DHCP server and is it currently up? Check that first. Also check network connectivity between your DHCP server and your PC.

Does DHCP work from Windows? (If you have dual boot or other PCs at home)

Post more for more help.

---

### Post by antz321 on 2008-05-05
I just checked by router (Bt home hub) and DHCP is definatly enabled...

EDIT - yep just checked and DHCP is working in windows.

---

### Post by cubeist on 2008-05-05
Can you post the settings from the following two commands
```
cat /etc/resolv.conf
```
and
```
cat /etc/network/interfaces
```
Just too see if there is anything incorrect.

Also, do you have one or two network cards in your machine?

---

### Post by antz321 on 2008-05-05
When typing cat /etc/resolv.conf I get the following:

```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5672
#
### END INFO

search home


nameserver 192.168.1.254
```

cat /etc/network/interfaces

```
auto lo
iface lo inet loopback
```

My network card is built into my motherboard, its a nvidia network controller. There is only one but there are 2 ethernet ports.

---

### Post by cubeist on 2008-05-05
> **antz321 said:**
> When typing cat /etc/resolv.conf I get the following:

```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5672
#
### END INFO

search home


nameserver 192.168.1.254
```

cat /etc/network/interfaces

```
auto lo
iface lo inet loopback
```

My network card is built into my motherboard, its a nvidia network controller. There is only one but there are 2 ethernet ports.

Darn, that all looks perfect... I'll ponder it some more.

---

### Post by antz321 on 2008-05-06
Still no internet! I keep having to boot into Windows which I am really starting to hate! I doon't understand why it is doing this.... please help :(:(:(:(

---

### Post by cubeist on 2008-05-06
> **antz321 said:**
> Still no internet! I keep having to boot into Windows which I am really starting to hate! I doon't understand why it is doing this.... please help :(:(:(:(

Usually the stuff in /etc/resolv.conf is set by the NetworkManager application and is used to assign ip's and supply dns information...but something is wrong with yours. Two ideas came to me...

First, the "home" option in the search domains category may be incorrect.  For example, mine is "gateway.2wire.net" which was automatically set by my router.  My idea is for you to boot into windows and find out what windows gets for this category (sorry I don't know where that info will be in windows) and then use this information (search domains and dns servers)to populate the fields in NetworkManager.

However this may not work as there is this known bug in NetworkManager that does not save custom info and overrides with the information supplied by the router (which theoretically should be correct).  The workaround is to manually edit the dhclient.conf file (/etc/dhcp3/dhclient.conf). Which brings me to my second idea...
Can you assign yourself a static ip from your router? If so you may want to try that..

Finally, as a note of caution, if you do make changes to your dhclient.conf file make sure you backup an original copy first!

---

### Post by antz321 on 2008-05-06
> **cubeist said:**
> Usually the stuff in /etc/resolv.conf is set by the NetworkManager application and is used to assign ip's and supply dns information...but something is wrong with yours. Two ideas came to me...

First, the "home" option in the search domains category may be incorrect.  For example, mine is "gateway.2wire.net" which was automatically set by my router.  My idea is for you to boot into windows and find out what windows gets for this category (sorry I don't know where that info will be in windows) and then use this information (search domains and dns servers)to populate the fields in NetworkManager.

However this may not work as there is this known bug in NetworkManager that does not save custom info and overrides with the information supplied by the router (which theoretically should be correct).  The workaround is to manually edit the dhclient.conf file (/etc/dhcp3/dhclient.conf). Which brings me to my second idea...
Can you assign yourself a static ip from your router? If so you may want to try that..

Finally, as a note of caution, if you do make changes to your dhclient.conf file make sure you backup an original copy first!

I belive I can create a new static IP address in my router, but how do I add this into Ubuntu? As far as the rest goes, I'm not fully understanding what you mean, any help would be much apprechiated. Thanks.

---

### Post by antz321 on 2008-05-06
This is getting out of hand. I *cannot* get this to work and an operating system that won't even allow me to connect to a wired connection is hopeless. Is there a way of re installing ubuntu? sending it back to orginal settings? something? otherwise I cannot continue using it, even though since I installed Ubuntu I have hardly touched windows. :(:(

---

### Post by cubeist on 2008-05-06
> **antz321 said:**
> This is getting out of hand. I *cannot* get this to work and an operating system that won't even allow me to connect to a wired connection is hopeless. Is there a way of re installing ubuntu? sending it back to orginal settings? something? otherwise I cannot continue using it, even though since I installed Ubuntu I have hardly touched windows. :(:(

Well it did cross my mind that a clean install might do the trick. But thats a lot of effort.  Frankly I am surprised more people are not posting here.  In the last couple weeks I have seen numerous posts similar to yours that dns just doesn't work.

Did you try booting back into window to try and discover the search domains and dns server information so that you can try manually populating the fields in network manager?  Or even try configuring a custom dhclient.conf file with a static ip?

---

### Post by antz321 on 2008-05-06
> **cubeist said:**
> Well it did cross my mind that a clean install might do the trick. But thats a lot of effort.  Frankly I am surprised more people are not posting here.  In the last couple weeks I have seen numerous posts similar to yours that dns just doesn't work.

Did you try booting back into window to try and discover the search domains and dns server information so that you can try manually populating the fields in network manager?  Or even try configuring a custom dhclient.conf file with a static ip?

I'm going to boot up into the live CD tomorrow and see what happens. If the internet works, I will just install that. I will let you know how it goes. But thats a task for tomorrow as I don't have enough time to be downloading the ISO. Thanks for the help though. :)

---

### Post by cubeist on 2008-05-06
> **antz321 said:**
> I'm going to boot up into the live CD tomorrow and see what happens.(...)

Gee, that's a good idea! A simple yet effective determinate on whether Ubuntu will give you internet!

---

### Post by moyofalaye on 2008-05-06
I too am having the same problem. I also tired all the check commands above in terminal, and my results are the same. I have also tried the live cd. 
And i still cant connect to the internet (wired) i dont use wireless on my pc.

Also everything worked fine, when i was using ubuntu 7.10

Im suspecting it has something to to with the nvidia mcp (if thats what they call it, no time to check it) I mean those that there motherboards come with 2 ethernet ports are having these problems.

Pleas anyone out there that has gotten theres to work, please help. Just help please.

---

### Post by cubeist on 2008-05-07
> **moyofalaye said:**
> I too am having the same problem. I also tired all the check commands above in terminal, and my results are the same. I have also tried the live cd. 
And i still cant connect to the internet (wired) i dont use wireless on my pc.

Also everything worked fine, when i was using ubuntu 7.10

Im suspecting it has something to to with the nvidia mcp (if thats what they call it, no time to check it) I mean those that there motherboards come with 2 ethernet ports are having these problems.

Pleas anyone out there that has gotten theres to work, please help. Just help please.

I thought of this during another post with a similar problems, but I have no idea if it will work.  It seems really simple... why not just specifically tell the computer what to use... I think this is the point of the dhclient.conf file (/etc/dhcp3/dhclient.conf)

Technically, there should be no need to edit this file, but if you backup a copy first, this gives you a lot of networking options... for example you can set which eth to use. (ie, eth0 or eth1)

Anyway, there is a ton of reading in man dhclient.conf

It might be a good place to start... and please, anyone with more networking knowledge than I (which is most people :) ), please chime in!

---

### Post by illu45 on 2008-05-07
I'm having a similar problem. I can connect to my wireless network and have internet fine for a while, but then the network settings mess up (go to WPA instead of WPA2) and I have to change them and reboot. Usually, this only happens about once or twice a day, after long periods of non-use. Still, it does get to being rather annoying.

---

### Post by antz321 on 2008-05-07
> **cubeist said:**
> I thought of this during another post with a similar problems, but I have no idea if it will work.  It seems really simple... why not just specifically tell the computer what to use... I think this is the point of the dhclient.conf file (/etc/dhcp3/dhclient.conf)

Technically, there should be no need to edit this file, but if you backup a copy first, this gives you a lot of networking options... for example you can set which eth to use. (ie, eth0 or eth1)

Anyway, there is a ton of reading in man dhclient.conf

It might be a good place to start... and please, anyone with more networking knowledge than I (which is most people :) ), please chime in!

Well this is the latest. I tried booting into the 8.04 live CD, worked fine... but still no internet! So it must be something to do with 8.04. I had a look in that dhclient.conf, but its already set to eth0 and im not really sure what the rest of it does. Also, it won't let me save on the account I need permissions or something. So im stumped, and still no internet with Ubuntu :(

---

### Post by sportman1280 on 2008-05-07
I am having the same issue.  Only one specific router is giving the issues.  It works great at my apartment but not at all at my moms.  As stated.  It is something to do with the DHCP.  IP address just never gets assigned!

Other forum topics...
[http://ubuntuforums.org/showthread.php?t=783447](http://ubuntuforums.org/showthread.php?t=783447)
[http://ubuntuforums.org/showthread.php?t=777185](http://ubuntuforums.org/showthread.php?t=777185)

---

### Post by upthelum on 2008-05-07
> **antz321 said:**
> Well this is the latest. I tried booting into the 8.04 live CD, worked fine... but still no internet! So it must be something to do with 8.04. I had a look in that dhclient.conf, but its already set to eth0 and im not really sure what the rest of it does. Also, it won't let me save on the account I need permissions or something. So im stumped, and still no internet with Ubuntu :(

The problem isn't with your 8.04 or the bt home hub, i use one and i got online with Hardy no problem. I'm unfortunately in windows but will post some file outputs when back in Linux. You could try assigning an IP address manually, use the 1.64 address as your gateway and dns servers but if that doesn't work set it back to auto dhcp.

---

### Post by tbielawa on 2008-05-07
> **sportman1280 said:**
> I am having the same issue.  Only one specific router is giving the issues.  It works great at my apartment but not at all at my moms.  As stated.  It is something to do with the DHCP.  IP address just never gets assigned!

Other forum topics...
[http://ubuntuforums.org/showthread.php?t=783447](http://ubuntuforums.org/showthread.php?t=783447)
[http://ubuntuforums.org/showthread.php?t=777185](http://ubuntuforums.org/showthread.php?t=777185)

That's the exact same issue I've been having. The two APs around my home work perfectly, but there is one in a business elsewhere that it refuses to connect to anymore. 

There's a bug report on LP [https://bugs.launchpad.net/ubuntu/+bug/220445](https://bugs.launchpad.net/ubuntu/+bug/220445) where people can make a mark if they're having the same issue

---

### Post by sportman1280 on 2008-05-07
Its got to be 8.04 settings, somewhere.  it worked before 8.04.

Please add details to the bug report!
[https://bugs.launchpad.net/ubuntu/+bug/220445](https://bugs.launchpad.net/ubuntu/+bug/220445)

---

### Post by him610 on 2008-05-07
> **cubeist said:**
> Darn, that all looks perfect... I'll ponder it some more.
I believe the two lines in your interfaces file are out of order. After making a backup copy of your interfaces, you might want to try editing your interfaces file (as sudo) to read

Code:
iface eth0 inet dhcp

auto eth0

Code_end

Good luck.

---

### Post by antz321 on 2008-05-07
> **hgh9mrp said:**
> I believe the two lines in your interfaces file are out of order. After making a backup copy of your interfaces, you might want to try editing your interfaces file (as sudo) to read

Code:
iface eth0 inet dhcp

auto eth0

Code_end

Good luck.

Tried that, didn't work.

---

### Post by him610 on 2008-05-07
Ok, how about this one for your interfaces file?

```

auto lo
iface lo inet loopback



iface eth0 inet dhcp



auto eth0


```

---

### Post by shazbut on 2008-05-07
I had a similar problem with 8.04, happened when using network manager to change from dynamic to static IP, though.  What happened was that although I specified a gateway address in network manager, it was not installing it as the default route.
What happens when you type **route** in terminal?
Should have a line at the bottom similar to:
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
If not you could try adding it with:
route add default gw X.X.X.X
(where X.X.X.X is your router address)

---

### Post by Joor on 2008-05-08
Same problem here, cant connect to the internet after installing 8.0.4 :(

---

### Post by illu45 on 2008-05-08
> **shazbut said:**
> I had a similar problem with 8.04, happened when using network manager to change from dynamic to static IP, though.  What happened was that although I specified a gateway address in network manager, it was not installing it as the default route.
What happens when you type **route** in terminal?
Should have a line at the bottom similar to:
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
If not you could try adding it with:
route add default gw X.X.X.X
(where X.X.X.X is your router address)

I will give that a try next time it cuts out, thanks!

---

### Post by sportman1280 on 2008-05-09
didnt work for me.

Also.  i noticed that on one of the machines... the MAC comes up with -00-00-00-00-00-00-00-00 at the end of a legal MAC address... not sure why.  The other 2 computers having issues with the router are not having the MAC address issue.

---

### Post by moyofalaye on 2008-05-12
For those that have not gotten it to work, "its actually a bug in ubunutu 8.0"

Here is the fix i cant remember where i got it from. 

```
 
$ sudo su
# rmmod forcedeth
# modprobe forcedeth msi=0 msix=0
# /etc/init.d/networking restart

```

And to make the fix permanent or should i say at boot time
do the following

To set this as a startup type script thingy...

```

Run gedit or kwrite as root and open /etc/rc.local
Atl+F2 -> gksu gedit /etc/rc.local on ubuntu
Run -> kdesu kwrite /etc/rc.local on kubuntu

Paste the lines between the comment lines and exit0.
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart


```

Oh i found the fix from [_here_]("http://ubuntuforums.org/showthread.php?t=766629&highlight=hardy+wired+ethernet+not+working&page=2")

---

### Post by chrisb62 on 2009-01-05
well i found a solution to this on my laptop at least.

i had this same problem with ubuntu 7.40 i think it was.

add:

"blacklist hostap_cs" to the /etc/modprobe.d/blacklist file - (without the quotes)

reboot, problem solved.



after doing a fresh install of 8.04, the internet worked fine so i figured they fixed whatever bug that was. so i did all the upgrades, came back and no internet.

so i thought, well i guess it doesnt hurt to try what i did before, and whataya know, it worked.

im know linux expert, very newb to be honest. not sure where i found that option to try, just after tons of searching on the net. got lucky i guess.

dunno if it will work for others but thought its worth a shot.

i have an old compaq laptop with a pcmcia linksys wireless card, if you are curious

---

