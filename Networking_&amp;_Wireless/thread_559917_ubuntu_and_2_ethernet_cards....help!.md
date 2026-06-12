---
title: "ubuntu and 2 ethernet cards....help!"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by davidsuma on 2007-09-25
I am a newbie to linux and need some direction from the pro...

Here it goes:

I have two machines: Linux(ubuntu) and XP.

Currently my linux is connected to the internet/DSL.
This machine also has 2 ethernet cards.

Now, I want my XP to be able to share files/printer with the Linux, BUT not the internet.

People from other sites told me to utilize samba and crossover cable to do this.

But since i'm a novice i need a step by step instruction to make it happen.

Can anyone help me please?...:(

Thank you.

---

### Post by noob12 on 2007-09-26
OK.  So no bites.  I'll try to help.

Let's make sure we both understand the situation.

Is your ubuntu box already connected and working on the Internet?

Is it the case that you actually do not want the XP box to have access to the Internet or you'd settle for it not having access?

Does your DSL modem/router support multiple clients?

Do you have a crossover cable already or are you going to purchase one?  Do you have enough money to buy a hub and two regular cables instead?

Can you post the output of the following commands run from you Ubuntu box while it is connected to the Internet:
```

ifconfig -a

cat /etc/network/interfaces

```

---

### Post by davidsuma on 2007-09-27
Is your ubuntu box already connected and working on the Internet?
Ans: My ubuntu is already connected to the internet & it's running just fine.

Is it the case that you actually do not want the XP box to have access to the Internet or you'd settle for it not having access?
Ans: I actually do not want the XP box to access the internet.

Does your DSL modem/router support multiple clients?
Ans: My DSL modem only has one (1) ethernet outlet to connect.
         And I don't have a router.

Current comp layout:

[internet]---->[DSL modem]---->[Unix box]---crossover cable---->[XP box]

Do you have a crossover cable already or are you going to purchase one? Do you have enough money to buy a hub and two regular cables instead?
Ans: I already have a crossover cable CAT 5 & I don't want to buy hub or cables if
         it's not necessary.

Underneth are results of commands you asked me to post.

I appreciate you trying to help me... Thank you.

==================================================
**Result of 'ifconfig -a' command:**

eth0      Link encap:Ethernet  HWaddr 00:50:BA:B9:D6:10  
          inet6 addr: fe80::250:baff:feb9:d610/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2774438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1950664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4123330804 (3.8 GiB)  TX bytes:161842830 (154.3 MiB)
          Interrupt:10 Base address:0x6c00 

eth1      Link encap:Ethernet  HWaddr 00:A0:CC:54:E6:EA  
          inet6 addr: fe80::2a0:ccff:fe54:e6ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:1393 dropped:0 overruns:0 carrier:2786
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:110 (110.0 b)
          Interrupt:3 Base address:0xe400 

eth0:avah Link encap:Ethernet  HWaddr 00:50:BA:B9:D6:10  
          inet addr:169.254.7.152  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x6c00 

eth1:avah Link encap:Ethernet  HWaddr 00:A0:CC:54:E6:EA  
          inet addr:169.254.11.95  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:158733 (155.0 KiB)  TX bytes:158733 (155.0 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:75.60.187.197  P-t-P:75.60.187.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2549010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1771050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3766709303 (3.5 GiB)  TX bytes:102766195 (98.0 MiB)

==================================================
[B]
Result of 'cat /etc/network/interfaces' command:[/B]

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 192.168.1.40
netmask 255.255.255.0


iface eth1 inet dhcp
address 192.168.1.40
netmask 255.255.255.0


iface eth2 inet static
address 192.168.1.40
netmask 255.255.255.0

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth2



auto eth1

==================================================

---

### Post by noob12 on 2007-09-27
OK.

You are using PPPOE over the eth0 interface.  The eth1 interface is the port to which you are going to connect via crossover to the XP box.  Conect them if you haven't already.

The configuration you have for eth0 in /etc/network/interfaces specifying DHCP along with an address and mask doesn't really make sense, but this isn't  important right now as you are really just using it for PPPOE.

You should run a firewall and you will want to set that up before you start file and printer sharing service.  We can limit the filesharing service to listen only on  the internal net, but it is a good idea to run a firewall on the Ubuntu host in your situation.  We'll return to this later.

For now we will just get the connection between the Ubuntu and Windows host working over the crossover cable. 

You will be configuring the eth1 interface statically with the address 192.168.2.1 and netmask 255.255.255.0 and no gateway.  You will also need to configure the XP machine with the fixed address 192.168.2.2 on this net.

For the Ubuntu host you can do this in System | Administration | Network or by running 
```

sudo gedit /etc/network/interfaces

```

In the text editor replace the section for eth1 with the following:
```

auto eth1
iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0

```
You should remove the line near the bottom of the file that says **auto eth1**; we've moved it up with this section.

Save the file and exit.

This configuration will be used automatically on subsequent boots, but  for now run
```

sudo ifdown eth1
sudo ifup eth1

```
to have this take effect immediately.

Post the output of the commands **ifconfig -a** and **cat /etc/network/interfaces** and **sudo ethtool eth1** so I can check them.

Now go to the Windows box.   In **Control Panel | Network Connections**, find and select your wired connection.  Right click and select Properties.   On the General tab, find the line that says TCP/IP properties select that and select Properties on that panel.  A new panel pops up.  On that panel find the radio button that says Use the following IP address and select it.  In the boxes enter the following  IP Address: 192.168.2.2  , Subnet mask: 255.255.255.0, no gateway.  (If it requires you to enter a gateway address enter 192.168.2.1).  Hit OK on the panels until they all go away.

Now from the windows box, get a CMD window (if you don't know how, got to Start | Run ... | and in the box type **cmd**).  In the CMD window type ping 192.168.2.1.  You should see 4 responses.

If we can get to this point you have the connectivity between these two boxes setup.  We can move on.  Otherwise, we need to diagnose the situation till you have this working.

---

### Post by davidsuma on 2007-09-27
noob12:

I did everything you instructed, but when i do "ping 192.168.2.1" in my XP box cmd,
it says "Request time out". Does it mean that the two have not established a connection?

Here is the results of commands requested:

==============================================
**ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:50:BA:B9:D6:10  
          inet6 addr: fe80::250:baff:feb9:d610/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2776773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1953238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4125085027 (3.8 GiB)  TX bytes:162281539 (154.7 MiB)
          Interrupt:10 Base address:0x6c00 

eth1      Link encap:Ethernet  HWaddr 00:A0:CC:54:E6:EA  
          inet6 addr: fe80::2a0:ccff:fe54:e6ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:237 errors:1 dropped:0 overruns:0 frame:0
          TX packets:32 errors:1528 dropped:0 overruns:0 carrier:3056
          collisions:0 txqueuelen:1000 
          RX bytes:34098 (33.2 KiB)  TX bytes:7100 (6.9 KiB)
          Interrupt:3 Base address:0xe400 

eth0:avah Link encap:Ethernet  HWaddr 00:50:BA:B9:D6:10  
          inet addr:169.254.7.152  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x6c00 

eth1:avah Link encap:Ethernet  HWaddr 00:A0:CC:54:E6:EA  
          inet addr:169.254.11.95  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:159541 (155.8 KiB)  TX bytes:159541 (155.8 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:75.60.187.197  P-t-P:75.60.187.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2551107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1773231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3768403112 (3.5 GiB)  TX bytes:103102559 (98.3 MiB)
===================================================
**cat /etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 192.168.1.40
netmask 255.255.255.0


auto eth1
iface eth1 inet dhcp
address 192.168.2.1
netmask 255.255.255.0


iface eth2 inet static
address 192.168.1.40
netmask 255.255.255.0

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth2
=================================================
**sudo ethtool eth1**

Settings for eth1:
No data available
=================================================

---

### Post by noob12 on 2007-09-27
For one thing you need to go back and edit the /etc/network/interfaces file.  I had written

```

iface eth1 inet [COLOR="Red"]static[/COLOR]

```

You still have **dhcp** where it should say static.  So please fix that.  Then repeat the ifdown/ifup commands.

But  it also looks like we may have more fundamental issues with your eth1 interface because the **sudo ethtool eth1** should have provided something.  It may not be a recent enough driver to support ethtool.

Can you check and see if you have a link light on the back of the port where the crossover cable is connected?

Aslo, can you please post the output of:

```

sudo lshw -C network

```

---

### Post by davidsuma on 2007-09-27
**sudo lshw -C network**

  *-network:0             
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:b9:d6:10
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:ec00-ecff iomemory:ff1ffc00-ff1ffcff irq:10
  *-network:1
       description: Ethernet interface
       product: LNE100TX
       vendor: Lite-On Communications Inc
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth1
       version: 20
       serial: 00:a0:cc:54:e6:ea
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.14 ip=192.168.2.1 latency=64 multicast=yes
       resources: ioport:e400-e4ff iomemory:ff1ff800-ff1ff8ff irq:3

================================================

Changes have been made to correct 'static' <--- sorry about that...i missed it.
I did the ifup/ifdown thingy....this time however it gives the following message:

**sudo ifdown eth1**
postconf: fatal: open /etc/postfix/main.cf: No such file or directory

[B]sudo ifup eth1
[/B]postconf: fatal: open /etc/postfix/main.cf: No such file or directory

BUT, i did "ping 192.168.2.1" again from my XP box. This time it gives
replies. :) This is good rite???...

I've also checked the cable connection behind both PC...all ethernets green light
thingy lighted up.

---

### Post by noob12 on 2007-09-27
Yes.  All good.  You have basic connectivity.  Will send more instructions later today.

---

### Post by davidsuma on 2007-09-27
Hi Noob12:

I went ahead and followed the samba tutorial I found at:
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

Where it shows you how to setup file sharing between ubuntu and xp.

To my surprise i am able to access my ubuntu shared folder FROM XP box.

BUT, for some odd reasons, I can't see my XP shared folder FROM Ubuntu network folder.
When i click [Places]---->[Network]....a network folder window opened but
I can't see my window xp shared folder in there.....it contain nothing.

What's going on????.... :( For a moment I thought i had it all figured out.

O well, i just wait for you then....

---

### Post by davidsuma on 2007-09-27
Dooooh!!!!

It's not working again now??...can't ping from XP.

Geee.... :(

---

### Post by davidsuma on 2007-09-27
I just found out that if i stop "firestarter" then i can ping my ubuntu from XP.

That's weird... at least to me as a novice.

---

### Post by noob12 on 2007-09-27
Firestarter controls the firewall.

We will want to set you up so that Samba is only listening on the 192.168.2  (eth1) interface and then set the firewall to allow the filesharing ports and ICMP traffic there.

Your files will be exposed if you are not careful.

---

### Post by davidsuma on 2007-09-27
how do you configure the samba to listen only to the eth1...
and how to configure firestarter to only allow filesharing port?...

I couldn't find any tutorial on that...

---

### Post by noob12 on 2007-09-27
OK.  First get your Samba service running only on the internal interface.

Edit you your **/etc/samba/smb.conf** file using 
```
sudo gedit /etc/samba/smb.conf
```

You should find a section that looks like this
```

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

```

Change only the last line of this section to read as follows.  Notice that the leading semi-colon and spaces have been removed.  Check that you got it as shown here.
```

interfaces = eth1

```


Then below that find this section
```

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true

```
and change the last line removing the leading semi-colon and spaces:
```

bind interfaces only = true

```

Save the file and exit.  

This configuration will be automatic on reboots but to make it take effect immediately run this now:

```

sudo /etc/init.d/samba restart

```

---

### Post by davidsuma on 2007-09-28
Thanks noob12...you are my hero! :)

Btw, how about configuring firestarter...
What do i do to make my computer save....example the folders are not exposed etc...

---

### Post by noob12 on 2007-09-28
We may still have a ways to go to make sure you're done.

It sounded like you had already installed firestarter.  You can continue to use that.   Keep the firewall active.

You need to configure the firewall to allow all connections on the internal net.

Bring up the firestarter configuration UI (System | Administration | Firestarter)

Select the Policy tab.  Click inside the first box that says "Allow connections from host".  Once you've clicked in the box, the "Add Rule" button will become active.  Click the "Add Rule" button.

In the panel that pops up select the "IP, host, or network" radio button, and in the box, enter this network specification: **192.168.2.0/24** which is your internal net.  Add a comment that says "allow traffic from internal net".

Add the rule.  Apply the Policy. 

That's it for this step.

Next we want to make sure you can share files both ways.

---

