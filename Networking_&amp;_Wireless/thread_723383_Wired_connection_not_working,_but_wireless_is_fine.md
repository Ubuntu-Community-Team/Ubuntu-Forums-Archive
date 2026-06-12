---
title: "Wired connection not working, but wireless is fine"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by spectrevk on 2008-03-13
This is an odd problem. I'll spare you the details of my week-long odyssey to get Ubuntu installed on my Compaq Presario V5000 laptop...just let me say that if you have trouble with a bootable CD, you might want to try a bootable DVD.

Now, my problem is that at home, both my wired and my wireless connections work. At work, however, where I used to be able to use a wired connection (when I had XP), nothing I try (or anyone else I've asked, including our sys admin) seems to be able to get the wired connection to work. I have the right DNS server, and it doesn't work. It even auto finds the right DNS server, and it doesn't work. I can see the actual network (various servers and such), but I can't connect to the internet, ping any website, or even ping the gateway. 

Oddly enough, while I was going through changes trying to get Ubuntu installed, I managed to connect to the work network and use the internet just fine using Fedora Core, so I'm not sure what the problem is.

I don't think it's the driver, since I was using Ubuntu 7.10 yesterday at home and had perfect connections.

It must be some configuration thing, but it's nothing that I can change with the default tools in the GUI, because I've tried all of that stuff. 

Earlier this week I tried disabling the wireless card in BIOS, just removing it in Ubuntu, trying to set up an assigned IP...none of it worked.

---

### Post by prshah on 2008-03-13
> **spectrevk said:**
> 
 seems to be able to get the wired connection to work. I have the right DNS server, and it doesn't work. It even auto finds the right DNS server, and it doesn't work. I can see the actual network (various servers and such), but I can't connect to the internet, ping any website, or even ping the gateway. 



plug in the network wire, then try restarting networking ```
 sudo /etc/init.d/networking restart
```

---

### Post by unutbu on 2008-03-13
Just to give us a better idea about the situation, please post the output to
```

ifconfig
route

```

---

### Post by spectrevk on 2008-03-13
Unfortunately I can't copy + paste those results, since it can't connect to the internet. What strikes me as very odd is that I'm able to see the Windows Network. I can see all of the servers just fine. It's just the internet that doesn't work.

And the fact that this works at home but not here is even more puzzling.

EDIT: Here's what route gave me:

Destination     Gateway    Genmask                Flags          Metric            Ref             Use     Iface
10.12.68.0       *              255.255.255.0        U               0                    0                   0       eth0
link-local            *              255.255.0.0           U                1000              0                  0        eth0

---

### Post by spectrevk on 2008-03-13
Here's a copy of what it ifconfig says about eth0, the wired ethernet interface:

ETH0  Link encap:Ethernet HWaddr 00:16:D4:01:F9:13
inet addr:10.12.68.78 Bcast:10.12.68.255 Mask: 255.255.255.0
inet6 addr: fe80::216:d4ff:fe01:f913/64 Scope: Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX Packets:293 errors:0 dropped:0 overruns:0 frame:0
TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:78537 (76.6KB) TX bytes: 11582 (11.3KB)
Interrupt:19 Base address:0x6000

---

### Post by Iowan on 2008-03-13
Check the contents of **/etc/dhcp3/dhclient.conf**.  There are several options there... but the routing table seems like a more likely suspect.

---

### Post by spectrevk on 2008-03-13
What would I do to fix the routing table? I'm not exactly sure what kind of changes I would need to make. I'm very new to linux (I've tried installations before, years ago, but never really got into it), but I'm fairly technically adept (I used to work in troubleshooting and support, and I like to think that I learn quickly)

---

### Post by unutbu on 2008-03-13
I don't know if this is the kosher way to make things work, but this has worked for me so I'll pass it on:

It appears 
10.12.68.78 is your laptopip. ??.??.??.?? (you fill in the blank) is your gateway at work.

Edit you /etc/hosts file to contain the following two lines:
```

10.12.68.78 laptopip
??.??.??.?? gatewayip

```

Again, change ??.??.??.?? to the real gateway ip.

Now make a little text file (really, a script):

```

#!/bin/sh
/sbin/ifconfig eth0 laptopip netmask 255.255.255.0 up
/sbin/route add -host gatewayip eth0

```

Call the script 'ethon'.

In a terminal run
```

chmod 755 ethon

```

Then, whenever you want to connect at work, run the command

```

./ethon

```

---

### Post by spectrevk on 2008-03-14
ack...I tried it, and it still doesn't work.

What's weird is that it gave me a bunch of permission denied messages, even when I used su

I tried typing sudo ./ethon and didn't get any errors, but it didn't fix anything either.

---

### Post by unutbu on 2008-03-14
At the terminal prompt, type:
```

sudo /sbin/ifconfig eth0 laptopip netmask 255.255.255.0 up
sudo /sbin/route add -host gatewayip eth0
ifconfig -a
route

```

Then post the output of all 4 commands here.

---

### Post by spectrevk on 2008-03-14
The first command gives nothing in return, which leads me to believe that it's not working. The weird thing is that if I just type su and enter a password, it says that it's the wrong password. But if I do sudo, the password is fine. I've only ever set one password during my install.In any case, the sbin commands didn't return anything, the ifconfig was the same as the one I posted before, and route offered this:

```

Destination    Gateway      Genmask                       Flags   Metric   Ref      Use   Iface
gateway ip      *              255.255.255.255             UH       0         0            0      eth0
10.12.68.0      *              255.255.255.0                 U         0         0           0       eth0
link-local          *               255.255.0.0                    U         0          0          0       eth0




```

Another thought that I've had is that the default installation for Fedora Core 8 connected to the office internet just fine. Perhaps this is an incompatibility with the program(s) Ubuntu uses for ethernet connection? I'm not sure where to begin with researching this, but perhaps if I found and switched over to the program that Fedora uses this would work alright?

Also, in the department of things that worry me, the indicator light for my wireless isn't lighting up anymore, which is very odd. But this problem seems to happen regardless of the light, so that'll be something else I can worry about later.

---

### Post by spectrevk on 2008-03-14
Okay, this thing with my wireless suddenly not coming on is weird. Is there anything in what we changed that should affect that? I'm using the bcm43xx driver with the firmware thing.

---

### Post by unutbu on 2008-03-14
spectrevk, all the commands I've suggested are harmless. They are temporary in the sense that you can always return your laptop to its previous state by rebooting. 

The two '/sbin' commands do not normally give any output... only if there is an error. So it is a good thing that there was no output.

'ifconfig', 'ifconfig -a' and 'route' are merely information gathering/diagnostic tools. 

```

sudo /sbin/ifconfig eth0 laptopip netmask 255.255.255.0 up

``` 
should (if anything) activate the eth0 interface, not shut it down.

The route command:
```

/sbin/route add -host gatewayip eth0

``` 
does change your routing table, but only temporarily. If it worked, we could have worked to make it permanent, but that's another story.

Regarding other issues:
1) "su password does not work, but sudo does." I think with Ubuntu this is normal behavior. I think I read somewhere that with Ubuntu you only ever need to use sudo or gksudo. When I type su at a terminal prompt, and type in my password, I also get 
```

su: Authentication failure
Sorry.

``` So I don't think this has anything to do with your current problem.

2) "Fedora worked." If Fedora just worked out of the box, then perhaps that's what you should use. But if there is a way to do it in Fedora then there is definitely a way to do it with Ubuntu. There is no "incompatibility" problem with the commands I've given you because the command line programs 'ifconfig' and 'route' are unix tools common to all linux distributions. You mentioned that GUI apps under Ubuntu did not work for you. I assume you tried Network Manager. Did you also try WICD? Some people report WICD working much better than Network Manager, but I have no personal experience with this.

