---
title: "No wired connection after upgrade"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by hofa on 2008-10-30
I just upgraded to Ibex Intrepid and my wired connection isn't working anymore.

when I put it in manually in /etc/network/interfaces, it gives me an error when I restart /etc/init.d/networking (I can't remember which error, I'm on Windows now)

When I try to do it with ifconfig
```
sudo ifconfig eth0 192.168.1.2
OR
sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0
```

it gives me the following error:
```
SIOCSIFADDR: No buffer space available
```

I am using a Dell XPS 1710 laptop with a Broadcom NetXtreme 57xx Gigabit Controller

Can anyone please help

---

### Post by hofa on 2008-10-30
bump?

---

### Post by phaZe~collapse on 2008-10-30
i am having the same problem on my router.  the wireless connection works ok, but when i plug in the wire the network manager just goes stupid.  the bug was filed here [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/277063](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/277063) as 'fixed' prior to 8.10 official release, however i am having this problem after just upgrading today.

---

### Post by hofa on 2008-10-31
Mine is a bit different.

I just can't set an IP address, not even manually. I put my backup back now and using good ol' hardy. I'm waiting for the cd to be delivered to attempt a clean install.

---

### Post by dwende on 2008-10-31
Same problem.

Internet upgrade from 8.04 to 8.10 seemed to run smoothly.

On reboot into 8.10 now have NO wired ethernet connection.

My router supports dhcp, but 8.10 fails to get an address from it.

Using the skge network card driver (used to work flawlessly
with 8.04).

---

### Post by hofa on 2008-10-31
what about static settings?

---

### Post by dwende on 2008-10-31
Hi Hofa

The command line command:
> sudo ifconfig eth0 10.0.0.5
also produces the result
> No buffer space available.

Using the graphical Network Connections setup, if I choose
under IPv4 settings "manual" instead of Automatic DHCP and
enter the IP that the DHCP server *would have assigned*, then
the notification is "wired network connection established" - but
I still can't ping the router.

My **guess **is that lots of other people are seeing the same problem.

---

### Post by hofa on 2008-10-31
I reported this bug on it's own: [https://bugs.launchpad.net/ubuntu/+bug/291449](https://bugs.launchpad.net/ubuntu/+bug/291449)

---

