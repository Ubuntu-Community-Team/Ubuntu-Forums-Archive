---
title: "Ethernet Converter"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by giddy1945 on 2007-08-30
I have an ethernet converter made by Buffalo (Model# WLI-TX4-G54HP).  I show a 90% signal.  I cannot believe how great this thing works!!!  I sure wish I could actually surf the net!!  I have no internet.  What is up with that?  Is it my bios?  Is it the $oft machine I'm running?  Is it.....my hurting BRAIN?  Please, Please, Please, someone who knows the answer (solution) to my 3 month long problem, enlighten me.  I am about to attach this computer to the front bumper of my truck, and take advantadge of my awsome auto insurance.  (alternative...$oft...ugly $oft)!

---

### Post by noob12 on 2007-08-30
Could you please post the output of these commands so people can help diagnose it?

```

sudo lshw -C network

sudo iwlist scan

iwconfig

ifconfig -a

```

---

### Post by dulbirakan on 2007-08-30
Are you sure you can login to the network correctly?

It might be some authentication problem with the network or the owner of the network might be employing IP/MAC filtering.

---

### Post by giddy1945 on 2007-08-30
Yes, I sure will, noob12, and as for IP/MAC filtering, dulbirakan, I don't know.  I do have a MAC laptop that successfully utilizes the net on the same free public network.
     On an other note, I thought that my Linux box would see this setup as a "wired" set up since it is ethernet.  I had never had any problem configuring it as a wired system before.  
     I will post the outputs of those cammands at oproximately 4PM CST. (2200 ZULU)
     Thank you.

---

### Post by giddy1945 on 2007-08-30
root@mint:/home/tilton# sudo lshw -c network 
Hardware Lister (lshw) - B.02.08.01 
usage: lshw [-format] [-options ...] 
       lshw -version 
 
        -version        print program version (B.02.08.01) 
 
format can be 
        -html           output hardware tree as HTML 
        -xml            output hardware tree as XML 
        -short          output hardware paths 
        -businfo        output bus information 
 
options can be 
        -class CLASS    only show a certain class of hardware 
        -C CLASS        same as '-class CLASS' 
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. ) 
 
root@mint:/home/tilton# sudo iwlist scan 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
root@mint:/home/tilton#  iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
root@mint:/home/tilton# ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:13:20:4D:C0:5F   
          inet addr:1.1.1.2  Bcast:1.1.1.255  Mask:255.255.255.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:13298 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:14257 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:3274611 (3.1 MiB)  TX bytes:1150288 (1.0 MiB) 
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2028 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2028 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:155824 (152.1 KiB)  TX bytes:155824 (152.1 KiB) 
 
root@mint:/home/tilton#

---

### Post by noob12 on 2007-08-30
I just took a look at an actual description of the product you have and I was completely on the wrong track.

I now see that the device you have is supposed to connect to your wired ethernet port on your host computer.  You are supposed to configure it to connect to your access point separately using a web-based config tool.  Once you configure that it should just work as your wired connection.  Your Ubuntu host will not consider it a wireless device.

Now that that is cleared up, let's try to get you up and running.

Your IP address to be 1.1.1.2 manually, apparently following Buffalo's directions.  I'm not sure if you noticed that after configuring the ethernet converter unit through the web interface they tell you to go back to using DHCP (obtain an IP address automatically).  If within the web interface, the converter says it is properly connected and authenticated to the access point, you should then go to System | Administration | Network on your Ubuntu box and select Automatic Configuration (DHCP).

Then disable and re-enable networking.  See if that starts to work then.

If not, please post the output of these
```

cat /etc/network/interfaces

route -n

cat /etc/resolv.conf

```

---

### Post by giddy1945 on 2007-08-30
Thank you for taking the time to help me.  Here is the iformation you have requested.  I followed your instructions exactly, although I know one cannot always do that.


root@mint:/home/tilton# cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 
 
auto eth1 
iface eth1 inet dhcp 
 
auto eth2 
iface eth2 inet dhcp 
 
auto ath0 
iface ath0 inet dhcp 
 
auto wlan0 
iface wlan0 inet dhcp 
 
 
iface eth0 inet dhcp 
address 1.1.1.2 
netmask 255.0.0.0 
 
 
root@mint:/home/tilton# route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
root@mint:/home/tilton# cat /etc/resolv.conf 
cat: /etc/resolv.conf: No such file or directory 
root@mint:/home/tilton#

