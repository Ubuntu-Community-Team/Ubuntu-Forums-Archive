---
title: "Please help"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by yogiudo on 2007-03-28
Hi again.
I just got back from the local Best buy and got myself a new router. Netgear to be exact.

I was able to connect to the internet through my pppoe connection via my Windows partition, but I am unable to connect to anything, (not even the router) through my Linux distro. I am using 6.06.

I would like very much tro connect to the internet from my Linux partition. Can someone spare a few moments to help this Ubuntu Noob get past this part? I specifically bought this router just to make my Linux internet connection possible.

---

### Post by chili555 on 2007-03-28
Did you set up the new router to select PPPoE and put in the username and password you got from your ISP? Once that's done, your Ubuntu machine should connect.

---

### Post by yogiudo on 2007-03-28
As I indicated in my previous email, I am able to connect to the internet through my PPPoE connection via my router in windows Partition. That would mean that what you mentioned has aleady been done and setup.

Furthermore:
I ran  ifdown -v eth0 and then  ifup -v eth0 

This displayed the error:

Error: Temporary failure in name resoluton

Does this add any extra ideas to anyones mind?

I have a x86 machine with a windows XP professional partition, and I have a Linux partition. The Linux partition is Ubuntu 6.06. 

I have a netgear router that has already been configured correctly and is providing internet "just fine" to my windows partition.

---

### Post by yogiudo on 2007-03-28
For anyone who is so kind to spend a moment on this, I do appreciate it. And, unlike "dawv" (above thread) I am patient, and will actually check back to see peoples replies. I am very excited to get my linux up and running, but my lack of experience is certainly an obstacle here.

I'm certainly "Fed up" with windows, so I'm willing to give this a chance.

I hope this helps to inspire any "would be" responses.

---

### Post by yogiudo on 2007-03-28
I am still here, still interested in solving this issue.

---

### Post by Floppyjoe on 2007-03-28
Can you post the result of ifconfig? This might shed some further light on the subject.

---

### Post by yogiudo on 2007-03-28
hi.

Because I do not have internet, I had no way to transfer the output, (I have no floppy and no writable CDROM drive) 

ifconfig displays something to this effect:

eth0      Link encap:Ethernet  HWaddr 00:80:C8:F8:4A:51
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:27 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0

---

### Post by yogiudo on 2007-03-28
Please keep in mind that is not my real output from ifconfig, 
but I did change the address at the top to reflect my real data.

---

### Post by Floppyjoe on 2007-03-28
> **yogiudo said:**
> As I indicated in my previous email, I am able to connect to the internet through my PPPoE connection via my router in windows Partition. That would mean that what you mentioned has aleady been done and setup.

Furthermore:
I ran  ifdown -v eth0 and then  ifup -v eth0 

This displayed the error:

Error: Temporary failure in name resoluton

Does this add any extra ideas to anyones mind?

I have a x86 machine with a windows XP professional partition, and I have a Linux partition. The Linux partition is Ubuntu 6.06. 

I have a netgear router that has already been configured correctly and is providing internet "just fine" to my windows partition.

From your previous post it looks like your network interface is getting an IP address from the router.

When you issued the commands:> ifdown -v eth0 and then  ifup -v eth0
did you use the prefix sudo command?

---

### Post by yogiudo on 2007-03-28
yes.

---

### Post by yogiudo on 2007-03-28
I su - root and then did it from there.

Basically everything you see is done from root.

---

### Post by Floppyjoe on 2007-03-28
> **yogiudo said:**
> Please keep in mind that is not my real output from ifconfig, 
but I did change the address at the top to reflect my real data.
I guess your not getting an IP address from the router then?

---

### Post by yogiudo on 2007-03-28
I believe I am getting an address from my router, because it sais 192.168.1.2, which is the address it should be if it had received it from the router.

However I dont have internet, which is my problem. I cant ping yahoo.com or google.com or anything except localhost and 192.168.1.2

If I try to ping my router (192.168.1.1) I get unreachable.

---

### Post by Floppyjoe on 2007-03-28
> **yogiudo said:**
> I believe I am getting an address from my router, because it sais 192.168.1.2, which is the address it should be if it had received it from the router.