3) "wireless light used to come on, but it doesn't anymore." Does the light come back on if you reboot? If not, try (after rebooting)
```

sudo ifconfig eth0 up

``` 
and if that doesn't work, try
```

sudo /etc/init.d/networking restart

``` 
If that doesn't work, then I'm sorry but I don't have any ideas why it should have stopped working. My only advice would be to think carefully about everything you've done between the time when it was working and the time you noticed it stopped working. Again, the effect of my commands can all be wiped out by a simple reboot.

3) your routing table looks ok except for the space: 'gateway ip' should be 'gatewayip'
(I assume this is just a typo, since otherwise route would be giving the wrong number of columns on that line...)

Sorry I couldn't help you. Hopefully some more knowledgeable member is reading and can lend a hand...

---

### Post by spectrevk on 2008-03-14
I didn't mean to suggest that the commands were harmful, I was only wondering if my puttering around might have switched something off. No big deal, really...I figured out what was going on with the lights. 

I had thought of using Fedora instead, but two things stopped me:

1. I like some of the tools included with Ubuntu more
2. As you said, if it works in one, it should work in the other, and I'm a little hard-headed.

That said, I'm very curious what might be the x-factor here if Fedora worked out of the box, and Ubuntu doesn't. What confuses me even more is that Ubuntu seems to work everywhere else. I just went to a Barnes and Noble and was able to connect to their wireless (didn't do much of anything, since I didn't feel like paying, but whatever). 

