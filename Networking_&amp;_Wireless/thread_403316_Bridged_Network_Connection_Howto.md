---
title: "Bridged Network Connection: Howto?"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by sveard on 2007-04-06
Hi there,

I have the following question:

Under Windows XP I could bridge my ethernet and wifi connections. That way, I could hook up an ethernet device to my laptop that is not wifi-compatible, and let it use my wifi connection through the ethernet LAN connection.

So I was wondering if I could get this to work on Ubuntu (6.10), wireless works like a charm out of the box, so the only thing I would need to know is how to create the bridged connection... I've looked around for some info but couldn't find anything. Any help would be most appreciated. :)

Thanks,

Sven.

---

### Post by PokerJoker on 2007-04-08
He Sven, there's a package called bridge-utils. Install it using package-manger. Just found it myself. Requires some manual configuration, i'm trying that now. Just like in XP  it needs to set up a br0 device.
But i will look to see if there is an ubuntu way to set it up.....if i find it i'll let u know.

Some info:

[http://linux-net.osdl.org/index.php/Bridge]("http://linux-net.osdl.org/index.php/Bridge")

Just tested it and setup is very straightforward, so if you don't mind getting your hands "dirty"  in a terminal using command-line...here's the mini-howto: 

My setup: Ubuntu box with 2 ethernet if's (wireless have bad reception, so not using them)
XP Notebook. 

Install bridge-utils using package-manager. Search for "bridge" 
Open terminal-window

sudo brctl addbr "your-bridge-name"

sudo brctl addif "your-bridge-name"  interface-name  [i assumed my eth0, incoming connection, which is connected to networkrouter ]

sudo brctl addif "your-bridge-name"  interface-name [in my case eth2, which is direct to notebook ]

check if this works:

sudo brctl show  or showmacs

finally dhcp, assuming u use it like me

sudo dhclient your-bridge-name

Takes a few seconds, after which you should get the "bound to" response meaning we have an ip-adress.

Finally reset network connection on notebook, and the bridge is built. 

Off course this is the manual setup, it needs to be made perm. Need to read up on that part still.

Hope it works for you too.

---

### Post by ap.sampson on 2007-04-09
So, here's where I'm at with this:
 I followed the directions in your post and in the tut verbatim.

However, whenever I get the "bound to....." message for the bridge, i have no connection on the buntu box.

I tried "sudo ifdown eth0" followed by "sudo ifup eth0" and I still don't get anything.  It isn't a hardware problem b/c the bridge works flawlessly in XP...So, I'm looking for some more details.

Do I need to ifdown eth0 and eth1 and then do what you have? do i need to enable/disable both through System>Admin>Network?  please help!

I tried "sudo ifconfig eth[0,1] 0.0.0.0" like the tut mentioned, but that didn't do jack for me.

Any help would be greatly appreciated, I sorta feel like throwing+xbox out the window right now.

ALSO, when I try to ping the router with the bridge i get a message about sendmsg not being allowed.[not sure if this will help]

---

### Post by PokerJoker on 2007-04-09
> **ap.sampson said:**
> So, here's where I'm at with this:
 I followed the directions in your post and in the tut verbatim.

However, whenever I get the "bound to....." message for the bridge, i have no connection on the buntu box.

I tried "sudo ifdown eth0" followed by "sudo ifup eth0" and I still don't get anything.  It isn't a hardware problem b/c the bridge works flawlessly in XP...So, I'm looking for some more details.

Do I need to ifdown eth0 and eth1 and then do what you have? do i need to enable/disable both through System>Admin>Network?  please help!

I tried "sudo ifconfig eth[0,1] 0.0.0.0" like the tut mentioned, but that didn't do jack for me.

Any help would be greatly appreciated, I sorta feel like throwing+xbox out the window right now.

ALSO, when I try to ping the router with the bridge i get a message about sendmsg not being allowed.[not sure if this will help]


U haven't described your setup. Are u using dhcp from network?
The bridge box has 2 if's, one connected to network (is it dhcp?) and one to your xbox..
I'm not an expert on bridgeing, but like in windows the bridge is setup like an extra interface (if) but don't think u can use it to do pinging and stuff. 

Also i'm not happy with the NetworkManager as i'm used to do it manually or with scripts. I had some trouble with wireless. But since i went to feisty and ethernetcable, it seems to work fine so for now i'l  let it do it's magic. 

Before setting up the bridge, i have an ip assigned to eth0 using dhcp, as per boot.
eth2 is connected to my notebook, your xbox, no ip, i can check this on my notebook, it gets the default 169.x.x.x ip from windows. 

set up bridge "br0" 
assign eth0 
assign eth2
dhclient br0 

reset eth conn on notebook( xbox)

that's all i did. the route table on my ubuntu shows both eth0 and br0 pointed towards gateway:

hoek@hoek-desktop:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0        0        0 eth0
192.168.1.0     *               255.255.255.0   U     0        0        0 br0
link-local           *               255.255.0.0       U     1000  0        0 eth0
default         192.168.1.254   0.0.0.0         UG    0        0        0 br0
default         192.168.1.254   0.0.0.0         UG    0        0        0 eth0


> Any help would be greatly appreciated, I sorta feel like throwing+xbox out the window right now.
  

Lol, please don't, you'll be sorry  :(

---

### Post by ap.sampson on 2007-04-10
Update:

Connection from the router, hitting eth0 is DHCP.  I've had some luck tonight! The bridge is up and running and the xbox is able to see everything on the network.

HOWEVER, my desktop isn't able to see jack once the bridge is up.

---

### Post by sveard on 2007-04-11
> **PokerJoker said:**
> ...

Hey,

Sorry for the late response. I had some trouble getting this to work but after digging some more around the net I've managed to hook up the device and it's now working fine, thanks!

---