However I dont have internet, which is my problem.
OK I thought you fudged that address in there.
Have your tried to ping internet servers both IP addresses and Domain names?
for example (82.211.81.186) and (ubuntuforums.org)
If one of these works and the other one fails then it is probably a DNS problem.
You can use network tools to ping in System/Administration/Network Tools under the ping tab.

---

### Post by yogiudo on 2007-03-28
Actually, I still have an error: the IP you saw was manually added by me. I tried to ad a static IP which did not work. So technically I am not receiving an IP from the router at all.

After I set it to DHCP and refreshed it, I got no IP at all. The tools under system admin dont work either.


:confused:

---

### Post by yogiudo on 2007-03-28
I am starting to wonder if it could be fixed by reinstalling.
Is that a suitable idea?

---

### Post by Grumblebum on 2007-03-28
I have the same situation.  D-Link ADSL VoIP Router, Model DVA-G3340S.  Works perfectly in Windows, so the modem configuration must be correct.  However in Ubuntu, I can't get out to the Internet.

I managed once, sometime ago to reach my ISP, but since then, nothing, so I only go back to Ubuntu everynow and again when I get a new idea.  14 years experience supporting MSbased hardware and software, now wanting to get away from it, but this isn't helping much!:mad:

---

### Post by yogiudo on 2007-03-28
I tried running it from the LiveCD and it does not work. I could try another distro, but I think that is a fairly dumb idea.


should I will wait for the next distro?

Should I "go back to windows" ?

I invested about 8 hours so far into this problem.
getting tired now.

advice?

---

### Post by Grumblebum on 2007-03-28
Can't help you, I'm afraid.  For what it's worth, I've reinstalled a number of times, always with the same result.  As everything's working properly in Windows and the modem/router's going OK, I figure it must be something wrong with the linux/browser, but for the life of me, I can't figure it out.  I think I've got Firefox down pat, so the problem must be with the linux setup.  Any suggestions appreciated.  I'm as new to Ubuntu as you, except I've invested far more hours than you over the weeks!  Tries Mandriva before that, but prefer the Ubuntu interface.

---

### Post by Mr. C. on 2007-03-28
Reinstalling is not likely to resolve anything.

We need to start at the lowest level.  Let's find out what hardware is available, and which drivers are being loaded.  I'm going to give you a series of commands to output into a file.  I'll try to minimize the amount of output you need to copy here:

```
dmesg | grep eth'[0-4]'
lspci | grep net
lspci -n | grep '2[80]0'
ifconfig -a | grep '^[a-z]'
ifconfig -a | grep UP
lsmod | grep mii

```
The other thing we need to know is your router's LAN networking info (ip address, netmask, broadcast).

MrC

---

### Post by Grumblebum on 2007-03-28
Where do I run this?  Remember, I'm a newbie in Linux!

---

### Post by Grumblebum on 2007-03-28
Management IP
These are the IP settings of the LAN interface for the DVA-G3340S. These setting may be referred to as Private settings. You may change the LAN IP address if needed.
	IP Address 	10.1.1.1	
	Subnet Mask   255.0.0.0

---

### Post by Mr. C. on 2007-03-28
> **Grumblebum said:**
> Where do I run this?  Remember, I'm a newbie in Linux!

Right, but you hijacked someone else's thread; the response was for the OP (original poster).

You can run the same commands in a Terminal Window.  You can paste the output into a file, and transfer it any way you can, otherwise, start typing.

MrC

---

### Post by Grumblebum on 2007-03-28
Thanks, and sorry about the lack of courtesy -- to you AND the OP.  Just feeling my way around.  Will go to the other operating system and try suff out and report back.  Cheers.

---

### Post by yogiudo on 2007-03-28
okay, I went into Linux, I ran those commands. Most of them did not produce useful results, however the first command (dmesg | grep eth'[0-4]') produced a message that indicated "No IPV6 routers present".

This seems to me to be a possible culprit.

the lspci -a | grep net command also produced useful information, indicating an nVidia MCP55 something or other.

I dont know if this is enough to troubleshoot my problem, I can possibly buy a floppydisk drive so that I can copy error messages into windows but that seems a bit excess.