---

### Post by noob12 on 2007-08-30
Your problem is primarily just configuring the Buffalo box.  Once you have that working you can then just set your Ubuntu box to acquire an address automatically and plug it in.

Have you already verified that the ethernet converter box has established a connection and authenticated to your access point?

Make sure to do that first.

Also, when you set up the ethernet converter box, did you configure the converter box (in its web interface) to obtain an IP address automatically (for itself)?  or did you configure a manual one (on the ethernet converter box)?  You don't want to leave it with the 1.1.1.1 address that it comes with by default.  You need to change it to acquire an address automatically on your actual subnet from your access point (or alternatively you need to set an address manually that is actually on the local subnet that your access point sits on.) Typically this will be something like 192.168.1.something.  Note that I am just talking about the ethernet converter at this point.  Not your Ubuntu box.

It would be helpful to know what subnet you do use on your LAN if you know that.

---

### Post by giddy1945 on 2007-08-30
By," verified that the ethernet converter box has established a connection and authenticated to your access point", you mean established a signal, right?  I do not know what authenticated to the access point means.

Also,"the local subnet that your access point sits on" is the actuall IP address of the public wireless service, correct?

And my subnet mask according to the converter is 255.255.255.0

Maybe I just need to know what the "server's" IP is, or maybe I'm just putting all these values in the wrong places.

I'm just so confused.  I'll read up on the different types of IP.

Thanks again.

---

### Post by noob12 on 2007-08-30
> **giddy1945 said:**
> By," verified that the ethernet converter box has established a connection and authenticated to your access point", you mean established a signal, right?  I do not know what authenticated to the access point means.

Established a signal and if there is any authentication (WEP / WPA) key required by the access point, that you have that setup right too.  If it is an open public access point, typically there is no key required.

> 
Also,"the local subnet that your access point sits on" is the actual IP address of the public wireless service, correct?


You are probably best off setting the converter to acquire its IP address automatically using DHCP from the access point.

> And my subnet mask according to the converter is 255.255.255.0

That will probably be correct because it is the most common one, but you will get one automatically using DHCP as well.

> 
Maybe I just need to know what the "server's" IP is, or maybe I'm just putting all these values in the wrong places.

I'm just so confused.  I'll read up on the different types of IP.

Thanks again.


Sorry for confusing you.   I think you're pretty close to having things working if you can just configure your converter properly.

---

### Post by giddy1945 on 2007-08-30
I just got some information about my public server.  The server does not use a static IP (DHCP only), and they do not use "broadcast DNS" whatever that is.  So......that being said, do you think I should put this thing in storage until I get into a house with an actuall hard wire, or can it actually be configured?

There is no WEP or any other encryption.

Thanks again.

---

### Post by noob12 on 2007-08-30
I would say that if you have been able to configure the ethernet converter to connect to the access point you are pretty close.

I think you are saying that you have done that.

The public access point you are using will normally have a local private subnet like 192.168.1.0 or similar on which they assign specific addresses to clients (like yours) by DHCP.  The access point itself will typically have an address like 192.168.1.1 and will serve as the gateway router as well as providing the DHCP to clients on the net.

It would be nice to know these values because we could try manually configuring an address for your Ubunto host, but we will try to proceed anyway.

Based on the Buffalo docs, all you should need to do now is plug in your Ubuntu host to the ethernet converter and configure it to use DHCP to acquire its address, gateway and dns.

Let's give it one last shot.  Try the following.  

```

xhost +
sudo gedit /etc/network/interfaces

```

Find the part where (earlier you said) it says
```

iface eth0 inet dhcp
address 1.1.1.2
netmask 255.0.0.0 

```
Change this to read as follows instead:
```

auto eth0
iface eth0 inet dhcp

```
Save and exit.

Then run 
```

sudo /etc/init.d/networking restart

```

Hopefully you should get a connection then.  If you make partial progress it's worth continuing.  If not, I probably won't be able to add much and you might try calling Buffalo's tech suppport.

---

### Post by giddy1945 on 2007-08-31
I totally erased everything except "auto eth0
iface eth0 inet dhcp"  in the /etc/network/interfaces.

Now it takes a few minutes for my root terminal to come up.
When I attempted the restart, this is the result:

