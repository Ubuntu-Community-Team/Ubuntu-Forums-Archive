---
title: "Need help with Shorewall"
date: 2005-08-07
forum: Networking &amp; Wireless
---

### Post by otakuj462 on 2005-08-07
Hi all, I'm currently working to configure an old PC of mind to act as a router using Shorewall. Unfortunately, I haven't had much luck getting it to work yet, and I have some questions. First, let me describe my setup:
I have my old PC running linux. Inside it is a wireless card (ath0) and a wired ethernet card (eth0). They goal is to allow ath0 to connect to an external wireless router, and then route the packets out through eth0 to a desktop computer.
ath0 is already configured, so the PC currently has an ethernet connection. Unfortunately, I'm not sure how I should configure eth0, or if I even need to configure it at all. At the very least, ifconfig sees it, though it doesn't list it as having an ip address. My first question is, how should I configure eth0?
My next question is, what is meant by a broadcast address? I can understand what it means for, say a router, which has an external ip address, from which it receives packets from the internet, and an internal one, to which it sends packets. To talk to the router, a device would look at its internal ip address, which must be synonymous with its broadcast address. But the idea is less clear when referring to, say, the wireless card, which only appears to receive packets. So when configuring the device in /etc/shorwall/interfaces, what should I put in the BROADCAST column?
Finally, in what situation would a device use DHCP? Is it simply used to resolve web addresses, or does it do something more? Should I configure my interfaces to use DHCP in this situation?

If anyone has any information, please let me know. Thanks.

-Jake

---

### Post by az on 2005-08-07
First off, Shorewall is excellent.  The key is to install the shorewall-doc package.  It includes a number of example scenario configurations.  You would just have to copy the two-interface configuration into your /etc/shorewall directory and change two or three things and you are good to go.  (Do not forget to change the /etc/defaults setting to make shorewall actually start)  The two-interfaqce defaults to network address translation and firewalling.

Youre external NIC (eth0) can be made to connect other boxes using dhcp, if you find that convenient.  You need to assign it a static ip address (use the network manager) and make the network different from your ath0 network.  Your box will be routing from one network to another (read the shorwall docs, they are excellent.)

Then, install dnsmasq.  It not only provides you with a dhcp server (for eth0), but it also caches dns which is really nifty.  I think you need to enable the rule in shorewall for dhcp requests, if I remember correctly...  dnsmasq is also easy to configure.

You should be good to go.

---

### Post by otakuj462 on 2005-08-08
Thanks for the advice! I have a few more questions.

I don't have a window system on this computer, so I'm stuck setting all this up from the command line.  I assume I can do most of the configuration of eth0 just by modifying /etc/network/interfaces. But I'm not sure what the text would look like to assign it a static ip address, and make the network different from the ath0 network. 
To make the eth0 network different from the ath0 network, if the ath0 network is 192.168.1.xxx, would I just need to assign the eth0 network a static ip of 192.168.2.xxx ? Do I just do this by modifying /etc/network/interfaces ? Or is there something more that needs to be done?
Finally, what does it mean to "cache dns"?
Thanks again.

-Jake

---

### Post by az on 2005-08-08
"don't have a window system on this computer, so I'm stuck setting all this up from the command line. "

I got hooked on mc a long time ago.  I still open a terminal and run mc when I look for a file rather than use nautilus...  

sudo apt-get install mc
(F9 to configure, and enable lynx-like browsing so that you use the cursor keys to go into and out of folders...  Anyway...



"I assume I can do most of the configuration of eth0 just by modifying /etc/network/interfaces. But I'm not sure what the text would look like to assign it a static ip address, and make the network different from the ath0 network.
To make the eth0 network different from the ath0 network, if the ath0 network is 192.168.1.xxx, would I just need to assign the eth0 network a static ip of 192.168.2.xxx ?"

Correct.  You can also just install etherconf and do
sudo dpkg-reconfiigure etherconf 
and it will configure it for you by asking questions.

"Do I just do this by modifying /etc/network/interfaces ? Or is there something more that needs to be done?"

I would probably run
sudo /etc/init.d/netowrking restart
to make all the changes take effect.



Finally, what does it mean to "cache dns"?
Thanks again.

Well, you can set up NAT (internet connection sharing, AKA masquerading, AKA Network Address Translation) but this will not do anyting for DNS.  You would be able to ping the ip address, but not the host.  You need to set up a dns cache/masquerader so that dns is also translated.  Caching just makes the lookup faster, in general.

---

### Post by otakuj462 on 2005-08-25
This is a late reply, I know, but believe it or not, I'm still working on getting this set up. My power supply died, and that delied my response. That's the problem with working with 10-year-old hardware.

I'm going to go over the setup once real fast, just to make sure there are no ambiguities. I have a ubuntu box with two NICs in it: a wireless card, ath0, and an etherent card, eth0. The goal is to allow ath0 to connect to a wireless router, and have eth0 via ethernet to another ethernet device, call it eth1, and to route the packets from ath0, to eth0, to eth1 and back.

Since I'm not interested in turning my linux box into a DHCP server (as there will be only one computer connected to eth0), I think I need to assign eth1 a static ip address that both Shorewall and eth1 knows about. I've assigned eth0 a static ip address (192.168.2.1) and eth1 a static ip address (192.168.2.100), and in the /etc/shorewall/interfaces configuration file, I have the eth0 broadcast address set to 192.168.2.255. How do I get Shorewall to recognize eth1? Do I have to tell it about eth1's static ip? If so, where do I do this?
Thanks.

-Jake

---

