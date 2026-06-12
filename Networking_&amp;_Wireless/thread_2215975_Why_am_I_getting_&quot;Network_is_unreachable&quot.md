---
title: "Why am I getting &quot;Network is unreachable&quot;?"
date: 2014-04-09
forum: Networking &amp; Wireless
---

### Post by phil215 on 2014-04-09
Hi Forum,
    I installed Ubuntu 12.04 LTS alongside WinXP for a dual boot system on a PC yesterday.
Ubuntu failed to connect to the network, but WinXP had no trouble at all.
I tried editing the wired connection information, using the manual option to input the relevant numbers for IP addr., Netmask, Gateway and DNS server.
Still no joy.
The network card is being recognised because the MAC addr. is displayed.
Attempting to ping the gateway gives "connect: Network is unreachable".
The routing table remains empty.
How best to proceed with getting Ubuntu talking to the network?

(P.S. I have successfully achieved the same dual boot system on my laptop and that works without a hitch.)

---

### Post by m-dw on 2014-04-09
There isn't enough information to answer your question.  Could you post the output of ifconfig -a?

---

### Post by varunendra on 2014-04-10
Plus the output of -
```
sudo lshw -numeric -C network
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by phil215 on 2014-04-10
Thanks for your reply m-dw. At the moment I can't supply the output verbatim but by comparison with the laptop the obvious missing line is the one beginning "inet" for eth0.
So there are only 7 lines on the PC for this device instead of 8. The loopback settings (8 lines) are present and correct.

When the wired connection method "Automatic (DHCP)" failed, I decided to try "Manual". However, I left "Search domains" blank and didn't add anything under the "Routes" button. Could this be a possible reason for the current connection failure?
Ubuntu didn't complain so it would appear that those fields were not mandatory.
If possible I would prefer to use automatic, but any troubleshooting that gets the PC connected would be good.
(Btw, it's not my machine, it belongs to a friend.)

Varunendra, I don't have access to the problem PC at the moment, but hope to run the lshw command tomorrow.

From memory, the NIC is probably the TP-Link TF-3200 and from initial investigations before my post I believe the Sundance driver is installed.
I'll get back with more as soon as I can. Thanks for your patience.

---

### Post by SeijiSensei on 2014-04-10
Pick an LAN address in the subnet your router supports that is not in use.  Let's say you choose 192.168.1.97. Now open a terminal and enter:
```
sudo /sbin/ifconfig eth0 192.168.1.97 netmask 255.255.255.0 broadcast 192.168.1.255
```
Now try to ping the router; let's say its address is 192.168.1.1.  Does that work?  If so, try this:
```
sudo ip route add default via 192.168.1.1
```
Now try to ping Google's DNS server at 8.8.8.8.  How about that?

If all this works correctly, then we just have to diagnose why your machine doesn't get an address at boot.

---

### Post by phil215 on 2014-04-12
Okay, here's the gen:
Output of "ifconfig -a"
```

eth0   Link encap:Ethernet  HWaddr 00:23:cd:00:19:83  
          inet6 addr: fe80::223:cdff:fe00:1983/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1225 (1.2 KB)  TX bytes:4156 (4.1 KB)

lo       Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2032 (2.0 KB)  TX bytes:2032 (2.0 KB)

```

Output of "sudo lshw -numeric -C network"
```

  *-network
       description: Ethernet interface
       product: IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY [13F0:200]
       vendor: Sundance Technology Inc / IC Plus Corp [13F0]
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 31
       serial: 00:23:cd:00:19:83
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sundance driverversion=1.2 duplex=full latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100Mbit/s
       resources: irq:9 ioport:b400(size=128) memory:de000000-de0001ff memory:dff00000-dff0ffff