root@mint:/home/tilton# xhost + 
access control disabled, clients can connect from any host 
root@mint:/home/tilton# sudo gedit /etc/network/interfaces 
 
(gedit:5859): GnomeUI-WARNING **: While connecting to session manager: 
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed. 
root@mint:/home/tilton# sudo /etc/init.d.networking restart 
 
root@mint:/home/tilton# sudo /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5015 
removed stale PID file 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
Listening on LPF/eth0/00:13:20:4d:c0:5f 
Sending on   LPF/eth0/00:13:20:4d:c0:5f 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 



Do I need to restore all the other values in the inerfaces file, or does it really matter? When I tried to configure my Ralink chipset, I read that taking the lines with "lo" out would do.

This "sleeping" crap is the same thing I was dealing with before.  NO!  Don't sleep, no sleeping.  It's time to work, I sais.

---

### Post by noob12 on 2007-08-31
First, do **not** remove the lines related to **lo** (the loopback) interface from your /etc/network/interfaces file.  A lot of things on your system won't work if you do that.  It is ok to remove everything except that, but that isn't your issue.

The behavior you experienced indicates that you didn't get a DHCP address assignment from the access point via the converter.

This means one of three things: (1) that you haven't actually established the connection from the converter to the access point properly or (2) the converter isn't conveying the requests up to the access point  or (3) the access point isn't actually public, e.g. will only accept some set of MAC addresses.

I'm assuming you can eliminate (3).  The access point is actually public, not just appearing so.  This leaves (1) or (2) as the likely candidates.   If we had the information about the local subnet and gateway served by the access point, we could try manually configuring an address on your Ubuntu host.   

By using the connection configuration/status web page of the converter box you should be able to determine connection status (a box that says "Wireless Status") between the converter box and the access point and confirm you are actually connected to the access point.  It should say something like "Connected".  I think the most likely problem is that the converter box has not actually connected to the access point. 

What I'd suggest is that you go through the User Guide for your converter box, pages 10-15, carefully step by step again.   As part of that procedure you need to set the ip address on your Ubuntu host manually to 1.1.1.2 and subnet to 255.255.255.0.  During that procedure you will configure the converter box to connect to the access point and you should confirm the wireless status is connected.  At the end of that procedure, after you have confirmed that the converter is actually connected to the access point, you need to set your Ubuntu box back to acquiring an address automatically, and then restart networking, as you did following my previous posting.  

I'm sorry but I don't really have any further ideas.  As far as I can tell your Ubuntu host is working fine and you just need to configure the converter box to work.  I'll try to answer any questions you have but I'm not likely to be much more help. :(

---

### Post by giddy1945 on 2007-08-31
Thank you so much for your help.  You have answered many questions pertaining to past issues.  I will revert everything in the interfaces file to proper values.  I will post the results of the setup.  I understand if you or anyone else has no further ideas.  I did read in another forum that the author could not get the OS to get any DHCP offers from the converter, so he had to resort to a static IP.  This will not be possible in my case, so if this one last thing does or does not work I will let you know.

Thanks again.  I'll be posting results around 1150 CST (1750 ZULU).

---

### Post by noob12 on 2007-08-31
You too can use a manually configured IP if you can find out the subnet and gateway address for your access point.

---

### Post by giddy1945 on 2007-08-31
Thanks again for your help.  I have spoken with the Sprint guys, and I have come to the conclution that I cannot be supported.  I will be getting out of the Navy in 7 months, and come back to Linux at that time (when I have a wired network).  For now, in storage my Linux box goes.  Till then, Fare well.

---

### Post by giddy1945 on 2007-08-31
Scratch that last post.  I had heard a while back that I could use my MAC to get on the net.  The problem was, in my mind, that I would be sacrificing a $1500 computer.  I wanted to sacrifice a hundred dollars worth of gear instead.  Turns out I was mistaken about the whole thing.  For three months I was banging my head against the desk, because of configuring issues like these, and I never once tried to connect the ethernet to my mac.  My mac is not hot.  It is not spinning 1000 mph.  Minimal heat is being disbursed.  It is just sitting quietly in the back ground while I checkout 4 months worth of new linux software...well, new to me.  

Thanks for trying noob12.
I just saved $115 on my computer hardware by switching to mac.

---

### Post by noob12 on 2007-08-31
Glad you are up and running in any case.  Sorry I couldn't help with your converter box.

---

