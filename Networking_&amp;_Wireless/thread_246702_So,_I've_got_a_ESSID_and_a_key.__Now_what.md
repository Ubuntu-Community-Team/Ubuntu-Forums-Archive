---
title: "So, I've got a ESSID and a key.  Now what?"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by MikeBenza on 2006-08-29
I've just arrived in Italy for my study abroad program. My apartment has free wireless. I have the ESSID (Netgear) and all the landlord can tell me is that the key is 0123456789. I don't know if that's hex or plain. I don't know if it's WPA or WEP. I can't connect to the internet other than in a computer room in the apartment, which kinda eliminates the point of me bringing a laptop.
 
I **don't **have gnome-network-manager installed -- it doesn't show in synaptic.  Ubuntu shows two icons in the upper panel: One for the wired net, one for the unwired. Both show as diconnected. Nothing happens when I double click the one that's for the wireless. When I double click the icon for the wired, I get options to plan with eth0 and lo0.
 
The wireless worked fine on WEP before I got here. I've rebooted. Other people (with Windows) have connected without a problem. Any idea?
 
- Mike

---

### Post by meng on 2006-08-29
It's WEP, hex, 64-bit.
Go System > Admin > Networking, and configure your wireless card using the ESSID and WEP key.
Then tell us whether it worked.

---

### Post by MikeBenza on 2006-08-29
I suppose I should've added I already tried that and it doesn't work ;).
 
I have a Netgear 511 with ndiswrapper too.  Also, I realized I **don't** have gnome-network-manager installed.  I thought I did, but now that I check, it's not even listed in synaptic -- and I have universe and multiverse in /etc/apt/sources.list

---

### Post by meng on 2006-08-29
Okay, thanks for the info.
Can you drop to the command line and try this?

sudo iwconfig eth0 essid Netgear key 0123456789
sudo ifconfig eth0 up
sudo dhclient eth0
ping google.com

Substitute eth0 with whatever your wireless device id is.

---

### Post by MikeBenza on 2006-08-29
The first two produce no output.  the third:
 
Listening on LPF/wlan0/00:0f:b5:26:c2:0b
Sending on LPF/wlan0/00:0f:b5:26:c2:0b
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPNAK from 88.38.78.xxx (I blocked it out)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
 
The last line is repeated for intervals 8, 9, 11, 10, 15, 1, then:
No DHCPOFFERS received.
No working leases in persisten database - sleeping.
 
The ping obviously fails.
 
 
 
When I ran those above commands, the following appeared at the end of dmesg:
wlan0: no IPv6 routers present
 
- Mike

---

### Post by meng on 2006-08-29
Whew tough, I've reached the end of my short tether of knowledge.

---

### Post by MikeBenza on 2006-08-29
The weird thing is that I followed [the instructions](http://doc.gwos.org/index.php/DisableIPV6) on the Ubuntu Doc Storage Facility for disabling ipv6.  I'm undoing that now and seeing if it works.  I'm going to sleep -- so I'll check back here tomorrow morning.  Please reply if anyone has any idea.
 
Grazie.
 
- Mike

---

### Post by MikeBenza on 2006-08-30
I still can't connect. A bunch of other people are having trouble, though with Windows and OS X. I'm guessing this is now more of a general wireless issue though, so can I still get help here?
 
Mike

---

### Post by Andrew Olney on 2006-08-30
network-manager-gnome shows up for me in synaptic

You may want to back up your /etc/network/interfaces file, and in a new /etc/network/interfaces file, comment out all the lines except those pertaining to lo. Otherwise your wireless may not appear in the applet. Try it without this extra step first.

If it still fails, you might want to show the output of 

ifconfig 

and 

iwlist scanning 

on this forum.

---

### Post by Andrew Olney on 2006-08-30
I forgot to mention -- you need to reboot after installing the network manager for it to appear in the applet bar.

Also make sure that you have used the Fn key combination to turn on your wireless hardware on your laptop.

---

### Post by MikeBenza on 2006-09-04
So the answer is essentially, the router is configured horribly.
 
Here what you get when a machine sucessfully gets connected:
 
Gateway: 88.38.78.97
IP: 88.38.78.98 -- .one-hundred-something
Broadcast: 255.255.255.248
 
So, that's only 7 clients and 1 gateway.  Dumb idea for a building with 30 college students.  Basically the router is assigning public IPs.  If you do reverse lookup on this IP, you'll see that the hostname has 'static' in it, which makes me iffy about resetting the router and configuring it myself.
 
Could anyone say if it's possible to just use .97 as the gateway, and have all the other clients in a 192.168 private network?  I don't think it'd be a problem at all, and is a much better idea.  I'll obviously ask the landlord before I change anything.
 
- Mike

---

### Post by lupine_nickt on 2006-09-04
Mike: definitely a problem with the router itself... this "DHCPNAK from 88.38.78.xxx" message "probably" means it's out of IP addresses (as you've surmised).

If you want to stick a load of computers into a private IP range, you need to use NAT - network address translation - and I really don't recommend it in your current setup, as it'll be a pain to get going right. 

At the moment, you have 5 usable client IP addresses (8 in total; 1 gateway, 1 network, 1 broadcast, 5 unused). if I were you, I'd ask the admin/flat owner to get the ISP to increase the network from a /29 to a /28 (16 addresses, 13 usable) or /27 (32 addresses, 29 usable)... maybe even a /26 (64 addresses, 61 usable). That shouldn't be a problem, assuming that they're with a decent ISP.

If you're determined to use NAT (or if the landlord is a PITA), then the easiest way to do it would be to enable NAT on the router, and make sure that it's LAN address is in the local network, too -- essentially, stop using the /29 subnet. 

The wireless on your laptop *is* working fine, btw :)

xF,

...Nick

---

### Post by MikeBenza on 2006-09-05
> If you want to stick a load of computers into a private IP range, you need to use NAT - network address translation - and I really don't recommend it in your current setup, as it'll be a pain to get going right. 
 
Why do you think it'll be a pain to set up?  I don't understand why it would be any different than setting up a regular router, just with a static IP and DNS.
 
What I also don't understand is why a telcom would set this up; if I've figured it out right, they're giving us 8 ips to use instead of 1.  IP space is limited -- why use something that's a configuration nightmare and is a PR nightmare to change?
 
I'm thinking of just buying another router, plugging that into the current one, and setting that up to use NAT on a private net.  What do you think of that?
 
- Mike

---

### Post by lupine_nickt on 2006-09-05
MikeBenza: in IPv4 address space, I have a /29, a 30 and a /32. I'll also be getting a second /32 shortly. Why? It's the "correct" way to do things :). I've also got some IPv6 address space - a /48, in fact (1.208x10^24 usable addresses). Contrary to what the paranoid say, we are not running out of IPv4 address space... and by the time it becomes a problem, we'll all have ipv6. 

I recommended not using NAT because, firstly it'll be a complete waste of your current IP allocation. Secondly, consider that you'll need to add port forwarding rules for every student who wants to play online gaming; use p2p; run their own servers... thirdly, some programs simply won't work at all. 

Fully routed IP addresses are good. NAT addresses are a kludge. Increasing your IP allocation is really easy, in comparison :). 

If you add a second wireless router, you're going to get crosstalk, leading to reduced performance on both.

---