```

Thank you SeijiSensei, that was a real guru reply. Yes, the first command allowed me to ping the router! The second command allowed me to ping the Google DNS server!
So far, so good. As you say, it's now a case of determining why the TCP/IP configuration is not being set at boot time. Looking forward to your next diagnostic suggestion.

---

### Post by varunendra on 2014-04-13
I would be curious to see what SeijiSensei thinks, everything on the driver and connectivity part looks solid to me.

My suggestion would be to try resetting the /etc/network/interfaces file (or wherever you tried manual configuration mentioned in your first post) to default and check router settings to make sure it is able to deliver a DHCP offer and the Ubuntu machine is able to request and accept it.

But I would wait for SeijiSensei's post which may offer more precise instructions on what to check/try.

---

### Post by 7sbaV8Kt5PTh on 2014-04-14
Just a quick look shows that there is no IP address assigned to eth0 for ipv4.

You might want to do a "netstat -nr" to see where the default route points.  It should show the IP address of your router going out to the Internet.

If you are using DHCP addressing from your router, it might not be working properly.

---

### Post by SeijiSensei on 2014-04-14
Those of us who learned Unix the hard way some decades ago were forced to rely on ifconfig and route!

As John observes, there is no address assigned to eth0 in the ifconfig results you posted.  So let's start by seeing if you can get an address with DHCP.  I assume you didn't need to set up static addressing for XP, so you shouldn't need it for Ubuntu either.

In /etc/network/interfaces, you should have only this entry for the Ethernet connection:
```

auto eth0
iface eth0 inet dhcp

```

If you do need to use static addressing, follow the steps described here: [https://help.ubuntu.com/12.04/serverguide/network-configuration.html#ip-addressing](https://help.ubuntu.com/12.04/serverguide/network-configuration.html#ip-addressing).

---

### Post by Iowan on 2014-04-14
> **SeijiSensei said:**
> 
In /etc/network/interfaces, you should have only this entry for the Ethernet connection:[s]Might not be that much if NM is running the show.
(or did I miss the manual configuration?)[/s]
Never mind... I'm curious if the Manual configuration method (in NM) might be part of the problem.

---

### Post by SeijiSensei on 2014-04-14
Indeed I just looked at /etc/network/interfaces on this machine with an active Ethernet connection and a disabled wifi adapter.  I created the wired connection via NetworkManager. Only the stanza for the localhost interface appears in the interfaces file.  NM must manage eth0 separately.

So perhaps you should try removing any stanza you created for eth0 from the interfaces file, then try setting up the Ethernet adapter using NetworkManager.

---

### Post by phil215 on 2014-04-15
Okay folks, please pay attention. Post #1 "The routing table remains empty." In other words
the result of "netstat -rn" was just the column headings, no data. This has to be a big
clue as to the source of the problem. Which script(s) is/are responsible for writing to the routing table?

Also, in post #4 I gave a pretty clear description of what was odd about the output from "ifconfig -a", when
the machine in question was not to hand. What software is responsible for setting up the addresses here?

Thanks for getting back to this thread SeijiSensei, your suggestions are highly valued!
I have to report that the interfaces file is deficient and looks like this at the moment:
```

auto eth0
iface eth0 inet dhcp

```

So, no entries for eth0, and I'm tempted to ask the question:
What software is responsible for setting up the NIC device in interfaces?

Btw, I confirm that the PC addressing is obtained by DHCP under WinXP.
I would like to use the same method under Ubuntu!

In the meantime I have been researching and trying various things.
e.g. sudo apt-get install ethtool.
The result was disappointing:
"Package ethtool is not available."
"E: Package 'ethtool' has no installation candidate."
(Any suggestions as to how to fix this?)

However, I had success with nm-tool. Output of "nm-tool"

```

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sundance
  State:             unavailable
  Default:           no
  HW Address:        00:23:CD:00:19:83

  Capabilities:

  Wired Properties
    Carrier:         off