### Post by Absorbed on 2008-10-31
I think I've got the same problem, with the "SIOCSIFADDR: No buffer space available" message. I've made a thread here: [http://ubuntuforums.org/showthread.php?t=964757](http://ubuntuforums.org/showthread.php?t=964757)

---

### Post by oferfrid on 2008-10-31
same here with Asus motherboard M2n, network is just broken.

static is not working too.

---

### Post by panosdotk on 2008-10-31
After my upgrade from 8.04 to 8.10 my wired connection was down. I connect to my access point but i don't have internet access. I can't change my IP and the eth0 (ifupdown is the connection name) show as unmanaged to Network Manager Applet.

My connection works fine after I make this change:

Edit file /etc/NetworkManager/nm-system-settings.conf

and under [ifupdown] section

change value managed=false to true

Hope this help

---

### Post by Neolit on 2008-10-31
> **oferfrid said:**
> same here with Asus motherboard M2n, network is just broken.

static is not working too.

Same problem with an HP laptop.

---

### Post by Absorbed on 2008-10-31
> **panosdotk said:**
> After my upgrade from 8.04 to 8.10 my wired connection was down. I connect to my access point but i don't have internet access. I can't change my IP and the eth0 (ifupdown is the connection name) show as unmanaged to Network Manager Applet.

My connection works fine after I make this change:

Edit file /etc/NetworkManager/nm-system-settings.conf

and under [ifupdown] section

change value managed=false to true

Hope this help

I tried changing it to true and then rebooting, and then tinkering with a static IP, ifconfig, etc., but it didn't make any difference.

---

### Post by oferfrid on 2008-10-31
> **panosdotk said:**
> After my upgrade from 8.04 to 8.10 my wired connection was down. I connect to my access point but i don't have internet access. I can't change my IP and the eth0 (ifupdown is the connection name) show as unmanaged to Network Manager Applet.

My connection works fine after I make this change:

Edit file /etc/NetworkManager/nm-system-settings.conf

and under [ifupdown] section

change value managed=false to true

Hope this help

Not working for me... 
anyone?

---

### Post by DE Retiree on 2008-10-31
> **hofa said:**
> I just upgraded to Ibex Intrepid and my wired connection isn't working anymore. (snip)

I am using a Dell XPS 1710 laptop with a Broadcom NetXtreme 57xx Gigabit Controller

Can anyone please help

Same here.  8.04 networking worked fine.  8.10 does not and everything I've tried in the "networking" preferences GUI does not seem to help.  I'm also using the Broadcom NetStreme 57xx Gigabit Controller but on a Dell 8400 desktop.  I'm trying to run 8.10 from the Live CD before doing an install.  The suggestions mentioned so far in this post have not helped me either.  I'm still quite a linux novice so be gentle with any replies.  Thanks.

---

### Post by oferfrid on 2008-10-31
> **DE Retiree said:**
> Same here.  8.04 networking worked fine.  8.10 does not and everything I've tried in the "networking" preferences GUI does not seem to help.  I'm also using the Broadcom NetStreme 57xx Gigabit Controller but on a Dell 8400 desktop.  I'm trying to run 8.10 from the Live CD before doing an install.  The suggestions mentioned so far in this post have not helped me either.  I'm still quite a linux novice so be gentle with any replies.  Thanks.

Tried LiveCD, didn't work for me (Asus motherboard).

---

### Post by zenkaon on 2008-10-31
same problem here, just upgraded - no wired connection.

Using a Dell Latitude D420.

However doing:
```
sudo dhclient eth0
```
will get things working

---

### Post by stankopp on 2008-10-31
The static IP addressing does not work either.  This is the same problem that we had with the 8.10 beta.  It exhibits the same exact behaviour as the beta. (Enter IP address 1.1.8.52, mask 255.0.0.0, gateway 1.1.1.88 and all that is retained is the 1.1.8.52, the mask goes to 8 and gateway to 0.0.0.0).  I have tried all of the editing of network config files (in the beta) without any success. I had hoped the IP addressing issues would be addressed in the final realease, but they have not not.  What is the point of testing if the problems are not going to be addressed?  Not all of us have wireless capability.  Intrepid Ibex is pretty much worthless as it sits.  I can not even go to the internet for a possible fix...

---

### Post by Absorbed on 2008-10-31
> **zenkaon said:**
> same problem here, just upgraded - no wired connection.

Using a Dell Latitude D420.

However doing:
```
sudo dhclient eth0
```
will get things working

I tried this and got the following:
```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No buffer space available
Listening on LPF/eth0/00:0d:87:f3:9c:b5
Sending on   LPF/eth0/00:0d:87:f3:9c:b5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Message too long
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

As far as I can tell nothing has changed afterwards.

I also noticed this bug report, which appears to be the same problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284377](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284377)

I noticed that if I do "sudo /etc/init.d/NetworkManager restart" I get the same thing as the above bug report:
```
[ 1031.164948] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1031.168135] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 1031.168238] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
```

I've no idea how relevant that is, but I figure that more information is better than less.

---

### Post by giancarlo76 on 2008-10-31
```
# sudo dhclient eth0
```
doesn't work for me (SIOCSIFADDR: No buffer space available), with an ASUS MoBo (forcedeth driver).

---

### Post by truongan on 2008-10-31
I have that trouble too.
So far so bad for me. I recall that in ubuntu 8.04, things went fine, sound, vesa vga, network etc... but now, they are just... trash.

Somehow, Ubuntu 8.10 wiped out my Fedora partition, although I had double check that I didn't touch that partition.

The goodness of 8.04 make me decides to give 8.10 a try while I was happy with my Fedora. And now I'm regretting that decision.

---

### Post by Obfuscator on 2008-10-31
I had to stop NetworkManager (sudo /etc/init.d/NetworkManager stop), delete my old /etc/network/interfaces (rename it), then restart NetworkManager. That worked, but I am still to figure out how to tell NetworkManager which interfaces to manage through the very cryptic GUI... This was not a pleasant upgrade. Really annoying when networking goes down and you don't know why or how to fix it, one would think that the upgrade process would ask you to remove /etc/network/interfaces before restart.

---

### Post by oferfrid on 2008-10-31
can you describe the solution in more details please 
so far it's not working for me.

the problem sexist for me using the live cd too, I'll be surprised if it have anything with the upgrade.

---

### Post by JFo NZ on 2008-10-31
This is how I've fixed the problem.

Edit /etc/network/interfaces

Add 2 new lines:

auto eth0
iface eth0 inet dhcp

Then restart machine. Fixed.

[I]Command to edit file:
sudo gedit /etc/network/interfaces[/I]

---

### Post by JasonDavies on 2008-10-31
My workaround for this problem is as follows:

1. Disable NetworkManager from starting up:

```
$ sudo update-rc.d -f NetworkManager remove
```

2. Reboot

3. Manually set up eth0 using ifconfig and route:

```
$ ifconfig eth0 10.0.0.10
$ route add default gw 10.0.0.2

```

4. Edit /etc/resolv.conf:

```
$ echo "10.0.0.2" >> /etc/resolv.conf
```

The exact IP addresses will be different for your individual setups, of course.  You might want to try running ```
dhclient eth0
``` instead of step 3.

---

### Post by oferfrid on 2008-10-31
how to rollback 
> $ sudo update-rc.d -f NetworkManager remove

---

### Post by pico on 2008-10-31
> **JFo NZ said:**
> This is how I've fixed the problem.

Edit /etc/network/interfaces

Add 2 new lines:

auto eth0
iface eth0 inet dhcp

Then restart machine. Fixed.

[I]Command to edit file:
sudo gedit /etc/network/interfaces[/I]

This steps does not work for me !

Any idea ??

---

### Post by Absorbed on 2008-10-31
> **JasonDavies said:**
> My workaround for this problem is as follows:

1. Disable NetworkManager from starting up:

```
$ sudo update-rc.d -f NetworkManager remove
```

2. Reboot

3. Manually set up eth0 using ifconfig and route:

```
$ ifconfig eth0 10.0.0.10
$ route add default gw 10.0.0.2

