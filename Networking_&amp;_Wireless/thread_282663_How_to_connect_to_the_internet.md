---
title: "How to connect to the internet?"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by Yochai on 2006-10-23
Hello,

I just install Ubuntu 6.06 on my computer. I was very happy doing that. The first thing that I did after that is of course trying to surf a little. But...

I can't connect to the internet. :( 

How can I connect to the internet?

Thanks,
Yochai.

---

### Post by mahy on 2006-10-23
> **Yochai said:**
> Hello,

I just install Ubuntu 6.06 on my computer. I was very happy doing that. The first thing that I did after that is of course trying to surf a little. But...

I can't connect to the internet. :( 

How can I connect to the internet?

Thanks,
Yochai.

Uhm, sorry, but this is quite a bad post. How are supposed to help you if you don't share more details? Do you use windows? How do you connect from there? LAN? Wireless? Dial-up? USB modem with DSL or cable connection?

---

### Post by Yochai on 2006-10-23
Thanks for the fast reply. Sorry, here are some details.

I have 2 operation systems installed. WinXP and Ubuntu. 
I have a cable connection to the internet.

Yochai.

---

### Post by mahy on 2006-10-23
> **Yochai said:**
> 
I have a cable connection to the internet.

This is much better but not enough. ;) The cable goes to modem and then what? What's the connection between modem and your computer? Is it an ethernet cable? (HINT: Ethernet cable looks like a telephone cable, but is thicker and its plugs are bigger.) Or is it a USB cable?

---

### Post by Yochai on 2006-10-23
Mmm... well... it is a Ethernet cable (99%).

Thanks for you patience,
Yochai.

---

### Post by mahy on 2006-10-23
> **Yochai said:**
> Mmm... well... it is a Ethernet cable (almost surely).

Thanks for you patience,
Yochai.