```

So, the NIC is not in a happy state under Ubuntu, yet this same card is allowing me to make this post under WinXP. I would be very grateful for any help to resolve this situation urgently or my friend might loose patience with this software. If Ubuntu can't get this machine online soon then I fear the O/S will have to be uninstalled and replaced by some expensive alternative, i.e. Win7 or Win8. Please don't let that happen!!

What's going on here? The same installation disk was used for this PC and my laptop, yet the results are very different.
My laptop connects to the internet in about five seconds under Ubuntu, this PC still can't connect under Ubuntu.
Grrr.

---

### Post by SeijiSensei on 2014-04-16
As I said above, if NetworkManager is handling the connection, you won't see a stanza for eth0 in /etc/network/interfaces.

Did you configure your PC using the NetworkManager GUI application?  That's by far the simplest method. I just did that today for a machine I moved.  I clicked on the network icon in the panel and chose to create a new wired connection.  I didn't have to do anything more than that.  It created the connection and used DHCP to configure the adapter.  I don't use stock Ubuntu with the Unity interface, but this technique works on both Kubuntu and Lubuntu.  I suspect it works with regular Ubuntu as well.

---

### Post by phil215 on 2014-04-16
Actually, SeijiSensei I missed your post #11 simply because it was on the next page and, being in a hurry, I overlooked it - sorry. Anyway, I have some good news. This post is being composed under Ubuntu on the PC which presented such an annoying problem! How did I do it? Well, not using the GUI, that failed even when I tried deleting the wired connection and created a new one. So, I edited interfaces to include the eth0 stanza and restarted networking...and it worked!! Easy once you know how.:)
Thanks to everyone who has helped me to resolve this connection problem.
How do I mark this thread as solved?

---

### Post by varunendra on 2014-04-16
> **phil215 said:**
> How do I mark this thread as solved?

Using the "Thread Tools" link above the top post on this page. Would be more helpful for others if you could also post the current contents of your **/etc/network/interfaces** file.

---

### Post by phil215 on 2014-04-16
Thanks Varun.
Correction:
In post #12 the code box showing the contents of "/etc/network/interfaces" was wrong.
It should have been:
```

auto lo
iface lo inet loopback

```
Apologies for that.

Now the file contains these lines:
```

auto eth0
iface eth0 inet dhcp

auto lo
iface lo inet loopback

```

The command to get connected was this:
```

sudo /etc/init.d/networking restart

```

To comply with your request Varun, the second line (the missing one!) in the output of "ifconfig -a" now takes the form:
```

inet addr:192.168.hhh.hhh  Bcast:192.168.hhh.255  Mask:255.255.255.0

```
The hhh represents up to three digits of the host part of the IP address.
So, for example:
```

inet addr:192.168.1.97  Bcast:192.168.1.255  Mask:255.255.255.0

```
The third line is now the one beginning "inet6" as in post #6, and there are no other changes.

There's one outstanding issue with the PC setup that I noticed after sending post #14. Although it now has internet connectivity, the desktop icon for networking is the 'arc plus radii', not the double arrow - one pointing up (upstream) and one pointing down (downstream).
The "Connection Information" menu item is greyed-out and the GUI tells me the machine is offline. No so, I made post #14 under those conditions, so the GUI is being deceptive.
It's not a high priority but I would like to see this corrected in the near future. If you know how to correct this please tell me!
However, now that internet connectivity has been achieved I'm willing to consider this thread solved.

---

### Post by SeijiSensei on 2014-04-16
I don't think the GUI network applet monitors devices started from /etc/network/interfaces.  You might as well remove it from the panel to avoid confusion.

---

### Post by steeldriver on 2014-04-16
... or you can edit /etc/NetworkManager/NetworkManager.conf and change

```

[ifupdown]
managed=false

```

```

[ifupdown]
managed=true

```

to tell network-manager not to ignore interfaces defined via /etc/network/interfaces

You should bear in mind that they are intrinsically different services though, and people HAVE had problems making them 'play nice'

---

### Post by phil215 on 2014-04-17
Thanks for your input SeijiSensei and steeldriver. As suggested, I set "managed=true" and the GUI is responding as expected. I'll watch for problems, but it would be an advantage to know if these occur in any particular area. In other words steeldriver, could you please provide a link to a thread that shows how others have had problems trying to make the different services inter-operate?

---