My current theory is that something about my laptop's hardware, some program that Ubuntu is using for networking, and the setup here at work (there are dozens of cubicles, so multiple hubs, and our phones use the same network...in fact, the network cable in question is from a pass-through on the back of my phone...yes, this worked under XP and Fedora) is causing the problem. I'm interested in trying out WICD, but I'm not sure where to find it. It doesn't have an icon in the menus, and I'm still looking for a good rundown of the linux filesystem. It's rather frustrating not knowing where my program executables and such are all located. I'm guessing somewhere in /bin, but I'm not sure. :(

Thanks for all of your help with this, by the way. The guy who was helping me out kinda gave up a few days ago, so I've been tooling around with this myself. Part of me wonders if this isn't a bug in Broadcom's driver/firmware.

---

### Post by unutbu on 2008-03-14
1) "Part of me wonders if this isn't a bug in Broadcom's driver/firmware."

Well, you said that your wired connection works at home, so that would suggest your eth0 hardware is fine. Also, if it worked under Fedora...

2) "It's rather frustrating not knowing where my program executables and such are all located."

```

which ifconfig 

``` shows you where the program ifconfig is located.

```

locate ifconfig

``` shows you *all* files on your system that has a filename which matches 'ifconfig'.

```
man ifconfig
```
spits out a manual page regarding ifconfig. They can be a little difficult to read, but its better than nothing.

3) Regarding WICD:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

