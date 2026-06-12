---
title: "Okies, this is weird."
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by Sonique on 2005-11-26
I've read a lot of posts in this forum, I have read loadsa help files but nothing seems to help.

This is my problem:
I have a Sony Laptop [PCG-C1VE] with ubuntu fully installed but I cannot get onto the internet. I have this wired network card which you plug into the pci port [i think that what it is called]. I plug into a router which is fully functional. The problem is which ever way i try to connect to internet [dhcp or static ip] i just get told that the "eth0" is idle. 

I have tried the following:
got to System>Administration>Networking>Ethernet connection>properties and done both static and dhcp.
gone into a terminal and opened up /etc/network/interfaces and tried making it use a static ip and a dhcp. And then restarted /etc/init.d/networking both times.

Supposely networking is very simple in ubuntu, so can anyone tell me what i have done wrong or at least point be in a direction.

:)Cheers:)

---

### Post by mips on 2005-11-26
Try this guide, [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

and post your results as you go along.

---

### Post by Sonique on 2005-11-27
when i put: [COLOR="RoyalBlue"]ifconfig eth0[/COLOR] in the terminal i don't get the part [COLOR="DarkOrange"]inet addr:10.2.3.7[/COLOR] not even the inet addr bit.

Also when i put [COLOR="RoyalBlue"]route -n[/COLOR], I dont get any numbers in the table, I just get the column names. This I think means it hasnt got any ip addresses.

So i did [COLOR="RoyalBlue"]sudo dhclient eth0[/COLOR] and i got:

[COLOR="DarkOrange"]Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DCHP](http://www.isc.org/products/DCHP)

sit0: unknow hardware address type 776
sit0: unknow hardware address type 776
Listening on LPF/eth0/00:00:86:3c:38:96
Sending on LPF/eth0/00:00:86:3c:38:96
Sending on Socket/fallback
DCHPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DCHPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DCHPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DCHPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DCHPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DCHPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DCHPOFFERS recieved
No working leases in persistent database - sleeping.[/COLOR]

Does this mean anything to anyone?

---

### Post by Sonique on 2005-11-27
Oh just to let you know: /etc/netowrk/interaces looks like [without the lines starting with '#':

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

---

### Post by Lambert on 2005-11-27
Can you post your /etc/network/interfaces file here

Keep the format of everything  but where you have personal data replace it with an X.

example

wireless-essid xxxxx

I'm guessing you use wep so is it open or shared? hexadecimal or ascii key format

One thing you can try is to use a static ip to ensure connection and then we can move forward with dhcp.

---

### Post by mips on 2005-11-27
In System>Administration>Networking  Is the 'enable this connection' box ticked ?
Deactivate the card and reactivate.

What brand&model card are you using ?

If you are battling to get the output from linux to a working machine copy and pste the output of the commands to a stiffy or memory stick.

---

### Post by Sonique on 2005-11-27
Hey Lambert, thanks for the help so far,
All there is in /etc/network/interfaces is this:
[COLOR="DarkOrange"]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp[/COLOR]
I guess that means I am missing stuff.

I don't know if i use wep because i don't know what it is. sorry. I have tried to do static ip but with no success. I just need to clarify:
in System>Administration>Networking>Ethernet connection>Properties
when you have static ip address:
ip address is the one you make up instead of the router doing it,
subnet mask is the same as my windows xp computer's one when connecting to the router
gateway address is the 'default gateway' on my windows xp computer

----

Hey mips, thanks also for your posts,
In System>Administration>Networking I didn't see a 'enable this connection' box ticked. It may be because I think i am using hoary version of ubuntu [of that means something, i borrowed it of a friend]. It does say under "Ethernet connection", "The interface eth0 is active" - is that the same as what you said?

The network card that I am using is a 3Com Megahertz 10/100 LAN CardBus PC Card and the model number is: 3CXFE575BT. Here is a picture of it: [http://www.deltacomputers.com/images/XJACK-BT.jpg]("http://www.deltacomputers.com/images/XJACK-BT.jpg")

The reason why i didn't use my memory stick is because ubuntu thinks that the "media probably doesnt have any data" or something on those lines.

Cheers

---

### Post by Lambert on 2005-11-27
wep is actually encryption for a wireless network. I see you say plugged into a router. I assumed it may be an ap/router but that may be a bad assumption.

I don't know much about using a device set up like you have but you can try this from the command line.

sudo ifconfig eth0 down

sudo ifconfig eth0 address <static_ip> netmask 255.255.255.0 broadcast <static ip, change last .xxx to .255> up

sudo route add default gw <router ip> eth0

then try to ping 

ping <router ip>

ping 216.239.57.99

If these are succesful then try to ping [www.google.com]("http://www.google.com")

Post ping results and results of the command ifconfig.

---

### Post by Sonique on 2005-11-27
on the bit:

sudo ifconfig eth0 address <static_ip> netmask 255.255.255.0 broadcast <static ip, change last .xxx to .255> up

its replies saying:

address: Host name lookup failure

---

### Post by Sonique on 2005-11-27
I think I will just update to the new ubuntu and see if it will work on that.

---

### Post by Lambert on 2005-11-27
If you ran it the exact way I wrote it then shame on me for not being clearer.

Where I put <> required input from you

<static ip> = a static ip in your router's range 
<static ip, change last .xxx to .255> = what ever you set as your static except the end would be .255

so the actual command would look more like this.

 sudo ifconfig eth0 address 192.168.0.10 netmask 255.255.255.0 broadcast 192.168.0.255 up

---

### Post by Sonique on 2005-11-28
I didn't write exactly what you wrote, I did it how you were supposed to do it [ you were clear enough thanks ]. I'm just upgrading to Breezy at the moment [ having a little problem with the display ], then I'll retry what you told me to do, hopefully it will work.
Thanks

---

### Post by wrtrdood on 2005-11-28
Since you mention you are upgrading, it might be a good thing at the network config prompt where it will most likely complain about no DHCP to do the manual config.  At this point you can plug in just about anything but a 192.168.X.X number is probably best and it should match the internal address of the router.  That is, the first three numbers (separated by the dot) should be the same.  Use 255.255.255.0 for the netmask.  Your gateway will be the router's address.  If the router is like most, it's getting its external address (the one seen on the Internet) from your ISP.  This is not the one you want.  You want the address of the port that connects to your local area network.  You'll also be asked for the DNS server.  You need at least one.  You can use what is supplied by your ISP or any public DNS server.  Once these are defined, you should be able to get online.  Good luck.

---

### Post by D1G1T4L on 2005-12-31
i have exactly same problem, i dont know what to do, it doesnt show inet address, even though my router assigns one in the router settings

---

### Post by D1G1T4L on 2005-12-31
[QUOTE=Sonique]on the bit:

sudo ifconfig eth0 address <static_ip> netmask 255.255.255.0 broadcast <static ip, change last .xxx to .255> up

its replies saying:

address: Host name lookup failure[/QUOTE]

same thing happens to me!

---

