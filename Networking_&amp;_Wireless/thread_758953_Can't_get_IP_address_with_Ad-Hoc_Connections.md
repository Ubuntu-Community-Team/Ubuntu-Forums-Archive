---
title: "Can't get IP address with Ad-Hoc Connections"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by miketowninc on 2008-04-18
Ok so I installed my WG11v2 through this [http://ubuntuforums.org/showthread.php?t=590942&page=1](http://ubuntuforums.org/showthread.php?t=590942&page=1)



Well my problem is that my card will not conect to a trendnet router with wep on or not. But it will connect to my neighboors wifi which has no wep on. So I am guessing that it doesn't like the trendnet router.


So I decided to make an ad-hoc with another wifi card. And it claims that it connects but it doesn't not get any IP's. I tried it on my Windows XP and it does connect and get ips. So there has to be something wrong with something in ubuntu. Any help?

THANKS!!

---

### Post by Kensey on 2008-04-18
> **miketowninc said:**
> So I decided to make an ad-hoc with another wifi card. And it claims that it connects but it doesn't not get any IP's. I tried it on my Windows XP and it does connect and get ips. So there has to be something wrong with something in ubuntu. Any help?

On XP, you get an IP starting with 169.254, right?  That's something Windows XP does -- if a network connection isn't configured for static IP, and it doesn't get an IP through DHCP, it will automatically assign itself one in that range (it's called Automatic Private IP Addressing).  Under Ubuntu this is handled by [avahi]("https://help.ubuntu.com/community/HowToZeroconf") -- is avahi listed as installed in Synaptic?

---

### Post by miketowninc on 2008-04-18
No It is 192.168.0.2. since it is internet sharing. I will check for avahi. But I know when I go to Network tools I get wlan0:avahi. So should it not be installed?

---

### Post by miketowninc on 2008-04-19
Any suggestions?

---

### Post by miketowninc on 2008-04-20
Really NO body has any idea??!?!??! Im going to have to abandon ubuntu

---

### Post by CrazyGuy123 on 2008-04-20
I think if you see wlan0:avahi, then that means it's found itself an ip address(in the 169.254 range) and should work.

You should be able to see other computers on the same ad-hoc network and share files/printers with them.  You won't be able to access the internet through another computer over the wireless.

If you want to access the internet through another computer on the wireless, you'll have to set up Connection Sharing on that computer first, and then that computer will give 192.168.0.X IP addresses to all the other computers on the same AD-hoc network.  Note, for this to work, the computer with network sharing must be the first computer that connects to the adhoc network.

---

### Post by miketowninc on 2008-04-20
> **CrazyGuy123 said:**
> I think if you see wlan0:avahi, then that means it's found itself an ip address(in the 169.254 range) and should work.

If you want to access the internet through another computer on the wireless, you'll have to set up Connection Sharing on that computer first, and then that computer will give 192.168.0.X IP addresses to all the other computers on the same AD-hoc network.  Note, for this to work, the computer with network sharing must be the first computer that connects to the adhoc network.

When I go to the vista computer it does not see my ubuntu PC on the network. Weither there is internet sharing or not.

---

### Post by CrazyGuy123 on 2008-04-20
I read the thread again, and I think I misunderstood you with my last post.

If an XP computer can get a 192.something IP, and the ubuntu computer can't get an IP on the same network, then the problem is one of these:

1.  The ubuntu computer is on the edge of the range for the network - bring it closer or fit a bigger aerial

2.  There is a problem with the wireless driver/configuration - this often happens if the encryption settings are set wrong - try with encryption off on all the computers.

3.  The XP computer may have a "static" IP set up. This is unlikley if it's an "internet connection sharing" network. To get ubuntu working on the same network, set ubuntu to also have a static IP.  (if the XP one is 192.168.0.2, set ubuntu to be 192.168.0.3, with a subnet mask of 255.255.255.0 and a gateway of 192.168.0.1)

---

### Post by CrazyGuy123 on 2008-04-20
Also, for the ubuntu computer to show up in windows, you need at least one folder shared.  To do that, right click any folder, select sharing, enable it, and install the sharing service - it's a bit of a pain, but it's because Windows File Sharing is considered a bit insecure, so isn't enabled by default because many users don't need to share fles with windows computers.

---

### Post by miketowninc on 2008-04-20
> **CrazyGuy123 said:**
> Also, for the ubuntu computer to show up in windows, you need at least one folder shared.  To do that, right click any folder, select sharing, enable it, and install the sharing service - it's a bit of a pain, but it's because Windows File Sharing is considered a bit insecure, so isn't enabled by default because many users don't need to share fles with windows computers.
I use network scanner and all it does is looks for ip address conected to the network. Also I had my internet sharing on my ad-hoc which when I plug the card in to the Xp PC worked. So that means it can be because to of the Ad-Hoc host. 


"I read the thread again, and I think I misunderstood you with my last post.

If an XP computer can get a 192.something IP, and the ubuntu computer can't get an IP on the same network, then the problem is one of these:

1. The ubuntu computer is on the edge of the range for the network - bring it closer or fit a bigger aerial

2. There is a problem with the wireless driver/configuration - this often happens if the encryption settings are set wrong - try with encryption off on all the computers.

3. The XP computer may have a "static" IP set up. This is unlikley if it's an "internet "connection sharing" network. To get ubuntu working on the same network, set ubuntu to also have a static IP. (if the XP one is 192.168.0.2, set ubuntu to be 192.168.0.3, with a subnet mask of 255.255.255.0 and a gateway of 192.168.0.1)"

1. I did it almost right on top of the adhoc host
2.Could it be a ndisswraper problems. Is there information that you could look at to see if it is working?
3.I have tried bot static and automatic Ip

THanks for you help!! Appreciate it

---

### Post by CrazyGuy123 on 2008-04-20
Yep it could certainly be an ndiswrapper problem - I don't use it so I don't know much about it I'm afraid  :(.  Try starting a new post asking if there's a proper driver for your wireless card, because generally they're much better than ndiswrapper ones.

Remember getting an IP address (DHCP) is the first thing thats done after connecting to a network, so if that fails, there's a good chance that it isn't a problem with finding an ip address, but instead wit the connection itself - ie. it just isn't sending or receiving ANY data.

I'm off to bed now, and since ndiswrapper is outside my understanding, can someone else provide some insight into what could be causing problems for mike?

---

### Post by miketowninc on 2008-04-22
So Can some one help?

---

### Post by miketowninc on 2008-04-22
Anyone?

---

### Post by chessmani on 2008-06-24
Hey, did you get this to work? I think I have the same problem.

---