4) If you're willing to give command-line networking one more try: Can you get the wired connection working under XP and/or Fedora again?
If so, run
```

route

```
again, and copy down the output and post here. Maybe if we know what a working routing table looks like, we can mimick it under Ubuntu... (route works under Fedora; I think there is a similar command under XP, but I'm not sure about the details.)

---

### Post by spectrevk on 2008-03-14
Unfortunately, I no longer have XP or Fedora installed on my laptop. I'll try out WICD when I get home this evening, and try it out at the office on Monday.

---

### Post by spectrevk on 2008-03-17
Okay, I tried WICD at work, and it's got the same problem. Is there some kind of underlying network driver that could be making the difference here? Obviously it works on my machine under Fedora, and it works for my co-worker with Ubuntu, so...what could be the issue here?

I'm having some trouble copy/pasting the results of Route from my XP machine :(

---

### Post by unutbu on 2008-03-17
Whooa, back up. There is a coworker with Ubuntu who can connect successfully?
What method does he use to connect? Copying his settings is perhaps the easiest way to connect. If you use DHCP, then everything can be copied, if you are assigned a static IP, you'll have to enter that instead (of course).

If he cannot tell you how he connected, ask him to run 
```

route
cat /etc/hosts
cat /etc/network/interfaces

```
Copy down his output and post. 

I know it is unpleasant to copy down output by hand and have to type it all in to post, but without seeing output it's impossible for us to help you. "It didn't work" is especially hard to debug. :)

It would also be very informative if it would be possible for him to try to connect to the internet from your office, using *your* ethernet jack and cable.  If he can do this, then at least you can rule out bad external hardware between your laptop and the internet. Be sure to use your ethernet cable so that is tested too.

Ask your sysadmin if his router is doing any ip packet filtering, or perhaps MAC address filtering. You want to make sure that the office router is not rejecting your IP packets on the basis of your IP address or your MAC (hardware) address. (I know you were able to connect using Fedora and XP, so it probably is not a MAC address filtering problem, but if Fedora was using a different IP address, *maybe* that could be related to your problem.)

I should have asked this before, but better late than never: Are you trying to connect using a static IP that was assigned to you by your sysadmin or are you expected to use DHCP at work?

If none of the above work, then we need to back up, slow down and recheck our assumptions. 

When you say you tried WICD but got the same problem, please state exactly what you did to configure WICD. The more detail you can give us, the better. 

The same goes with Network Admin. Tell us exactly which boxes you clicked and what you see or entered in each of the tabbed windows.

Finally, this link my help you.
[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

---

### Post by spectrevk on 2008-03-17
The co-worker is our linux sys admin...and he tried his hand at fixing the problem early last week, before I started posting here. He entered the same DNS info, and it didn't work. He remarked that the IP address DHCP is giving me is outside the range that we normally get (normally our IPs are 10.12.66.xxx or 10.12.67.xxx; mine is 10.12.68.78 or 10.12.68.79). He then tried to set up a static IP, but that didn't work either. What's infuriating is that under DHCP, I'm able to see the network, and I can clearly connect to the DNS server if I'm getting an IP address, but I can't ping the gateway or anything else of interest. 

So I've tried DHCP and Static IP before, with the same results (no internet). I'm not sure how it is that Fedora was able to get an acceptable IP from the server while Ubuntu isn't.

---

### Post by unutbu on 2008-03-17
The configuration of DHCP on the server side is independent of the configuration of your company's firewall. The DHCP server could very easily be handing out ip addresses which fall outside the range of ip addresses that the router/firewall accepts. At the moment this seems like the most likely candidate for origin of your problems.

---

### Post by spectrevk on 2008-03-17
But...if that's the case, then why isn't the static IP setup working? And why was I getting valid IP addresses from DHCP under XP and Fedora?

I'm not sure what the best next step would be.

---

### Post by unutbu on 2008-03-18
Those are all good questions.
What exactly did you try to get static IP working?
Perhaps try the method described here:

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

Please take notes on all the steps you take and post computer output here.

---

### Post by spectrevk on 2008-03-18
Well, the initial try was done by  the sysadmin, and he just used Network Manager. I've tried since then using both NM and WICD (which I like a lot more than NM, except that there's no access to the Hosts file; it's superior for dealing with wireless connections though, IMO).

Of interest is that when following the directions on that page, I found an interfaces file that said only:

auto lo
iface lo inet loopback

I'm wondering if this is because my WICD isn't set to start up any interfaces automatically.

In any case, setting up the static IP that way had more or less the same results, same ifconfig results, same lack of internet access. The main difference is that when I'm set with a static IP and I try to ping the gateway, I get a message that the Destination Host is Unreachable. When I'm using DHCP, it says that the Network is Unreachable.

---

### Post by spectrevk on 2008-03-18
Well, the initial try was done by  the sysadmin, and he just used Network Manager. I've tried since then using both NM and WICD (which I like a lot more than NM, except that there's no access to the Hosts file; it's superior for dealing with wireless connections though, IMO).

Of interest is that when following the directions on that page, I found an interfaces file that said only:

auto lo
iface lo inet loopback

I'm wondering if this is because my WICD isn't set to start up any interfaces automatically.

In any case, setting up the static IP that way had more or less the same results, same ifconfig results, same lack of internet access. The main difference is that when I'm set with a static IP and I try to ping the gateway, I get a message that the Destination Host is Unreachable. When I'm using DHCP, it says that the Network is Unreachable.

---

### Post by spectrevk on 2008-03-18
Okay. I just ran ipconfig and route on my XP computer that *does* work. Keep in mind that this is a desktop machine, so the hardware is very different. 

[http://img.photobucket.com/albums/v475/teninjas/workingconfig.gif](http://img.photobucket.com/albums/v475/teninjas/workingconfig.gif)

---

### Post by spectrevk on 2008-03-18
Okay, I just tried something out: I used the ethernet cable that goes to the desktop, and I actually got a working internet connection, with a valid IP address. So apparently there's some issue with the phone passthrough.

When I tried using the phone passthrough on the desktop, I again got a 10.12.68.xxx ip address, but it worked fine. So it looks like there is some issue between linux and this phone pass through. I also tried a Live CD for Fedora, since Fedora worked before, but...it didn't work. The original install I did used a standard install DVD, so it's possible that it installed some odd network thingy that I didn't have the prescence of mind to take note of at the time. :(

I'm starting to lose hope that this is something I can fix.

---

### Post by spectrevk on 2008-03-18
Okay, using my brain this time, I've managed to get a good copy/paste of the ifconfig and route responses on this laptop. This is what it looks like when I'm using the passthrough from the phone:
```

eth0      Link encap:Ethernet  HWaddr 00:16:D4:01:F9:13  
          inet addr:10.12.68.79  Bcast:10.12.68.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe01:f913/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:843 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:265633 (259.4 KB)  TX bytes:130909 (127.8 KB)
          Interrupt:19 Base address:0x6000 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.12.68.0      *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 eth1
default         *               0.0.0.0         U     1000   0        0 eth1
```

And this is what it looks like when I use the connection meant for the desktop (i.e. when it actually works)

```

eth0      Link encap:Ethernet  HWaddr 00:16:D4:01:F9:13  
          inet addr:10.12.66.147  Bcast:10.12.67.255  Mask:255.255.254.0
          inet6 addr: fe80::216:d4ff:fe01:f913/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:877 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:286936 (280.2 KB)  TX bytes:138260 (135.0 KB)
          Interrupt:19 Base address:0x6000 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.12.66.0      *               255.255.254.0   U     0      0        0 eth0
default         cs1721-oak-lang 0.0.0.0         UG    0      0        0 eth0

```

If anyone can help me based on this info, I'd be really grateful. The phone passthrough seems to work with windows xp, so I know that it works. This seems to be a problem between that hardware setup and my software setup in ubuntu. I'm running 7.10.

---

### Post by unutbu on 2008-03-18
"When I tried using the phone passthrough on the desktop, I again got a 10.12.68.xxx ip address, but it worked fine."

Great! Please post the result of the "route PRINT" and "ipconfig" when the desktop is connected through the passthrough.

Am I right in assuming that you can't just leave the desktop connected through the passthrough and let your laptop use your desktop's port? 

Is so, we're going to have to find a configuration which works with the 10.12.68.xxx address you are being assigned when the laptop (or any computer) is connected through the passthrough.

I think it would be a big help to see what a working routing table looks like on a connection using the passthrough, and it sounds like you can find that out using your desktop...

---

### Post by spectrevk on 2008-03-18
[http://img.photobucket.com/albums/v475/teninjas/passthrough.gif](http://img.photobucket.com/albums/v475/teninjas/passthrough.gif)

I've tried a static IP using 10.12.66.3 as the gateway, but that doesn't work either. :(

---

### Post by unutbu on 2008-03-18
Boot up the laptop with eth0 connected to the passthrough.
Make sure that DHCP has successfully assigned you an ip address by running ifconfig and looking for what comes after "inet addr". It should be a number of the form 10.12.68.xxx.

Then run:

```

sudo route add -net 10.12.68.0 netmask 255.255.255.0 eth0
sudo route add default gw 10.12.66.3 eth0

```

Try pinging the gateway by number:
```

ping -c1 10.12.66.3

```

If it works, great. If it doesn't, post the output to
```

ifconfig 
route

``` Please don't tell me it doesn't work without posting some output.

---

### Post by Leed on 2008-03-19
Sry for the double post, connection problems

---

### Post by Leed on 2008-03-19
I have the same problem and really don't believe it is his fault. I suspect that something went wrong in an Ubuntu Update...

I have a work pc here, and since yesterday my wired network doesn't work anymore. Wireless still works, but if I leave for a long break (akka lunch), wireless loses its connection and won't find any networks anymore. 

I've been using Ubuntu on this machine since December 2007 without problems. The Wired calbe itself is fine, works perfect when I plug it into another machine. 

what I did was set Wired connection manually to dhcp (without nm-applet), then restarted in Windows, there the connections both worked. Then after restarting in Ubuntu again, I set the network connection back to roaming mode... so far it works again. Hope you also got a dual boot (everyone should)

---

### Post by spectrevk on 2008-03-19
> **unutbu said:**
>  Please don't tell me it doesn't work without posting some output.

Not a problem. Now that I know there's a way to at least temporarily get the laptop online, I can copy/paste with ease.

```

spectrevk@spectrevk-laptop:~$ sudo route add -net 10.12.68.0 netmask 255.255.255.0 eth0
[sudo] password for spectrevk:
spectrevk@spectrevk-laptop:~$ sudo route add default gw 10.12.66.3 eth0
SIOCADDRT: No such process
spectrevk@spectrevk-laptop:~$ ping -cl 10.12.66.3
ping: bad number of packets to transmit.
spectrevk@spectrevk-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:01:F9:13  
          inet addr:10.12.68.79  Bcast:10.12.68.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe01:f913/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5809 (5.6 KB)  TX bytes:15726 (15.3 KB)
          Interrupt:19 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:78:B2:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:546 (546.0 b)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5588 (5.4 KB)  TX bytes:5588 (5.4 KB)

spectrevk@spectrevk-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.12.68.0      *               255.255.255.0   U     0      0        0 eth0
10.12.68.0      *               255.255.255.0   U     0      0        0 eth0

```


Is it possible that there is an issue with the DHCP Client? How would I set which dhcp client program I am using? I figure I can install them easily enough, but I want to be sure that I can control which one is active.

---

### Post by unutbu on 2008-03-19
All of our problems center on this line.

```

spectrevk@spectrevk-laptop:~$ sudo route add default gw 10.12.66.3 eth0
SIOCADDRT: No such process

```

This line is telling the laptop that all ip packets not destined for the internal 
10.12.68.0 network should be sent to the gateway, whose ip address is 10.12.66.3.

I'm not sure why the laptop is choking on this. If we can figure that out, I think you'll be home free.

When your routing table looks closer to this:
```

Kernel IP routing table
Destination     Gateway              Genmask         Flags Metric Ref    Use Iface
10.12.68.0      *                 255.255.255.0         U     0      0        0 eth0
default        10.12.66.3               0.0.0.0         UG    100    0        0 eth0

```

you should be able to access the internet.

---

### Post by unutbu on 2008-03-19
This thread is eerily similar:
[http://ubuntuforums.org/showthread.php?t=584521](http://ubuntuforums.org/showthread.php?t=584521)


Ask your sysadmin what is the IP address of the switch/router on the other end of your passthrough. Try substituting that for  10.12.66.3.

---

### Post by unutbu on 2008-03-19
```

#!/usr/bin/perl
use strict;
use warnings;

for (0..255) {
    my $gw="10.12.68.$_";
    print "sudo route add default gw $gw eth0\n";
    open(CMD,"sudo route add default gw $gw eth0 2>&1|");
    my $wrongip=0;
    while (my $line=<CMD>) {
	if ($line=~m/SIOCADDRT/) {
	    $wrongip=1;
	    last;
	}
    }
    close(CMD);
    if (!$wrongip) {
	print "The gateway is $gw\n";
	exit;
    }
}

```

Save this in a file. Call it test.pl.
Call chmod to make it executable:
```

chmod 755 test.pl

```
Then run it from the command line. It should spit out a lot of lines like

```

sudo route add default gw 10.12.68.xxx eth0

```

It should stop and print

```

The gateway is 10.12.68.yyy

```

when it finds the gateway. This *may* be able to find your gateway for you. If it doesn't end by telling you your gateway, then we'll have to reconsider your netmask. Your network sysadmin should have all this information, however. Finding it yourself it just for thrills.

---

### Post by spectrevk on 2008-03-19
Okay, so I tried running the script and at first, it didn't return a gateway. Then on a hunch, I went into Synaptic Package Manager and tried installing dhcpcd, bootp, and pump. If I was thinking, I would have tried each one and then tried again from there, but as it is, I'm not sure which one fixed this.

In any case, I tried a network restart and the script suddenly worked!

Then, just to see, I tried pinging google, and suddenly I could!

Before I declare a victory, I'm going to try a standard reboot of the PC and see if I still have access. Either way, thanks a billion for all of your patience.


WEIRD!

I just restarted, and at first...same problem. I tried network restart...same problem. I tried restart and running the script, and suddenly it worked again. Here's what I get right now for ifconfig and route:

```

spectrevk@spectrevk-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:01:F9:13  
          inet addr:10.12.68.83  Bcast:10.12.68.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fe01:f913/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:289245 (282.4 KB)  TX bytes:50666 (49.4 KB)
          Interrupt:19 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:78:B2:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:546 (546.0 b)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5736 (5.6 KB)  TX bytes:5736 (5.6 KB)

spectrevk@spectrevk-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.12.68.0      *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.12.68.1      0.0.0.0         UG    0      0        0 eth0

```

---

### Post by unutbu on 2008-03-19
Well, knock me over with a feather!
I'm so happy for you. Yay!:popcorn:

---

### Post by unutbu on 2008-03-19
The proper gateway is (obviously) 10.12.68.1. Now you can probably use WICD to configure eth0 and you can dispense with my perl script.
Then the machine should just work upon boot.

---

### Post by spectrevk on 2008-03-19
The sysadmin popped over and we tried it out a little...I still can't quite get it to do it automatically, but somehow manually setting the Gateway to that address (while keeping DHCP) works like a charm. In order to set a manual gateway in WICD I have to enable static IP though. He made up a script for it, but the script doesn't seem to execute, since it needs a password or something.

Bah. I'll mess with it later. At least I know a way around this now. I can't thank you enough.

Now, onto my other config issues (suspend/hibernate tops the list)! I've got some documentation to look up. :)

---

### Post by unutbu on 2008-03-19
Ok, happy journeys.

---