Ok, so open a terminal (you'll find it in the menu -> Accessories or so i believe) and type 

sudo ifconfig

You should see the names of your network devices and some details about them. You'll probably have some device named "eth0" or "eth1". (it depends on how many network cards are found in your machine). Type

dhclient eth0 (or eth1 of necessary)

and watch the output. When it's finished, you should be able to surf. N.B. if the ifconfig is only giving you the loopback device (named "lo"), try "sudo ifconfig eth0 up" and/or the same with eth1.

---

### Post by Yochai on 2006-10-23
I did it. The 'ifconfig' and after it the 'dhclient', the output seems to be o.k. (I can post it if necessary.)

But, still, **I can't connect to the internet**.

Yochai.

---

### Post by Gargamella on 2006-10-23
if you use a router try 

sudo pppoeconf

in terminal you will be able to set a dsl connection

---

### Post by mahy on 2006-10-23
> **Yochai said:**
> I did it. The 'ifconfig' and after it the 'dhclient', the output seems to be o.k. (I can post it if necessary.)

But, still, **I can't connect to the internet**.

Yochai.

Yes please, post the output of the two commands.

---

### Post by Yochai on 2006-10-23
Here is the output of the two commands:

**yochai@yochai-desktop:~$ sudo ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:0D:61:95:29:13
          inet addr:172.28.12.105  Bcast:255.255.255.255  Mask:255.255.224.0
          inet6 addr: fe80::20d:61ff:fe95:2913/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:36799 (35.9 KiB)  TX bytes:6941 (6.7 KiB)
          Interrupt:209 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

**yochai@yochai-desktop:~$ sudo dhclient eth0**
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0d:61:95:29:13
Sending on   LPF/eth0/00:0d:61:95:29:13
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.208.192.1
bound to 172.28.12.105 -- renewal in 1227 seconds.
**yochai@yochai-desktop:~$**

---

### Post by mahy on 2006-10-23
> **Yochai said:**
> 
DHCPACK from 10.208.192.1
bound to 172.28.12.105 -- renewal in 1227 seconds.
**yochai@yochai-desktop:~$**

try: ping 172.28.12.105

if it succeeds (packets return), try pinging something outside. e.g. [www.ubuntu.com](www.ubuntu.com)

---

### Post by Yochai on 2006-10-23
Pinging the first **succeeded**. Pinging outside **failed**.

---

### Post by Yochai on 2006-10-23
> **Gargamella said:**
> if you use a router try 

sudo pppoeconf

in terminal you will be able to set a dsl connection

Seems to be not relevant. Anyway - the wizard failed.

---

### Post by mahy on 2006-10-24
> **Yochai said:**
> Pinging the first **succeeded**. Pinging outside **failed**.

Strange. Seems like a problem between modem and your ISP. However, you're saying it works in windows. Are you sure it behaves just like a normal network connection in windows? Don't you have some special handling program there (which is absent in Linux)? I'm asking this because i dunno what else might be wrong.

---

### Post by Yochai on 2006-10-24
> **mahy said:**
> Strange. Seems like a problem between modem and your ISP. However, you're saying it works in windows. Are you sure it behaves just like a normal network connection in windows? Don't you have some special handling program there (which is absent in Linux)? I'm asking this because i dunno what else might be wrong.

When I connect to the internet in Windows, there is a cable dialer of the ISP that pop up and do the connection (but, as far as I know, this is the normal/common kind of cable connection). You think it is related?

---

### Post by ClarkePeters on 2006-10-24
Not sure about cable, I just did this:

from command line type:

$sudo pppoeconf eth0

then it asked me a couple of questions and whether or not I wanted to connect automatically on boot--I said yes, and I've been on the internet ever since.

I have a DSL (ADSL) connection, so maybe this won't help, but geesh, it was sooo easy once someone pointed it out to me.

---

### Post by c0rrupt3d_fate on 2006-10-24
> yochai@yochai-desktop:~$ sudo ifconfig
eth0 Link encap:Ethernet HWaddr 00:0D:61:95:29:13
inet addr:172.28.12.105 Bcast:255.255.255.255 Mask:255.255.224.0
inet6 addr: fe80::20d:61ff:fe95:2913/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:152 errors:0 dropped:0 overruns:0 frame:0
TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:36799 (35.9 KiB) TX bytes:6941 (6.7 KiB)
Interrupt:209 Base address:0xc000

with an output like that, it looks like you should have no problems browsing, I use a liveCD called backtrack (useful withall of its network security utilities) and when you start it, to prevent from immediately being detected on the network you have to manually enable your network devices

---

### Post by c0rrupt3d_fate on 2006-10-24
The method I always used to gain access to the network,
and internet access aswell (if the network has a connection)
is the ifconfig -a command, that will give you a list of the curent interfaces you have available on your comptuer,
usually this would be named eth0
following that, I would do ifconfig eth0 up
after that, I would do a dhcpcd eth0 to gain an ip address
after that command has completed, you should be good to go

---

### Post by mahy on 2006-10-24
> **Yochai said:**
> When I connect to the internet in Windows, there is a cable dialer of the ISP that pop up and do the connection (but, as far as I know, this is the normal/common kind of cable connection). You think it is related?

Yes it is! :mrgreen:

The dialing software submits username and password, and you have to do the same in Linux. However, i've got no experience with such devices so i'll leave it to experts.

---

### Post by Yochai on 2006-10-24
> **ClarkePeters said:**
> Not sure about cable, I just did this:

from command line type:

$sudo pppoeconf eth0

then it asked me a couple of questions and whether or not I wanted to connect automatically on boot--I said yes, and I've been on the internet ever since.

I have a DSL (ADSL) connection, so maybe this won't help, but geesh, it was sooo easy once someone pointed it out to me.

Thanks, I tried it with no success. (I've a cable connection.)

---

### Post by Yochai on 2006-10-24
> **mahy said:**
> Yes it is! :mrgreen:

The dialing software submits username and password, and you have to do the same in Linux. However, i've got no experience with such devices so i'll leave it to experts.

**Sounds very reasonable to me.** I would like to thank you very much for your very good and patient help.

**I'll will be very happy to have more help from someone who can continue from this point.** This is my first Linux-based system and I have no intention giving up because of technical problems. 

**Help needed.**


Thanks a lot,
Yochai.

---

### Post by ClarkePeters on 2006-10-25
If you're still not getting connected, have you thought about searching out a local ubuntu group? Maybe someone could walk you through over the phone, or even look at your system. It must be a pain trying to work without a connection, it's so important. You can find local support almost anywhere, even here in Taiwan. :)

---

### Post by ClarkePeters on 2006-10-25
p.s.
check your internet service provider, there's probably someone who knows about linux systems who can walk you through--for free hopefully.

---

### Post by mips on 2006-10-25
> **Yochai said:**
> **Sounds very reasonable to me.** I would like to thank you very much for your very good and patient help.

**I'll will be very happy to have more help from someone who can continue from this point.** This is my first Linux-based system and I have no intention giving up because of technical problems. 

**Help needed.**


Thanks a lot,
Yochai.

What brand/model cable modem do you have ???
Do you perhaps have a router lying around you can connect to the cable modem ??
Who is your ISP and provide a link to their website please ???

---

### Post by Yochai on 2006-10-25
> **ClarkePeters said:**
> p.s.
check your internet service provider, there's probably someone who knows about linux systems who can walk you through--for free hopefully.

My ISP are so mainstream -- they do not support Linux. Do you believe it? I checked their forum and found some inadequate solutions. I'll take a look again, now that I got some experiance in this problem.

Hopefully, after I/We will solve the problem I'll send them a "How to..." manual to put on their website. It will help other people here to enjoy Ubuntu easier than me. ;)

---

### Post by jhofmann on 2006-10-25
I wonder if you have a dns (domain name server) configured?  My dns is listed in a file named /etc/resolv.conf.  If your isp gave you a dns address to use, make sure that it is in the resolv.conf file.

---

### Post by Yochai on 2006-10-25
> **ClarkePeters said:**
> If you're still not getting connected, have you thought about searching out a local ubuntu group? Maybe someone could walk you through over the phone, or even look at your system. It must be a pain trying to work without a connection, it's so important. You can find local support almost anywhere, even here in Taiwan. :)