I would like to use Linux though, so I am open to that if all else fails.

Any more ideas?

Thanks in advance,

---

### Post by Mr. C. on 2007-03-29
If you're going to interpret the data for me... than you don't need me to help!

No IPv6 routers is typical.  It is inconsequential.

Search the forums for this "nVidia MCP55". and see what you come up with.

Without data, I can't help.

MrC

---

### Post by zami on 2007-03-29
I appologize if this seems overly simple.  (But if your problem IS this simple I'd feel bad for not suggesting it, so here goes!)

I had a hell of a time setting up my own wireless router.  Here is what I remember of it.

1 - modem first.  This should be simple.  Physical line from computer to modem, physical line from modem to phone jack.

2 - router.  Still a physical cord; no wireless yet.  I had to set this up while in Windows, because I HAD to use the install/setup disc that came with the router (a Linsys model).  I simply could not set up the router any other way.

3 - wireless.  There was a specific order in wich Linksys wanted me to power on/off modem and router, and unplug the physical cords.  Tedius stuff that was in the instructions.

4 - network key.  I had to print up my uber long network key, which was auto generated and applied from the Windows/Linksys install/setup program.

5 - rebooted into Ubuntu and
a) in System > Administration > Networking
   make sure the connection you want to use is enabled, then highlight it and click properties, and in the Network Password field type in that super long network key.  Note that, in my case I actually have a password for my network, AND I have this super long key for just the ability to use the router.  You want the long router key in this field.

b) right click your Gnome panel (yes, I'm making the presumption your using Gnome!), then "Add to Panel", and select "Network Monitor".  

c) click on your Network Monitor you just added to the Gnome panel, and try all the different options in the "Connection" field.  Mine defaulted to "lo", when I need "eth1" to actually get online.  When I setup my husbands machine, it connected automatically to "eth0", yet I had to manually type in "eth1" to get a real connection.  (I can also see some of my neighbors networks, and the public school nearby.  Sillyness.)

Again, I appologize if this is all realy elementary!  I just know I myself had a horrid time setting up my router, and did all sorts of complicated trouble shooting, when all along my problem was so simple I'd just overlooked it's solution.

Best of luck to you!  You'll get it.

-zami

---

### Post by Grumblebum on 2007-03-29
If I may butt in again, I think the info will be useful to both of us!

I ran the commands you suggested in terminal.  The resposes are posted below:

dmesg | grep eth'[0-4]'

[17179584.508000] e100: eth0: e100_probe: addr 0xf8001000, irq 201, MAC addr 00:14:85:D0:A4:4F
[17179585.796000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179600.148000] eth0: no IPv6 routers present


lspci | grep net

0000:01:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller (rev 02)


lspci -n | grep '2[80]0'

0000:01:08.0 0200: 8086:1051 (rev 02)

ifconfig -a | grep '^[a-z]'
ifconfig -a | grep UP
lsmod | grep mii

I think it stuffed up at the end somewhere.  It looks different to what I saw in Linux.  It's a pain logging in and out of two op systems!

---

### Post by kvonb on 2007-03-29
When you use Windows to connect "through" the router, does that mean that you connect by clicking on a "connect to" icon, ie a dialup thing?

If so, then you need to configure pppoe on the Ubuntu machine.

Simply open a terminal from the menu->accessories and type:

sudo pppoeconf

It will ask you for all your connection details like username and password.

If that succeeds, then repost and I will help you further.

---

### Post by Grumblebum on 2007-03-29
Don't know which one of us you're answering, but in answer to my last post, this response may be more comprehensive:

dmesg | grep eth'[0-4]'
lspci | grep net
lspci -n | grep '2[80]0'
ifconfig -a | grep '^[a-z]'
ifconfig -a | grep UP
lsmod | grep mii