```

4. Edit /etc/resolv.conf:

```
$ echo "10.0.0.2" >> /etc/resolv.conf
```

The exact IP addresses will be different for your individual setups, of course.  You might want to try running ```
dhclient eth0
``` instead of step 3.

That's solved it for me. Thanks bestowed upon you.

---

### Post by gryzzly on 2008-10-31
> **oferfrid said:**
> how to rollback

Hi, I also completed these steps (update-rc.d -f NetworkManager remove)

And I would also like to know how to rollback (it didn't help so far)

Thanks.

---

### Post by JasonDavies on 2008-10-31
> **oferfrid said:**
> how to rollback

To reinstate NetworkManager's startup and shutdown links, do:

```
$ sudo update-rc.d NetworkManager defaults
```

---

### Post by river2884 on 2008-10-31
please advise this upgrade does not work with networking.

This is a horrible, horrible upgrade.

---

### Post by mundo on 2008-11-01
No wired or wireless connection for me either after upgrading although Mobile Broadband works OK.

---

### Post by truongan on 2008-11-01
Your method work for me, gryzzly! After disable Network Manager ifconfig run just fine, it stop yelling at me about the "No buffer space available" stuff.

---

### Post by billd42 on 2008-11-01
> **JasonDavies said:**
> My workaround for this problem is as follows:

yeah, this worked for me!  Thanks a whole bunch.

This upgrade (Hardy -> Intrepid) mostly worked for me, except, man, what a showstopper of a networking bug.  I'm not sure how that Network Manager got out of the barn.

---

### Post by pico on 2008-11-01
Works also for me !
THX

But...
if the problem is the latest version of NetworkManager (with latest kernel I suppose) Is not possible to downgrade the single package (Network manager) to the last stable release ??

If YES... HOW ??

thx again!

---

### Post by francis_ba on 2008-11-01
[IMG]http://tinyurl.com/rerunner/[/IMG]
viva ubuntu!!!!!!!!!!!!!!!

---

### Post by uarale on 2008-11-01
> **JFo NZ said:**
> This is how I've fixed the problem.

Edit /etc/network/interfaces

Add 2 new lines:

auto eth0
iface eth0 inet dhcp

Then restart machine. Fixed.

[I]Command to edit file:
sudo gedit /etc/network/interfaces[/I]
Same problem with my Acer 5570Z

This works for me, but the Network Manager icon disappears after that.

---

### Post by gryzzly on 2008-11-01
nothing works for me so far :(
the biggest problem is that I (being so disapointed now) installed this at my parents, so they don't have network now...

I am still using my 8.04 on laptop...

Please help.. (tried all described solutions...)

---

### Post by dheerajsp on 2008-11-01
i;m able to access my router after manually adding eth0 in my interfaces list. but im still unable to access any sites!

when i restart the networking, i get a msg which says something like /etc/resolv.conf in missing!

strangely, this happened only in Kubuntu. when i tried Wubi'ed Ubuntu, it worked!

---

### Post by hofa on 2008-11-01
Just create a file /etc/resolv.conf and add the ip address for your router

```
sudo gedit /etc/resolv.conf
```

and add the following line:

```
nameserver [IP address of your router]
```

(you can find the IP address of your router by using the code ```
route -n | grep UG
```
the IP address in between the two 0.0.0.0 is your router.)

---

### Post by oceallaighm on 2008-11-01
> **JFo NZ said:**
> This is how I've fixed the problem.

Edit /etc/network/interfaces

Add 2 new lines:

auto eth0
iface eth0 inet dhcp

Then restart machine. Fixed.

[I]Command to edit file:
sudo gedit /etc/network/interfaces[/I]

This worked for me, though I do loose the NetworkManager. Toshiba L300D-10Q

Many thanks.

---

### Post by hofa on 2008-11-01
You don't have to restart your machine. Doing ```
sudo /etc/init.d/networking restart
``` should be enough.

I allready tried this method, it didn't work for me

---

### Post by gryzzly on 2008-11-01
here is some comands output that might be helpful:
lspci -knn 
```

02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C+ [10ec:8139] (rev 10)
        Kernel driver in use: 8139too
        Kernel modules: 8139cp, 8139too

```
ifconfig
```

eth0    Link encap:Ethernet  HWaddr: 00:50:8d:6a:66:35
        inet6 addr: fe80::250:8ddd:fe6a:6635/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:11 errors: 0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 B)  TX bytes:2178 (2.1 KB)
        Interrupt:18 Base address:0xa0000

lo      Link encap:Local Loopback
        inet addr:127.0.0.1   Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:216 errors:0 dropped:0 overruns:0 frame:0
        TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:13536 (13.5 KB) TX bytes:13536 (13.5 KB)

```
sudo ifup eth0
```

Ignoring unknown interface eth0=eth0.

```
sudo ifdown eth0
```

ifdown: inerface eth0 not configured

