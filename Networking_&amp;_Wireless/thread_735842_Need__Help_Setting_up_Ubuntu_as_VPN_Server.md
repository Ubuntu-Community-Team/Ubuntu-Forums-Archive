---
title: "Need  Help Setting up Ubuntu as VPN Server"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by ubuntogenius on 2008-03-26
I have an old cpu that I am running Ubuntu Server on.  I am currently using Samba to act as a file server for a central location for files.  Because I have not been able to invest in more storage space for the server I still have files on the 4 clients.  The clients are running the following: 2 laptops Vista, pcs XP.  I have a linksys wrvs4400N as my switch which also has a vpn server built in.  My problem is that I have already been thru linksys support to understand that quickvpn is not currently supported on vista platforms.  What I need to be able to do is use the laptops to access my network from home.  Because I cannot do this thru the built in vpn server on my linksys, I would like to know if there is a way to setup my Ubuntu server to also act as a vpn server?  Also, my understanding is that vista no longer works with IPSEC?  This was linksys' explaination for why it won't work with their quickvpn, because it uses IPSEC for the protocol.

Thanks for the Help!

---

### Post by SpaceTeddy on 2008-03-26
in short - yes there is. But this is neither easy to do, nor simple to understand.
I personally am a fan of OpenVPN, which keeps fairly simple configuration files and works on all platforms (as far as i know even on portable devices, but i have not tested that yet). furthermore, it will only use one port, and can be setup to run in the background to autoconnect/reconnect. Also it can route networks or redirect fully over the VPN - which ever mode is desired.
I must point out though that OpenVPN does NOT use ipsec as protocol, but uses SSL/TLS instead (if this does not tell you anything, ignore it :) )
a good startingpoint for openvpn is [here]("http://openvpn.net/index.php/documentation/howto.html"). if any questions arise, i will try to help aswell :)

Another solution i can think of is pptp. I have setup that too, but was never very satisfied with it. So i cannot really say much towards it (i deleted it again in favor of OpenVPN)

i bet there are other solutions out there, but i do not know of them (apart from a few highly priced ones). So forgive me the shortness of my list of options :)

hope it helps

[EDIT]
Linksys must be mistaken about Vista not working with IPSEC anymore. That would make no sense, since IPSEC is the standard protocol for VPNs... or so i have learned last year... maybe the world does evolve faster than i tought...

---

### Post by andguent on 2008-03-26
Another VPN option is Hamachi from LogMeIn.com. It's free for 16 computers. If you need to connect more than 16 computers together you need to pay for it. I've used OpenVPN and pptp on Linux and Windows, Hamachi is by far the easiest to setup.

[https://secure.logmein.com/products/hamachi/vpn.asp?lang=en](https://secure.logmein.com/products/hamachi/vpn.asp?lang=en)

---

### Post by SpaceTeddy on 2008-03-27
mhm... yes i've been hearing this a lot lately that people use hamachi to network their computers. Of course it is an option, and in the end you will have to decide for yourself what you want to do or do not want to do... 

I personally would not use hamachi. Not because it does not work (it acctualy does quite well), but for the fact that i do not entriely know HOW it works. HOW much traffic is shared trough the hamachi servers, what traffic could be sniffed there.

Also, afaik, hamachi is a layer 2 Network bridge, so even broadcasts would go over it. In some cases this may be a required option (in games for example) while in others it can simply flood the internet line or have some other, undesired effects (ever tried to run a hamachi client on a server that also issues dhcp-leases ?)

My main concern is the lack of knowledge about the architecture and the flow of traffic tho. I  do not have control over it and it bypasses my firewall - therefore i do not like it !

this is just my opinion about it - don't want to offend anyone :)

---

### Post by andguent on 2008-03-27
No offense taken. I always want the best tool for the job, and no VPN server is perfect for every need. I've setup 15-20 different OpenVPN connections, and I find that the best for managed environments when you want a routed VPN.

Hamachi is painfully easy to setup. If you only needed the basics of VPN connections, and already spent months to get OpenVPN running, Hamachi can make you feel like you wasted a lot of time. If you want to walk a normal computer user through installing it and joining your VPN, it is the way to go.

SpaceTeddy you are dead on for the broadcasting. Hamachi VPN passes a LOT of traffic across its interface. I can also say I have successfully gotten LAN based games (particularly from Blizzard) to work across it without issue thanks to that broadcasting. I also run nightly rsyncs across it for file backup, and that has been fairly stable.

According to LogMeIn documentation, the only traffic they see for Hamachi is the authentication trust handshakes, mostly occuring when a new client trys to join the network. I can say that the throughput bandwidth acts as if it is not relayed. 

I just did a file transfer across Hamachi while monitoring my server via iptraf. It appears that my backup server phones home to hamachi (416 bytes) every 10 minutes or so. I'm not timing it, but I know for sure it is not a constant thing. Meanwhile, there is a massive amount of UDP traffic coming directly from my mom's house as I'm copying a 30MB file at 70kB/s. I have basic DSL, she has FIOS, so I would expect a better transfer rate then that but it still is very usable.

A limitation to note for Hamachi: while everything is encrypted, the way to join a network is via a password. Make sure your VPN password is very very good.

---

### Post by SpaceTeddy on 2008-03-27
mhm - you seem to know a lot more about the architecture than i do... could you poing me to a location where i can read up on it, or can you answer some questions ?

for example, which encryption algorithms are used for the transport ? how strong is it ? does the hamachi server only do authentification and holepunching (which would be needed to bypass nat firewalls) or does it do more ?

mhm... i just relaized that this thread was acctually about something else :) so i'll stop here :)

---

### Post by andguent on 2008-03-27
The OP wanted VPN info, we can give him(her) some VPN info.  ubuntogenius feel free to ask another question if you need more info.

SpaceTeddy, click the link I gave above and work your way down the left side Navigation panel. See especially the "how it works" and "security". Once in security, there is a "Security Architecture description" link that is a good read too if you want to get into encryption types.

The long and short of it is that the VPN works for the big three OS's, and the only thing the Mac & Linux users are missing is multi language support, and a GUI. All of the networking functionality is there. "Hamachi is currently available for Windows 2000, XP, 2003, and Vista. Console versions of Hamachi are also available for Linux and OS X."

And no, I don't work for them, but I do kinda sound it huh.... :)

---