phil@phil-desktop:~$ dmesg | grep eth'[0-4]'
[17179586.260000] e100: eth0: e100_probe: addr 0xf8001000, irq 209, MAC addr 00:14:85:D0:A4:4F
[17179587.104000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179599.956000] eth0: no IPv6 routers present
phil@phil-desktop:~$
phil@phil-desktop:~$ lspci | grep net
0000:01:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller (rev 02)
phil@phil-desktop:~$
phil@phil-desktop:~$ lspci -n | grep '2[80]0'
0000:01:08.0 0200: 8086:1051 (rev 02)
phil@phil-desktop:~$
phil@phil-desktop:~$ ifconfig -a | grep '^[a-z]'
eth0      Link encap:Ethernet  HWaddr 00:14:85:D0:A4:4F
lo        Link encap:Local Loopback
sit0      Link encap:IPv6-in-IPv4
phil@phil-desktop:~$
phil@phil-desktop:~$ ifconfig -a | grep UP
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
phil@phil-desktop:~$
phil@phil-desktop:~$ lsmod | grep mii
mii                     5888  1 e100
phil@phil-desktop:~$

Will now go back to Linux and try the last suggestion.

---

### Post by Grumblebum on 2007-03-29
Last suggestion had no result, either.

---

### Post by yogiudo on 2007-03-29
> 
If you're going to interpret the data for me... than you don't need me to help!

No IPv6 routers is typical. It is inconsequential.

Search the forums for this "nVidia MCP55". and see what you come up with.

Without data, I can't help.

MrC

Excuse me, what your asking me to do is not really possible because I dont have internet and I dont have a floppy drive. If you read my post you would know that. I wrote down the output from the commands but I will not write down volumes upon volumes upon volumes of information - That is not an acceptable solution.

---

### Post by yogiudo on 2007-03-29
It seems clear to me at this point that Linux does not support some network configurations and x86 hardware. That is fine. I would presume based on my own experience so far that it supports roughly 3%-5% of the possible hardware configurations - typically configurations that have been around for 4-5 years.

If someone can suggest a configuration that they know works with Ubuntu 6.06 I would be willing to consider purchasing that hardware configuration.

---

### Post by Mr. C. on 2007-03-29
> **yogiudo said:**
> Excuse me, what your asking me to do is not really possible because I dont have internet and I dont have a floppy drive. If you read my post you would know that. I wrote down the output from the commands but I will not write down volumes upon volumes upon volumes of information - That is not an acceptable solution.

This is nonsense.  The output is about 14 lines, nothing near "volumes upon volumes upon volumes of information".  Your choice to be not provide the information required is your choice.

Perhaps you will share with us your "acceptable solution".
> **yogiudo said:**
> 
It seems clear to me at this point that Linux does not support some network configurations and x86 hardware. That is fine. I would presume based on my own experience so far that it supports roughly 3%-5% of the possible hardware configurations - typically configurations that have been around for 4-5 years.
This is also nonsense.  What is clear is your frustration and choice not to work through the issues.  Don't ask others now to spend more time than you are willing to spend resolving your own issues.

Best of luck,
MrC

---

### Post by chili555 on 2007-03-29
I must respectfully disagree. I received a new computer, a Thinkpad T60, on Tuesday. I ripped the awful XP harddrive out and replaced it with a zippier drive upon which I installed Edgy. It booted and the wireless indicator was flashing. I gave my encryption code and essid and connected. I installed the ATI drivers and, 15 minutes after first boot, I was done. Linux clearly supports equipment built in early March 2007. My estimate of what is supported globally is 90%. That's the end of my rant.

I think your ethernet card is supported and I think with a very few tweaks, we will have it going. Here are my recommendations.

Open up a terminal and type *sudo gedit /etc/network/interfaces* No matter what else is in there, please edit it to read: ```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```Save and close. Next, *sudo gedit /etc/resolv.conf* No matter what else is in there, make it look like:```
nameserver 208.67.222.222
nameserver 208.67.220.220
```Save and close. Now restart networking: *sudo /etc/init.d/networking restart* Let me know if the response is "sleeping" or "Bound to 192.168.xx" If the latter, open up Firefox and go web surfing!

---

### Post by Grumblebum on 2007-03-29
Still piggy backing on this thread, I ran everything above with positive results, except for the restart network command.  Results below:

phil@phil-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:14:85:d0:a4:4f
Sending on   LPF/eth0/00:14:85:d0:a4:4f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.1.1.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:14:85:d0:a4:4f
Sending on   LPF/eth0/00:14:85:d0:a4:4f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.1.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.1.1.1
bound to 10.1.1.2 -- renewal in 1663 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