Fortunately, I've also WinXP on my system. ;) 

But, yes, I can't work on the Ubuntu installation now because I don't know how to connect to the internet.

I checked the local Ubuntu site in my country (Israel), the link to the forum there bring me here. I guess no local support available for me. ](*,)

---

### Post by mips on 2006-10-25
> **Yochai said:**
> Fortunately, I've also WinXP on my system. ;) 

But, yes, I can't work on the Ubuntu installation now because I don't know how to connect to the internet.

I checked the local Ubuntu site in my country (Israel), the link to the forum there bring me here. I guess no local support available for me. ](*,)

I recall dealing with a Israeli cable modem issue before. Can you provide the details I requested please. Although I cannot read Hebrew I'll see what I can do.

---

### Post by Yochai on 2006-10-25
> **ClarkePeters said:**
> p.s.
check your internet service provider, there's probably someone who knows about linux systems who can walk you through--for free hopefully.

I already called them three times, they do not give technical support for Linux system. They have some written manual but it is not adequate for Ubuntu-linux.

What a world... :-?

---

### Post by Yochai on 2006-10-25
> **mips said:**
> What brand/model cable modem do you have ???
Do you perhaps have a router lying around you can connect to the cable modem ??
Who is your ISP and provide a link to their website please ???

I have Motorola SB4200 Surfboard cable modem.
Router? I don't think I've one.
My ISP name is "Internet Zahav", it is in Israel, their website is in Hebrew [http://www.zahav.net.il/shop/]("http://www.zahav.net.il/shop/")

More info?

Thanks in advance,
Yochai.

---

### Post by mips on 2006-10-25
Please read links in the post below before you just jump in and do the first thing that comes to mind.

Have a look at this, apparently it applies to all cable isp's in Israel. [http://www.whatsup.co.il/modules.php?op=modload&name=Reviews&file=index&req=showcontent&id=17](http://www.whatsup.co.il/modules.php?op=modload&name=Reviews&file=index&req=showcontent&id=17)

PPTP should be available in the repositories if i'm not mistaken, dunno the status of L2TP

Do you know what software you used in Windows to do the authentication ? Was it pptp or vpn as I have also heard of a vpn based setup.

**Please feedback on what guide worked for you.**

---

### Post by mips on 2006-10-25
Read these, the solutions are there. Check the dates on the guides as things might have changed, so don't do things you don't have to do.

[http://iglu.org.il/amit/cable/](http://iglu.org.il/amit/cable/)
[http://mirror.hamakor.org.il/archives/linux-il/02-2004/8701.html](http://mirror.hamakor.org.il/archives/linux-il/02-2004/8701.html)
[http://cables2.netvision.net.il/linux/](http://cables2.netvision.net.il/linux/)  adapt for Zahav
[http://www.technion.ac.il/~eyalroz/linux_cable_pptp.html](http://www.technion.ac.il/~eyalroz/linux_cable_pptp.html)
[http://www.whatsup.org.il/doc/CABLES-DHCP-PPTP-HOWTO.html](http://www.whatsup.org.il/doc/CABLES-DHCP-PPTP-HOWTO.html) This one is more readble for people that read left to right.
[http://www.mail-archive.com/linux-il%40cs.huji.ac.il/msg24725.html](http://www.mail-archive.com/linux-il%40cs.huji.ac.il/msg24725.html) Zahav is mentioned in here
[http://www.technion.ac.il/~eyalroz/linux_cable_pptp.html](http://www.technion.ac.il/~eyalroz/linux_cable_pptp.html)
[http://l3ech.net/cables_linux.php](http://l3ech.net/cables_linux.php)        Looks good, also see links at bottom
[http://l3ech.net/cables_linux_l2tp.php](http://l3ech.net/cables_linux_l2tp.php)   Looks good, also see links at bottom

If you see anything for Debian then it most likely works on Ubuntu as well.

IGNORE, key words for future searches as i always battle to find these: 
.co.il Israel Hebrew Cable Modem Cablemodem Cable-Modem Actcom Aquanet Barak Bezeq International Bezint Golden Kavei Zahav Kzahav Internet Gold Inzahav Israserv NetVision Technion Kavey-Zahav

---

### Post by qra on 2006-10-25
> **Yochai said:**
> Hello,

I just install Ubuntu 6.06 on my computer. I was very happy doing that. The first thing that I did after that is of course trying to surf a little. But...

I can't connect to the internet. :( 

How can I connect to the internet?

Thanks,
Yochai.

with the firefox open go to menu open location annd write about:config
in the new window in filter write ipv6
go to value and double click to change from false to true

That could be your solution as it was mine but I still have problems to connect and update the packages as well as with the evolution.

Tks

---

### Post by Yochai on 2006-10-29
> **mips said:**
> Read these, the solutions are there. Check the dates on the guides as things might have changed, so don't do things you don't have to do.

[http://iglu.org.il/amit/cable/](http://iglu.org.il/amit/cable/)
[http://mirror.hamakor.org.il/archives/linux-il/02-2004/8701.html](http://mirror.hamakor.org.il/archives/linux-il/02-2004/8701.html)
[http://cables2.netvision.net.il/linux/](http://cables2.netvision.net.il/linux/)  adapt for Zahav
[http://www.technion.ac.il/~eyalroz/linux_cable_pptp.html](http://www.technion.ac.il/~eyalroz/linux_cable_pptp.html)
[http://www.whatsup.org.il/doc/CABLES-DHCP-PPTP-HOWTO.html](http://www.whatsup.org.il/doc/CABLES-DHCP-PPTP-HOWTO.html) This one is more readble for people that read left to right.
[http://www.mail-archive.com/linux-il%40cs.huji.ac.il/msg24725.html](http://www.mail-archive.com/linux-il%40cs.huji.ac.il/msg24725.html) Zahav is mentioned in here
[http://www.technion.ac.il/~eyalroz/linux_cable_pptp.html](http://www.technion.ac.il/~eyalroz/linux_cable_pptp.html)
[http://l3ech.net/cables_linux.php](http://l3ech.net/cables_linux.php)        Looks good, also see links at bottom
[http://l3ech.net/cables_linux_l2tp.php](http://l3ech.net/cables_linux_l2tp.php)   Looks good, also see links at bottom

If you see anything for Debian then it most likely works on Ubuntu as well.

IGNORE, key words for future searches as i always battle to find these: 
.co.il Israel Hebrew Cable Modem Cablemodem Cable-Modem Actcom Aquanet Barak Bezeq International Bezint Golden Kavei Zahav Kzahav Internet Gold Inzahav Israserv NetVision Technion Kavey-Zahav

Well, the belows seems to be the most relevant.
[http://cables2.netvision.net.il/linux/](http://cables2.netvision.net.il/linux/)  adapt for Zahav
[http://l3ech.net/cables_linux_l2tp.php](http://l3ech.net/cables_linux_l2tp.php)   Looks good, also see links at bottom

But, although I did my best to make it work -- I failed! (And I've some experience with programs belive me.) This is too much for me, and I'm quite **desperate **from Linux/Ubuntu. :( 

I hope someone (maybe from **Israel**) will see this post.

SOS
Yochai.

---

### Post by mips on 2006-10-29
Yochai,

Could I possibly suggest you contact a the authors of those guides via email and also look at local linux user groups/forums for assistance.

> **Yochai said:**
> Well, the belows seems to be the most relevant.
[http://cables2.netvision.net.il/linux/](http://cables2.netvision.net.il/linux/)  adapt for Zahav
[http://l3ech.net/cables_linux_l2tp.php](http://l3ech.net/cables_linux_l2tp.php)   Looks good, also see links at bottom

But, although I did my best to make it work -- I failed! (And I've some experience with programs belive me.) This is too much for me, and I'm quite **desperate **from Linux/Ubuntu. :( 

I hope someone (maybe from **Israel**) will see this post.

SOS
Yochai.

---

### Post by Yochai on 2006-10-29
**Thanks god. Solution found.** Indeed, a local manual. I would like to thank all the users that post in this thread. **Special thanks** to [**mahy**]("http://www.ubuntuforums.org/member.php?u=176527") and [**mips**]("http://www.ubuntuforums.org/member.php?u=8017") for the patient and kind support.

Here is a summary of the problem and the solution (for other users).
**Problem: **
I just installed Ubuntu and I can't connect to the internet.
I'm from israel and I've a cable connection.
**Solution:**
follows the instructions (in Hebrew) appear [**here**]("http://penguin.org.il/doku.php?id=%D7%9E%D7%93%D7%A8%D7%99%D7%9B%D7%99%D7%9D:%D7%94%D7%AA%D7%97%D7%91%D7%A8%D7%95%D7%AA+%D7%9C%D7%90%D7%99%D7%A0%D7%98%D7%A8%D7%A0%D7%98+%D7%91%D7%A4%D7%A1+%D7%A8%D7%97%D7%91").

*Users that are not from israel may find some helpful info in this thread as well.*

Thanks a lot,
Yochai.

--
I guess I'll have now a lot of time for other Ubuntu problems and stuff. Thanks mahy. Thanks mips.

---

### Post by mips on 2006-10-29
> **Yochai said:**
> **Thanks god. Solution found.** Indeed, a local manual. 

Yochai, thanks for the feedback, I'm sure it will benefit other users as well.

Whats the chances of an english translation and posting it here ? Just so we can get the gist of it incase some others might experience problems with it. Unfortunately I don't read Hebrew otherwise I would have done so.

---

### Post by Yochai on 2006-10-30
Here is what one should do (in English). 
NOTE: This manual is relevant only for ones that use cable connection (with pptp protocol only). This is relevant mainly to users in Israel.

Lets start...

Open terminal and enter as a root
> sudo -i  #will prompt you for a password

type
> dhclient

then type
> wget [http://welcome.hot.net.il/ISPpages/012/012linux.tar.gz](http://welcome.hot.net.il/ISPpages/012/012linux.tar.gz) #download file to current directory

and then
> tar -xvzf 012linux.tar.gz #extract(x) with text feedback(v) a gz(z) file(f) named 012linux.tar.gz

Now you have a new folder named "012linux", enter it by
> cd 012linux

Open the file "cstart" with a text editor and replace USERNAME by your username (as given by the ISP), fix IFACE to be "eth0" (with out the quote). replace the address cablepns.012.net.il with your ISP's pptp server address, and the nameserver addresses by the one given to you by your ISP (call and ask them). It should look like this:

------------
bin/bash

USERNAME=put here your user name!!
IFACE=eth0
/sbin/ifdown $IFACE
/sbin/ifup  $IFACE
...
/sbin/route add -host pns.inter.net.il gw $CABLEGW
------------

in the same file change the line
CABLEGW=$(grep routers /var/lib/dhcp/dhclient-$IFACE.leases ...)
to 
CABLEGW=$(grep routers /var/lib/dhcp3/dhclient.$IFACE.leases ...)
(there is a "3" added there and a "-" that change to "." look carefully)

Update the file /etc/ppp/pap-secrets with your username and password

Apply ./cstart, simply by typing 
>./cstart

check connection by
> ping -c3 [www.google.com](www.google.com)

you should get:
...3 packets transmitted, 3 received, 0% packet loss

If you do get it: congradulation you are connected!

Now, in the file "cstart" do the following
add a "#" to the line
cp -f pptp-linux /sbin
so it will be 
#cp -f pptp-linux /sbin

delete the dot and the slash at the begining of the pptp-linux command so it will look like this:
pptp-linux cablepns.012.net.il debug user $USERNAME mtu 1460 mru 1460 defaultroute

That is all.
Anyone that want to format this manual, so it will look better is welcome.

Thanks, and good luck to us all,
Yochai.

-----
The short manual translated from hebrew from [http://penguin.org.il/doku.php?id=%D7%9E%D7%93%D7%A8%D7%99%D7%9B%D7%99%D7%9D:%D7%94%D7%AA%D7%97%D7%91%D7%A8%D7%95%D7%AA+%D7%9C%D7%90%D7%99%D7%A0%D7%98%D7%A8%D7%A0%D7%98+%D7%91%D7%A4%D7%A1+%D7%A8%D7%97%D7%91](http://penguin.org.il/doku.php?id=%D7%9E%D7%93%D7%A8%D7%99%D7%9B%D7%99%D7%9D:%D7%94%D7%AA%D7%97%D7%91%D7%A8%D7%95%D7%AA+%D7%9C%D7%90%D7%99%D7%A0%D7%98%D7%A8%D7%A0%D7%98+%D7%91%D7%A4%D7%A1+%D7%A8%D7%97%D7%91)
(see there for copyrights)

---

### Post by mips on 2006-10-30
Yochai thanks for the translation !

---

### Post by Yochai on 2006-10-30
> **mips said:**
> Yochai thanks for the translation !

You are welcome. Hopefully, this thread will help other new Ubuntu users.

Connecting to the internet is a very fundemental issue, I wonder why the Ubuntu's developers/team (I guess there is one) don't address this in a simpler way (maybe some automatization?). I'm sure that problems like this make many users to discard Ubuntu (and other Linux distributions as well).

:KS The feeling here is that Ubuntu has a strong momentum. Maybe I'm naive, but I'm really hope to see it as some alternative to Windows in the future. 

All the best,
Yochai.

---

### Post by slbruce on 2006-12-26
Hi

I have also been having this problem.  However the link at [http://welcome.hot.net.il/ISPpages/012/012linux.tar.gz](http://welcome.hot.net.il/ISPpages/012/012linux.tar.gz) does not work.  If anyone has this file and has got it to work please reply or PM me.  I am at my wit's end trying to connect to Internet Zahav from Linux and am on the verge of giving up :( 

Thanks

Spencer

---

### Post by mips on 2006-12-27
The whole site seems to be down. Have you PM'ed/Mailed the person that posted that link ???


> **slbruce said:**
> Hi

I have also been having this problem.  However the link at [http://welcome.hot.net.il/ISPpages/012/012linux.tar.gz](http://welcome.hot.net.il/ISPpages/012/012linux.tar.gz) does not work.  If anyone has this file and has got it to work please reply or PM me.  I am at my wit's end trying to connect to Internet Zahav from Linux and am on the verge of giving up :( 

Thanks

Spencer

---

### Post by slbruce on 2006-12-27
Yes, I PM'd him (don't know his email) but he has not replied.

Spencer

---

### Post by larytet on 2007-01-27
here how it goes in my case (012+Hot combination):
 
to download the tar.gz 
At this point you are connected to the LAN of ISP 
(try dhclient to get IP address) and you have IP address from ISP
command ifconfig will show inet addr:172.x.x.x  This is local IP address you got from the ISP (do they use NAT/proxy ?)
try to ping hot.net.il you should see that DNS resolves - IP address of the server
If so far is ok try to pull the tar.gz

wget [http://welcome.hot.net.il/ISPpages/012/012linux.tar.gz](http://welcome.hot.net.il/ISPpages/012/012linux.tar.gz)

If there is no such file or you work not with Hot+012 try this link 
[http://www.gomyplace.com/id/012linux.tar.gz](http://www.gomyplace.com/id/012linux.tar.gz) (you will need "normal" not PPTP connection or use Windows to download the file) 
This is 48K file

Alternative is to connect Linux to non-cable connection and apt-get install pptp-linux and pptpconfig



Next step is scipt - I attach the scripts here
[http://www.gomyplace.com/id/cstart](http://www.gomyplace.com/id/cstart)
[http://www.gomyplace.com/id/cstop](http://www.gomyplace.com/id/cstop)

Next crucial link for you is this one [http://penguin.org.il/doku.php?id=%D7%9E%D7%93%D7%A8%D7%99%D7%9B%D7%99%D7%9D:%D7%94%D7%AA%D7%97%D7%91%D7%A8%D7%95%D7%AA+%D7%9C%D7%90%D7%99%D7%A0%D7%98%D7%A8%D7%A0%D7%98+%D7%91%D7%A4%D7%A1+%D7%A8%D7%97%D7%91](http://penguin.org.il/doku.php?id=%D7%9E%D7%93%D7%A8%D7%99%D7%9B%D7%99%D7%9D:%D7%94%D7%AA%D7%97%D7%91%D7%A8%D7%95%D7%AA+%D7%9C%D7%90%D7%99%D7%A0%D7%98%D7%A8%D7%A0%D7%98+%D7%91%D7%A4%D7%A1+%D7%A8%D7%97%D7%91)
Unfortunately this site is about always down. I was lucky and made a copy from a table there 

Netvision DNS	    212.143.212.143   194.90.1.5 	
PPTP/L2TP 		cable.netvision.net.il
			
Golden Internet 	DNS	192.116.202.222 213.8.172.83 	
PPTP 	213.8.8.112 	pns.inter.net.il
			
Actcom 	DNS	192.114.47.4 192.114.47.52	
PPTP\L2TP 	192.117.122.13 	username.c.actcom.net.il
			
KaveyZahav 	DNS	212.117.129.5 212.117.129.3 	
PPTP 	212.199.26.28 	cablepns.012.net.il
			
Barak 	DNS	212.150.49.10 62.90.133.233 	
PPTP 	62.90.133.58 	pns.barak.net.il
			
Bezek Beinleumi 	DNS	192.115.106.35 192.115.106.10 	
PPTP/L2TP 	212.179.61.77 	gch.bezeqint.net
			
Israserv 	DNS	192.115.0.100 192.115.3.100 	
PPTP 	192.117.195.250 	

Urbis 	DNS	192.118.6.3 	
PPTP 	172.26.255.241 	cable.urbis.net.il
	
Aquanet 	DNS	192.117.240.10 192.117.240.3	
PPTP 	213.57.50.250 	cable.aquanet.co.il

Technion 	DNS	132.68.1.2 132.68.1.9 	
PPTP 	132.68.254.109 	ccdis3.technion.ac.il

Univ TA 	DNS	132.66.32.10 132.66.16.2 	
L2TP 	132.66.4.125 	lns.tau.ac.il
			
Hebrew Univ 	DNS	128.139.6.1 128.139.4.3 	
PPTP 	132.64.10.2 	vpn.huji.ac.il

Now your next step is figure out DNS server 
Connect Windows and run ipconfig /all 
Check the list IP addresses, find your provider, make sure that at least DNS server subnet resembles the one in the table (the table is outdated)

At this point your now DNS IP address, you have files pptp-linux, cstart, cstop from the tar.gz above on your disk.

Now let's edit a couple of files. First file is cstart 
Pay attention that you likely have to replace username (ric) and (less likley) interface (eth0)  in the scripts. 
```

USERNAME=ric
IFACE=eth0

```

Another place to change is cablepns.012.net.il in the line 
```

./pptp-linux cablepns.012.net.il debug user $USERNAME mtu 1460 mru 1460 defaultroute

```
Check that table above 
For example,cablepns.012.net.il is Ok for KaveyZahav
```

KaveyZahav 	DNS	212.117.129.5 212.117.129.3 	
PPTP 	212.199.26.28 	cablepns.012.net.il

```
Now line 
```

CABLEGW=$(grep routers /var/lib/dhcp3/dhclient.$IFACE.leases | tail -n 1 | cut -d ";" -f1 | cut -d "t" -f3 | cut -d "o" -f4 | cut -d ' ' -f2)

```
This thing depends on the distribution
In Ubuntu filename /var/lib/dhcp3/dhclient.eth0.leases In other distros it can be different
We are done with cstart
Now file /etc/ppp/options
There is a line "auth" replace it with "noauth"
Now file /etc/ppp/pap-secrets 
Section outbound connections
*               yourPasswordHere

Now run cstart and ping google

---

### Post by mips on 2007-01-27
> **larytet said:**
> 
Now your next step is figure out DNS server 


You can usually get this from the support section of the ISPs website or alternatively you can do a google search for [B]*ISP Name* DNS server
[/B]

---

### Post by larytet on 2007-02-01
I just installed Linksys WiFi router (about $60 in Israel)
Option L2TP works with the cable company 
The setup is slightly tricky
- find out IP address of the L2TP server (call support of your ISP)
- connect using the first option - DHCP
- when the router connects and shows IP address on  the status page (something like 172.x.x.x) switch to L2TP, fill in user name and password and IP of the L2TP server
In a minute you are connected.

---

### Post by dbraun86 on 2007-04-23
This is really complicated for new users. And a turn-off.
Someone should make a GUI for connecting with cables.

---