```

oh, all this is hand typed... since I don't have network on the computer with problems...

---

### Post by gryzzly on 2008-11-01
then, when I complete this:
sudo update-rc.d -f NetworkManager remove
```

  Removing any system startup links for /etc/init.d/NetworkManager ...
    /etc/rc2.d/S28NetworkManager
    /etc/rc3.d/S28NetworkManager
    /etc/rc4.d/S28NetworkManager
    /etc/rc5.d/S28NetworkManager

```
sudo /etc/init.d/networking restart
```

  * Reconfiguring network interfaces...                     [ OK ]

```
sudo dhclient eth0
```

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For into, please visit http://www.isc.org/sw/dhcp

Listening on LFP/eth0/00:50:8d:6a:66:35
Sending on LFP/eth0/00:50:8d:6a:66:35
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleepeing.

```

---

### Post by gryzzly on 2008-11-01
Please somebody try to help. I am not having 8.04 disc with me, so I am not able to roll back and I will not soon come to parents again, and it would be worst if I will leave them with no internet...
Many thanks

---

### Post by hofa on 2008-11-01
Have you tried setting a static IP and route after the last changes you did?

```
sudo ifconfig eth0 [Your IP] netmask [Your network's netmask]
sudo route add defatult gw [IP or your router]
```
and put 'nameserver [IP address of your router]' in /etc/resolv.conf (delete all the other information)

Or you quickly download an 8.04 disc from ubuntu site

---

### Post by gryzzly on 2008-11-01
> **hofa said:**
> Have you tried setting a static IP and route after the last changes you did?

I don't have router here, it's only DSL modem that works as DHCP as I can understand it. So I don't know what should I put as static IP or netmask.

And internet is kind of slow around here, I am not sure if I will be able to get 8.04 till the evening. Thanks for advice, I put it on download.

---

### Post by hofa on 2008-11-01
How do you connect to the internet?

---

### Post by gryzzly on 2008-11-01
> **hofa said:**
> How do you connect to the internet?

I am using my own laptop with 8.04 on it, thru somebody's open wi-fi around here. 

On parents desktop it is no wi-fi adapter or any other possible connection except wired one. (and wired one is through dsl modem).

---

### Post by hofa on 2008-11-01
Last thing I would try:

```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

if this doesn't work, then I don't know what will...

---

### Post by gryzzly on 2008-11-01
> **hofa said:**
> Last thing I would try:

```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

if this doesn't work, then I don't know what will...

Here is output:
sudp ifconfig eth0 down — doesn't produce output;
sudo ifconfig eth0 up — doesn't produce output;
sudo dhclient eth0:
```

There is already a pid file /var/run/dhclient.pid with pid 5880
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:8d:6a:66:35
Sending on   LPF/eth0/00:50:8d:6a:66:35
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleepeing.

```

Thank you a lot for you response. Unfortunately it doesn't work.

Hopefully, somebody has some more ideas?

---

### Post by emrahustun on 2008-11-01
> **JasonDavies said:**
> 

```
$ sudo update-rc.d -f NetworkManager remove
```

Reboot

```
$ ifconfig eth0 10.0.0.10
$ route add default gw 10.0.0.2
$ sudo update-rc.d NetworkManager defaults

```


Hello.
This works for Datron laptop too.
But I need to do these after all restarts.

And second problem, it can't get DNS ip.
Any idea?

---

### Post by hofa on 2008-11-01
edit /etc/resolv.conf and put in 
```
nameserver 10.0.0.2
```
make sure it is the only line in there

---

### Post by Absorbed on 2008-11-01
> **gryzzly said:**
> I am using my own laptop with 8.04 on it, thru somebody's open wi-fi around here. 

On parents desktop it is no wi-fi adapter or any other possible connection except wired one. (and wired one is through dsl modem).

Well, I'm no expert, but it appears that your router doesn't use DHCP, and therefore need to set your IP address manually. If you use a router, you can probably login to your router and enable DHCP there, and then "sudo dhclient eth0" should work.

To manually set your IP address you have do something like the following:
```
sudo ifconfig eth0 <your IP address>
sudo route add default gw <your router's IP address>

```

Then you need to add "nameserver <your router's IP address>" to /etc/resolv.conf

---

### Post by emrahustun on 2008-11-01
> **hofa said:**
> edit /etc/resolv.conf and put in 
```
nameserver 10.0.0.2
```
make sure it is the only line in there

Thank you. I put it before. Now DNS is working by coincidence.
But when i restart my machine, i have to do these things again.

---

### Post by oferfrid on 2008-11-01
> **JasonDavies said:**
> My workaround for this problem is as follows:

1. Disable NetworkManager from starting up:

```
$ sudo update-rc.d -f NetworkManager remove
```

2. Reboot

3. Manually set up eth0 using ifconfig and route:

```
$ ifconfig eth0 10.0.0.10
$ route add default gw 10.0.0.2

```

4. Edit /etc/resolv.conf:

```
$ echo "10.0.0.2" >> /etc/resolv.conf
```

The exact IP addresses will be different for your individual setups, of course.  You might want to try running ```
dhclient eth0
``` instead of step 3.

Works for me on Asus m3n but this is a workaround not a solution.
The Network manager is down. the IP is static.

---

### Post by Hangwire on 2008-11-01
> **oceallaighm said:**
> This worked for me, though I do loose the NetworkManager. Toshiba L300D-10Q

Many thanks.

Yup. Worked for me too.

---

### Post by gryzzly on 2008-11-01
> **Absorbed said:**
> Well, I'm no expert, but it appears that your router doesn't use DHCP, and therefore need to set your IP address manually. If you use a router, you can probably login to your router and enable DHCP there, and then "sudo dhclient eth0" should work.

To manually set your IP address you have do something like the following:
```
sudo ifconfig eth0 <your IP address>
sudo route add default gw <your router's IP address>

```

Then you need to add "nameserver <your router's IP address>" to /etc/resolv.conf

Thank you for your response. It is no router at all here. It is DSL modem.

---

### Post by Corazon912 on 2008-11-01
Well I took detailed notes of all these fixes since as soon as I upgraded I had network trouble.  However when I went back to Ubuntu 8.10 and on it now, the wired connection worked just fine with no fixings needed.
I assume everyone has already tried re-booting, but its working here now with no problems.

---

### Post by Absorbed on 2008-11-01
> **gryzzly said:**
> Thank you for your response. It is no router at all here. It is DSL modem.

I don't know how to setup a DSL modem manually. You could wait until someone who does know posts, or you could search the web. Perhaps these links could be relevant: [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE) [https://help.ubuntu.com/8.04/internet/C/modems-adsl-usb.html](https://help.ubuntu.com/8.04/internet/C/modems-adsl-usb.html)

I found out how to get the internet to work with my router manually when installing gentoo, so perhaps there will be gentoo documentation for configuring DSL modems, if you don't have any luck elsewhere.

Good luck.

---

### Post by stoneybroke on 2008-11-01
After up-grading from V8.04 to V8.10 I was getting a network connection but after a power failure and reboot I lost the network connection icon on the top bar this has came back after entering

sudo /etc/init.d/NetworkManager stop then
sudo /etc/init.d/NetworkManager start

but after entering

sudo update-rc.d NetworkManager defaults

I get

update-rc.d: warning: /etc/init.d/NetworkManager missing LSB style header
System startup links for /etc/init.d/NetworkManager already exist.

However I still can't get the network to work even after trying all the above methods posted so I still have no network connection to the internet.

---

### Post by gryzzly on 2008-11-01
> **Absorbed said:**
> I don't know how to setup a DSL modem manually. You could wait until someone who does know posts, or you could search the web. Perhaps these links could be relevant: [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE) [https://help.ubuntu.com/8.04/internet/C/modems-adsl-usb.html](https://help.ubuntu.com/8.04/internet/C/modems-adsl-usb.html)

I found out how to get the internet to work with my router manually when installing gentoo, so perhaps there will be gentoo documentation for configuring DSL modems, if you don't have any luck elsewhere.

Good luck.

Thanks for response.

I had a connection before, so I am familiar with setup process for DSL modem and ubuntu. Problem is that I can't connect to the modem at all. 
I should get something that is called &#8220;PPPoE Access Concentrator on eth0&#8221; &#8212; which is like an answer that modem gives when connected to PC. (as I understand it)

---

### Post by billd42 on 2008-11-01
Managed to get networking working with the workaround detailed earlier in this post, but now when I put my computer to sleep, networking doesn't work on resume.  I tried to stop and restart the eth0 interface and get a new dhcp lease but kept getting the error someone detailed earlier where dhclient keeps trying to get an IP address and failing.

Rebooting the machine helped, that was about it.
](*,)](*,)](*,)

---

### Post by mundo on 2008-11-01
I've managed to fix this issue by doing the following:

```
sudo gedit /etc/apt/sources.list
```

Add the following 2 lines in this file and save:

```
deb http://ppa.launchpad.net/network-manager/ubuntu intrepid main
deb-src http://ppa.launchpad.net/network-manager/ubuntu intrepid main
```

Then update the your local repositories - I did this by using a Mobile Broadband stick to get a connection so this may be an issue if you haven't got any network: 

```
sudo apt-get update
```

Then update the system:

```
sudo apt-get upgrade
```

Reboot and see if you can then connect to your network.

---

### Post by lugburz on 2008-11-01
Do you know if the NetworkManager issue is going to be fixed soon? because the work-around described in this thread worked for me and I prefer the have an official fix.

Thanks

---

### Post by Neo70 on 2008-11-01
I have solved the problem adding:

auto eth0
iface eth0 inet dhcp

in the file /etc/network/interface.

Reboot your pc and enjoy the network. (After that you can unistall NetworkManager). 

Hope this help!:guitar:

---

### Post by Neo70 on 2008-11-01
I have solved the problem putting:

auto eth0
iface eth0 inet dhcp

in the file /etc/network/interfaces.

Reboot your system and enjoy the network!
Hope this help. (After that you can uninstall Network Manager)

See ya :guitar:

---

### Post by waffen on 2008-11-01
Yes that work if you dont have a static IP.... any idea in this case?

---

### Post by widor on 2008-11-01
> **waffen said:**
> Yes that work if you dont have a static IP.... any idea in this case?

Yes. I use a static IP address with a wired ethernet connection and also had a problem with network connections after upgrading from 8.04 to 8.1.  

In my case, I noticed that I was able to ping successfully using an IP address but not using a domain name, so the connection itself was okay but evidently DNS wasn't.  

So I checked my /etc/resolv.conf file and found it was empty apart from a comment line. Adding a line saying **nameserver 192.168.1.1** to this file temporarily fixed the problem and enabled normal network connections (use the IP address of your usual DNS server rather than 192.168.1.1 if it's different).  

As I say, this was only a temporary fix as the file reverted to empty on rebooting. However, I discovered that installing the resolvconf package fixed this and now I can reboot and networking works as normal.

---

### Post by handband2 on 2008-11-01
> **mundo said:**
> I've managed to fix this issue by doing the following:

```
sudo gedit /etc/apt/sources.list
```

Add the following 2 lines in this file and save:

```
deb http://ppa.launchpad.net/network-manager/ubuntu intrepid main
deb-src http://ppa.launchpad.net/network-manager/ubuntu intrepid main
```

Then update the your local repositories - I did this by using a Mobile Broadband stick to get a connection so this may be an issue if you haven't got any network: 

```
sudo apt-get update
```

Then update the system:

```
sudo apt-get upgrade
```

Reboot and see if you can then connect to your network.

Thanks for the help.

but....

I would recommend adding it to the repository by:

```
sudo gedit /etc/apt/sources.list.d/launchpad.list
```

---

### Post by waffen on 2008-11-02
> **handband2 said:**
> Thanks for the help.

but....

I would recommend adding it to the repository by:

```
sudo gedit /etc/apt/sources.list.d/launchpad.list
```

OK, I make all this, reboot my laptop and... the problem persist! :(

---

### Post by giorasta on 2008-11-02
I've the same problem.
Jason solution seems to working for mem too but when I reboot problem return: I can't get Ip address from dhcp. 
So I relaunch dhclient and it works. How can I fix problem? Network manager actually is disable

giorasta

---

### Post by emrahustun on 2008-11-02
> **JasonDavies said:**
> 

```
$ sudo update-rc.d -f NetworkManager remove
```

Reboot

```
$ ifconfig eth0 10.0.0.10
$ route add default gw 10.0.0.2
$ sudo update-rc.d NetworkManager defaults

```

After I've done these and put "nameserver 10.0.0.2" in /etc/resolv.conf it's been solved. But after system restart this issue is back again. Now, I have to do these after all restars.

Do you have any suggestions?

Thanks.

---

### Post by waffen on 2008-11-02
Hello,

I found the solution:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I installed Wicd and all my problems go out! I can connect with my static IP address I see the wifi.

I have a problem with thew intrepid repos for Wicd, but I downloaded from sourceforge de deb. packages, uninstall NetworkManage and WifiRadar if you have preintalled both of them.

I can not test with wifi network (actually I can see a pair of wifi network more.. ) but another user can try it?

---

### Post by gryzzly on 2008-11-02
I am going to roll back to 8.04... :( Though I was having some trouble there as well ([http://ubuntuforums.org/showthread.php?t=960551](http://ubuntuforums.org/showthread.php?t=960551)).. 

Feeling disappointed. Network is not minor issue at all :( And I don't see solution for relatively old desktop with no wi-fi capabilities... No router — so no need of static IP. But it just doesn't work.

And on 8.04 network was working without problem.

---

### Post by waffen on 2008-11-02
I response you for the flash in the other link...

But you surrender very easy... :D can you try with wicd? because I suppose its working with your wifi with out problems... its no only for static IP manage all protocols... including wifi.

---

### Post by theorem_hunter on 2008-11-03
same here :(

$ sudo depmod
$ sudo modprobe r8180
$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:21:85:47:1d:29
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:7 errors:0 dropped:2501878221 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3070 (3.0 KB)  TX bytes:3808 (3.8 KB)
          Interrupt:221 Base address:0xc000

$ sudo ifconfig eth0 add 10.0.0.10 broadcast 255.255.255.255 netmask 255.0.0.0
SIOCSIFBRDADDR: Cannot assign requested address
SIOCSIFNETMASK: Cannot assign requested address

$ sudo netgo
* Bringing down interface eth0
* Assigning ip 10.0.0.10 to eth0
- Error: SIOCSIFADDR: No buffer space available
* Setting netmask: 255.0.0.0
- Error: SIOCSIFNETMASK: Cannot assign requested address
* Setting gateway: 10.0.0.2
- Error: SIOCADDRT: No such process

---

### Post by gryzzly on 2008-11-05
> **waffen said:**
> I response you for the flash in the other link...

But you surrender very easy... :D can you try with wicd? because I suppose its working with your wifi with out problems... its no only for static IP manage all protocols... including wifi.

I surrender because it's not my machine, but fathers. And I don't want him another day to spend even without music (since I can't install anything cuz it's no internet)

And Wicd would maybe help to wi-fi if this machine would have that. 

Thanks for response.

Installing 8.04 :(

---

### Post by waffen on 2008-11-05
> **gryzzly said:**
> I surrender because it's not my machine, but fathers. And I don't want him another day to spend even without music (since I can't install anything cuz it's no internet)

And Wicd would maybe help to wi-fi if this machine would have that. 

Thanks for response.

Installing 8.04 :(

Hello,

Are you try with WICD? Its working for me...

---

### Post by oferfrid on 2008-11-06
Installing 8.04 (waiting for good solution) :(

---

### Post by Smeags on 2008-11-06
I had a problem with my wired connection using Intrepid Live CD.  I have an Asus P5N32-E SLI board and wired connection was fine in Windows, just not Ubuntu.  I tried some of the solutions posted here, but I also read that nVidia 680i chipset (which my board has) was having issues with forcedeth.

After some searching I found that I needed to update my BIOS.  I hadn't updated it at all since buying it about 2 years ago.  After updating my BIOS to the newest version my wired connection worked perfectly on the Intrepid Live CD.

I'm not sure this will help everyone here, but maybe it will point some in the right direction.

---

### Post by gryzzly on 2008-11-07
> **Smeags said:**
> I had a problem with my wired connection using Intrepid Live CD.  I have an Asus P5N32-E SLI board and wired connection was fine in Windows, just not Ubuntu.  I tried some of the solutions posted here, but I also read that nVidia 680i chipset (which my board has) was having issues with forcedeth.

After some searching I found that I needed to update my BIOS.  I hadn't updated it at all since buying it about 2 years ago.  After updating my BIOS to the newest version my wired connection worked perfectly on the Intrepid Live CD.

I'm not sure this will help everyone here, but maybe it will point some in the right direction.

Thank you for idea. Hm.  I went to lenovo web-site and it is written that their "BIOS update utility" is working only with windows. Can I do it without installing windows? Oh, definitely 8.04 LTS isn't that bad at all.

---

### Post by farazhussain on 2008-11-10
I had the same problem and simply commenting out the line "iface eth0 inet dhcp" from /etc/network/interfaces worked for me. (See post #6 here: [http://ubuntuforums.org/showthread.php?p=6147839#post6147839](http://ubuntuforums.org/showthread.php?p=6147839#post6147839))

In case anyone is interested, here's my /etc/network/interfaces:

"
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider


auto eth0
#iface eth0 inet dhcp
"


Hope this helps.

---

### Post by lugburz on 2008-11-11
After the today kernel update the bug seems to be solved.

---

### Post by waffen on 2008-11-11
> **lugburz said:**
> After the today kernel update the bug seems to be solved.

False! I just update my laptop, reboot and network Manager dont remember my fixed IP address....:confused:

---

### Post by lugburz on 2008-11-11
I agree, my declaration was wrong. I'm confused too, this because this moorning I did these things:

1. I upgraded the kernel using the upate manager

2. restarted the laptop, NetwokManager was off as before

3. then I attempt to start by hand NetworkManager

4. I plugged the eth wire and magically the newtowork took a goo IP and gateway addresses

5. after that I attemptet do enable again the NetworkManager daemon in rc levels usi "update-rc.d NetworkManager defaults", but after the reboot the NetworkManager shows the usual problem when dhclient is called.

---

### Post by Caethes on 2008-11-12
The temporary solution for me was to remove NetworkManager from auto starting and manually fetch an ip.

```
sudo update-rc.d -f NetworkManager remove
```
reboot

```
sudo dhclient eth0
```

---

### Post by hsl.gt7 on 2008-11-12
Hey Guys I m new one for Ubuntu and I'm having Problem with My DSL connection. I m using ZTE ZXDSL 852 modem that provide by S.L network provider(SLT). and it is finely works with the Windows based OS and when I move on to ubuntu that modem is not working so I download Ubudsl software and install it on my ubuntu box and after that also there are error messages by saying my modem is not configured well not properly installed so any one can help me. can any one tell me how to install USB modem(ZTE ZXDSL 852 modem) and how to configure it properly and tell me what are the things that I want to download to do that everything that I need to. So Please some one help me I want to configure and install my ZTE ZXDSL 852 modem in ubuntu.

---

### Post by oferfrid on 2008-11-12
I would open a new thread for that (it looks like a different problem).

---

### Post by TheShader on 2008-11-13
> **waffen said:**
> Hello,

I found the solution:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I installed Wicd and all my problems go out! I can connect with my static IP address I see the wifi.

I have a problem with thew intrepid repos for Wicd, but I downloaded from sourceforge de deb. packages, uninstall NetworkManage and WifiRadar if you have preintalled both of them.

I can not test with wifi network (actually I can see a pair of wifi network more.. ) but another user can try it?

Wow! This works! Thank you very much! I'm a Linux noobie. :lolflag:

:guitar:

---

### Post by handband2 on 2008-11-26
I found this:
[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)

It looks like mixed success trying the 2nd method.

---

### Post by antonio.napoli on 2008-12-05
> **JasonDavies said:**
> My workaround for this problem is as follows:

1. Disable NetworkManager from starting up:

```
$ sudo update-rc.d -f NetworkManager remove
```

2. Reboot

3. Manually set up eth0 using ifconfig and route:

```
$ ifconfig eth0 10.0.0.10
$ route add default gw 10.0.0.2

```

4. Edit /etc/resolv.conf:

```
$ echo "10.0.0.2" >> /etc/resolv.conf
```

The exact IP addresses will be different for your individual setups, of course.  You might want to try running ```
dhclient eth0
``` instead of step 3.

This thread is very professional. It worked out immediately, many thanks!! Antonio Napoli

---

### Post by antonio.napoli on 2008-12-05
This thread is very professional. It worked out immediately! Many thanks! Antonio Napoli

---

### Post by MonkeyPaw on 2008-12-26
Just to add to the adventure, I had the same problem on my old system. I managed to get my connection working by disabling the default eth0 connection and then making a new wired connection. I manually entered my MAC address (which I found by entering 'ifconfig' in the console), and manually entering my IP Address, Netmask, Gateway, and DNS. It worked after a reboot. Fortunately, my router allows me to do this, but man was this a frustrating ordeal! :-|

---

### Post by clcoyle on 2009-02-05
Folks, I have the same set of issues, and I'm still using 8.04.

Everything was fine until yesterday when I was messing around trying to get SynCE on it to sync up my wonderful Windows Mobile device with Evolution.   

I will try and find which thread I was following, and try to narrow down and post the command(s) that broke it, but I believe it was right after I did an apt-get update.   

Whatever this is doesn't seem to me to be an issue with Intrepid!

I followed a few of the commands before realizing (slap me now!) that they were for DHCP, and I went static the other day after I got Samba up and running with my mixed network.    So now I need to go back and fix a couple of things.   Or maybe just re-install Hardy.

---

### Post by Wolfhere on 2009-02-05
> **JFo NZ said:**
> This is how I've fixed the problem.

Edit /etc/network/interfaces

Add 2 new lines:

auto eth0
iface eth0 inet dhcp

Then restart machine. Fixed.

[I]Command to edit file:
sudo gedit /etc/network/interfaces[/I]

Try removing the auto eth0 line and edit the: iface eth0 inet dhcp to 
auto eth0 inet dhcp

wurked fer me!

---

### Post by Wolfhere on 2009-02-05
> **clcoyle said:**
> Folks, I have the same set of issues, and I'm still using 8.04.

Everything was fine until yesterday when I was messing around trying to get SynCE on it to sync up my wonderful Windows Mobile device with Evolution.   

I will try and find which thread I was following, and try to narrow down and post the command(s) that broke it, but I believe it was right after I did an apt-get update.   

Whatever this is doesn't seem to me to be an issue with Intrepid!

I followed a few of the commands before realizing (slap me now!) that they were for DHCP, and I went static the other day after I got Samba up and running with my mixed network.    So now I need to go back and fix a couple of things.   Or maybe just re-install Hardy.

make sure you have the line to disable the synce interface in your interfaces file with:
iface rndis0 inet dhcp

---

### Post by sahrjd on 2009-02-18
> **JFo NZ said:**
> This is how I've fixed the problem.

Edit /etc/network/interfaces

Add 2 new lines:

auto eth0
iface eth0 inet dhcp

Then restart machine. Fixed.

[I]Command to edit file:
sudo gedit /etc/network/interfaces[/I]

That messed my machine up.  I have to boot in receovery mode and change ti back to get the system to boot correctlly again.

---

### Post by sahrjd on 2009-02-18
I was able to get wired (not wireless (802.11 or GSM) to work for a while.  I loadeda webpage and it started downloading some updates and then the connection went away :(

Makes no sense.

---

### Post by scrawl78 on 2009-03-02
> **JasonDavies said:**
> My workaround for this problem is as follows:

1. Disable NetworkManager from starting up:

```
$ sudo update-rc.d -f NetworkManager remove
```

2. Reboot

3. Manually set up eth0 using ifconfig and route:

```
$ ifconfig eth0 10.0.0.10
$ route add default gw 10.0.0.2

```

4. Edit /etc/resolv.conf:

```
$ echo "10.0.0.2" >> /etc/resolv.conf
```

The exact IP addresses will be different for your individual setups, of course.  You might want to try running ```
dhclient eth0
``` instead of step 3.

Thanks for this solution. It's such a pity it is necessary on a clean install from a recently downloaded Live CD.

Out of curiosity, are there currently any updates/fixes for the Network Manager or is the best solution simply not to use it?

---

### Post by oferfrid on 2009-04-29
Solved for me in Ubuntu 9.04.
Just working even on the live CD
(M2N-W Asus motherboard)

---

### Post by hofa on 2009-04-29
Oh I forgot this thread was here

It just went back to 7.10 because I didn't want to hastle with manual network configuration. After a month or so I switched to Arch Linux.
If you're still having problems, I suggest you try Network Profiles (netcfg). It rocks =D

---