What now??

---

### Post by chili555 on 2007-03-29
Huh? This looks like a positive result:```
DHCPOFFER from 10.1.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.1.1.1
bound to 10.1.1.2 -- renewal in 1663 seconds.
```You are hooked up. Can you surf? Download updates? Get torrents? Instant message your Mum?

---

### Post by Grumblebum on 2007-03-29
Can't surf, can't ping ISP.   can talk to router through Firefox.  What about the device not found error?  If I could surf, all my troubles would be over!

---

### Post by chili555 on 2007-03-29
Did you follow **all** the steps? Did you follow post#35 above? If your  interfaces file contained only lo and eth0, you wouldn't have device not found for eth2, ath0, etc., etc. Please retrace your steps. You might also *sudo gedit /etc/modprobe.d/blacklist* to add:```
blacklist ipv6
```Please check my post above and recheck your work. Please post back.

---

### Post by Grumblebum on 2007-03-29
Thanks.  Yes, followed all the steps faithfully.  Will try again.  Have to boot Linux now.  Will report back shortly -- with the full results.

---

### Post by Grumblebum on 2007-03-29
OK, here goes -- the full routine you wanted me to run:

sudo gedit /etc/network/interfaces

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

sudo gedit /etc/resolv.conf

nameserver 10.1.1.1

sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:14:85:d0:a4:4f
Sending on   LPF/eth0/00:14:85:d0:a4:4f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.1.1.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:14:85:d0:a4:4f
Sending on   LPF/eth0/00:14:85:d0:a4:4f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 10.1.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.1.1.1
bound to 10.1.1.2 -- renewal in 1353 seconds.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

sudo gedit /etc/modprobe.d/blacklist

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

blacklist ipv6

Where do we go from here?

---

### Post by chili555 on 2007-03-29
I apologize if I did not make myself very clear in post #35. Let me try a little harder. Please *sudo gedit /etc/network/interfaces* to make it look exactly like this, no more, no less:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```Then *sudo gedit /etc/resolv.conf* to make it look exactly like this, no more and no less:```
nameserver 208.67.222.222
nameserver 208.67.220.220
```Restart networking: *sudo /etc/init.d/networking restart*

Don't make me fly down there!:)

---

### Post by Grumblebum on 2007-03-29
Gotcha!  I thought you meant right in context!  What is the nameserver IP address, though?  Just out of interest!  I thought it would be provided by my ISP.  Years of mindfix with MS had obviously gotten to me.  Back in a few minutes.  Cheers.

---

### Post by Grumblebum on 2007-03-29
Yes!!  Talking to you now from Ubuntu!  Thankyou very, very much.  This has been a many weeks long batlle and you've fixed it a morning (for me!).

I owe you a beer or three, if ever I get over there.

Can you tell me, where is the best place to learn some of the command language and file structure.  For instance, I'm assuming sudo is a structural  level above or below root?  The GUI is quite nice, but from a Windows perspective, quite a lot can be done from the command line that can't be done elsewhere.....  Cheers.

---

### Post by chili555 on 2007-03-29
I suggest you just read these forums. When you want to accomplish a task, read posts from others that are asking about the same subject. Read on down the thread until you find out what they finally did to make it work. Write it down and bookmark it. As you see in an earlier post on this thread, I bought a new laptop recently, and I read hundreds of posts about it to see what issues I might find and how to solve them.

I keep a document in my /home/chili where I have collected the successful process to accomplish what interested me: remote administration of a server, Video CD's, ripping mp3's from the command line (!), etc. and I add to it and refer to it frequently. I call it "My Help File."

sudo is the accepted way to temporarily, it expires at the end of the command, gain root, or super-user privileges. Approximately, Super User DO. By default, for security, ordinary users cannot edit configuration files, see certain files or install software. So when you, the *only* user, want to do so, you must temorarily be granted root privileges.

Keep learning! Good luck.

---

### Post by Grumblebum on 2007-03-29
Thanks for the tip and all the best.  I'll probably trip over you sometime in the future.

Cheers.

---

### Post by yogiudo on 2007-03-30
I will try that when I get home.

---

