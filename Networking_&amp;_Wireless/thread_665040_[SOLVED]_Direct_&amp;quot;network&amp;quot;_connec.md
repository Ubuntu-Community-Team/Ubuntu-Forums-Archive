---
title: "[SOLVED] Direct &amp;quot;network&amp;quot; connection"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by dawynn on 2008-01-11
I apologize in advance if this is one of the most basic questions regarding networking.  I'm no sysadmin, and I'm not even sure of all the correct terminology to even try to research this.

I volunteer at a non-profit organization that has a Panasonic PT-D3500U video projector -- the kind of thing built for showing "Powerpoint" presentations.  We have a Macintosh computer that shows the presentations.  This style of projector has a built-in lan interface that allows the projector to be plugged into a network and controlled from any computer on the network.

We have successfully accomplished getting a direct link from the Macintosh to the projector with just a standard lan cable.  In order to do so, we had to configure IPv4 manually, and type in an IP address, Subnet Mask, and Gateway / Router.

In order to ease the problem of trying to concentrate on the presentation and juggle other software at the same time, I tried to take an aging PC from the back room and fit it with a stripped down version of Ubuntu to be used specifically as a "control" box for the projector.  I've got Icewm as the window manager, with enough Gnome to run the control-center.  KDE is absent, as much as I can help (nothing against KDE -- but this particular box is low on memory).

At this point, we're having trouble getting the same magic to happen with the Linux box that we had with the Mac.  Here's where you can help:

1) What software would be best for configuring network and even making sure the network card is working?

2) What common issues should I watch out for when configuring this kind of projector-to-computer direct link?

Think lightweight, but graphical as much as possible.  And if there is any neato handy pre-written guide for doing this kind of thing -- feel free to send along a link.

Thanks everyone!

---

### Post by HermanAB on 2008-01-11
Hmm, open a terminal and use the textual graphics...

Honestly, the best way to debug low level network trouble is with ifconfig, telnet and ping.

Cheers,

Herman

---

### Post by dawynn on 2008-01-13
Ok -- I'm going to need a bit more hand-holding than that.

I need to get the following settings made:

IP Address: 192.168.0.? (there's some flexibility with the last node here)
Subnet Mask: 255.255.255.0
Gateway: 192.168.0.1

Or I need to figure out what these are already set to, so I can update the projector.  And I need to make sure that the card is actually sending and receiving.

What commands would I use to complete these tasks?

Thanks in advance.

David

---

### Post by sqrt2 on 2008-01-13
I don't know what controlling a projector via the network actually means, but just to configure the network interface you don't need a graphical environment. Simply edit your /etc/network/interfaces so it looks something like this:
[indent]auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.0.42 # or whatever host address you want
netmask 255.255.255.0
gateway 192.168.0.1[/indent]
Then take down the interface and run "ifup eth0" to bring it up again. (Or simply reboot.) Since you're on a direct connection, configuring a gateway doesn't really make sense so you just could leave out that line.

---

### Post by dawynn on 2008-01-18
I set up /etc/network/interfaces much like you indicated (used 192.168.0.9 instead -- rest was typed verbatim).  Still having problems.

After running the "ifup eth0" command, I try to ping the projector ( 192.168.0.8 ) with the following results.  Please note: hand copying from another computer -- space added after the 8 in the first line to prevent forum from confusing the 8 and end parenthesis with a smiley.  I apologize for any other errors:

PING 192.168.0.8 (192.168.0.8 ) 56(84) bytes of data
From 192.168.0.9 icmp_seq=2 Destination Host Unreachable
From 192.168.0.9 icmp_seq=3 Destination Host Unreachable
From 192.168.0.9 icmp_seq=4 Destination Host Unreachable
From 192.168.0.9 icmp_seq=6 Destination Host Unreachable
From 192.168.0.9 icmp_seq=7 Destination Host Unreachable
From 192.168.0.9 icmp_seq=8 Destination Host Unreachable
From 192.168.0.9 icmp_seq=10 Destination Host Unreachable
From 192.168.0.9 icmp_seq=11 Destination Host Unreachable
From 192.168.0.9 icmp_seq=12 Destination Host Unreachable

--- 192.168.0.8 ping statistics ---
12 packets transmitted, 0 received, +9 errors, 100% packet loss, time 10999ms, pipe 3

Note: actually the icmp_seq messages will keep continuing if I let them in the same pattern -- skip one, print three -- but I hit ctrl-c, thus breaking the sequence.

Any other suggestions?

---

### Post by mips on 2008-01-18
> **dawynn said:**
> 
Or I need to figure out what these are already set to, so I can update the projector.  And I need to make sure that the card is actually sending and receiving.


First try and ping your PCs loopback address, 127.0.0.1
Next try and ping your PCs ethernet address, 192.168.0.x

Verify the projectors IP settings again and post them here.

post the output of **ifconfig -a** here
post the output of **lspci -v here** ([COLOR="Red"]Just the section on the Ethernet card[/COLOR])

---

### Post by sqrt2 on 2008-01-18
Also, the output of "route -n" could be helpful.

---

### Post by dawynn on 2008-01-18
I can supply this much right now:

$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.138 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.100 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.099 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.104 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.099/0.110/0.138/0.17 ms

$ ping 192.168.0.9
PING 192.168.0.9 (192.168.0.9) 56(84) bytes of data.
64 bytes from 192.168.0.9: icmp_seq=1 ttl=64 time=0.140 ms
64 bytes from 192.168.0.9: icmp_seq=2 ttl=64 time=0.099 ms
64 bytes from 192.168.0.9: icmp_seq=3 ttl=64 time=0.104 ms
64 bytes from 192.168.0.9: icmp_seq=4 ttl=64 time=0.103 ms

--- 192.168.0.98 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.099/0.111/0.140/0.0198 ms

Projector Settings:
Host Name: PROJECTOR
DHCP: Off
IP Address: 192.168.0.8
Netmask: 255.255.255.0
Gateway: 192.168.0.1
Mac Address: 00:0B:97:41:38:0D

I'll upload files with the rest of the information once I can locate my zip drive.

---

### Post by mips on 2008-01-18
> **sqrt2 said:**
> Also, the output of "route -n" could be helpful.

Only really relevant if he is trying to connect to a different network and needs a default gateway. It won't hurt thought to include the output here though.

---

### Post by dawynn on 2008-01-18
Here's the files as promised.

---

### Post by Nem1976 on 2008-01-18
I have a ? are you tring to connect the Ubuntu PC directly to the projector via a Cat5/Lan cable?  Or are you hooking your Ubuntu PC into a Switch/Hub that also has the projector connected to it?  

Honestly it sounds like a hardware link isn't present.  Most likely the Mac worked because it recognizes it needs to be a crossover cable instead.  Most new switches have an auto sensing option that will allow any kind of cable pluged in to work.  

Are you getting any link lights on the network card of the projector or workstation?

---

### Post by dawynn on 2008-01-18
Yes -- exactly.  We're using a single lan cable and just plugging in directly from one device to the other.  The PC is kinda old, but the network card itself was purchased off the shelf just a month ago.

Our projector is kinda awkward to get to -- so not sure if its showing any lights.  But I had noticed that the computer's network card is not blinking.

So, is there a way to tell Linux that I'm doing a direct connection?  Or am I needing to add in a hub to make the connection work?

Again, thanks everyone for the help!

---

### Post by mips on 2008-01-19
> **dawynn said:**
> Yes -- exactly.  We're using a single lan cable and just plugging in directly from one device to the other.  The PC is kinda old, but the network card itself was purchased off the shelf just a month ago.


Is this a normal LAN cable that you genrally use between the PC and the wall socket?

If it is then it will not work. You need a Cross Over (X-Over) LAN cable where the Transmit & Receive wire pairs are swapped around on the one end. They are cheap and your IT section should have some or else try a shop.

---

### Post by sqrt2 on 2008-01-19
> **mips said:**
> Only really relevant if he is trying to connect to a different network and needs a default gateway.
Delete your link-local route and say that again. Anyway, the output of route looks OK in this case.

However, what looks bad is that there is no "RUNNING" flag showing up in ifconfig. This normally means that the interface is configured but there is no network cable attached. It looks very much like the wrong cable indeed is the problem.

---

### Post by kevdog on 2008-01-19
Can you ping your gateway machine

ping 192.168.0.1

---

### Post by mips on 2008-01-19
> **kevdog said:**
> Can you ping your gateway machine

ping 192.168.0.1

There is no gateway. He has a direct physical connection between two devices.

---

### Post by Nem1976 on 2008-01-19
Like mips's said you can get this to work if you can get a Cross over cable or plug both devices into a switch/hub.

---

### Post by dawynn on 2008-02-29
I apologize for not responding back sooner.  The last few entries here were correct -- we were using just a regular lan cable.  That worked for our Mac, but not our Linux machine.  Once we plugged both machines into a hub -- everything worked fine.

Thanks to everyone for their help on this issue.

---

