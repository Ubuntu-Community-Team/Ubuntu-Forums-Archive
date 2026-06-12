---
title: "Torrent protection/ privacy"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by dan1973 on 2009-05-14
Could someone advise me on the best package to help preserve privacy while using transmission torrent. 

I hear that all sorts of seeders can nose into your system - probably microsoft employees with nothing better to do!

Many thanks,

Dan

---

### Post by AndThenWhat on 2009-05-14
Yeah there is a blocklist for people like that.  Just go to (Edit -> Preferences) then go to the Peers tab and check the box "Enable Blocklist". Then you should be good to go!

---

### Post by Ocxic on 2009-05-14
The block list only block certain organizations(RIAA, MPAA, etc) from connecting to you, but any peer or seed that you are connected to while downloading is going to see you IP address, and privacy is gonna go out the window.

---

### Post by binbash on 2009-05-14
I suggest using deluge.YOu can encrypt the connections plus there is a blocklist plugin ;)

---

### Post by lovinglinux on 2009-05-14
> **binbash said:**
> I suggest using deluge.YOu can encrypt the connections plus there is a blocklist plugin ;)

Encryption only helps to avoid bandwidth caps, which means your ISP won't be able to sniff through your data headers to determine the protocol of your transfer and thus reduce it's bandwidth. Blocklists just prevent from connecting to undesired peers. It doesn't protect your privacy. Nevertheless, is a good idea to use both.

You might also consider using a system wide blocklist filter, like [moblock](http://moblock-deb.sourceforge.net/) or [iplist](http://iplist.sourceforge.net/), because they protect not only your torrent connections, but the entire network.

Anyway, unless your downloading things you shouldn't be downloading, what's the problem if Microsoft connects to the swarm? I doubt they will help to seed Ubuntu distros in the first place, which would be really funny, but the torrent protocol is not like eDonkey and Limewire. The peers you connect to cannot see your directories or anything else you are sharing outside a single torrent swarm.

Before someone suggests, TOR should not be used for p2p. Using TOR for large data transfers is considered abuse. Besides, you will probably get very slow connections and TOR has it's own privacy issues.

Deluge allows you to setup proxies for different types of data transfer, but like TOR, they will probably slow down your connection considerably. Besides, your privacy level would depend on the proxy you are using. Would you trust a proxy?

If you really want to protect your privacy, then you should contract a VPN service with very clear privacy policies. Other than that, I don't know what else could be done. The nature of p2p requires that you disclose your IP address, otherwise you won't be able to download.

---

### Post by maybeway36 on 2009-05-14
You could use PeerGuardian, but then you'd probably have to run Windows.
All the spy IPs can do anyways is see what you're seeding and downloading, if I'm not mistaken.

---

### Post by lovinglinux on 2009-05-14
> **maybeway36 said:**
> You could use PeerGuardian, but then you'd probably have to run Windows.
All the spy IPs can do anyways is see what you're seeding and downloading, if I'm not mistaken.

As I have already posted above, moblock and iplist are the Linux alternatives for Peerguardian and they work perfectly. Please don't even consider running Peerguardian through Wine. It probably won't work and it's unnecessary.

---

### Post by Randomperson_1000 on 2009-05-21
Turn encryption and use a iplist. 

You can use tor to communicate with the tracker, this isnt going against their rules(i think) cos you arent downloading anything through tor if u set up your torrent client to go through tor then all the ips in the swarm will not see your real ip and this is how most people get caught. All the peices come through your real ip.

Note however if som1 was to run netstat they would be able to see your ip. Also u can't seed u become passive

You can't hide your ip/change while bittorenting because of how bittorent works. U need to be active and have a real ip address.

If you really are worried about privacy use blocklists(not 100% effective) and try finding some private bittorent sites.

btw - if u are worried about getting caught dl something dodgy the only real way to get caught is if a bad seed uploads to you or you upload to a bad seed. Microsoft or any other anti p2p companies simply being in a swarm cant do anything. I read about it somewhere its quite difficult to pin something onto you.

---

### Post by doas777 on 2009-05-21
I wish [I2P(wikipedia)]("http://en.wikipedia.org/wiki/I2P") would gain more acceptance and use. it seems promising for anonymity,  but would allow larger transfers, which is really unkewl on tor.

---

### Post by johndoe32102002 on 2010-07-08
> **lovinglinux said:**
> 
You might also consider using a system wide blocklist filter, like [moblock](http://moblock-deb.sourceforge.net/) or [iplist](http://iplist.sourceforge.net/), because they protect not only your torrent connections, but the entire network.

If you really want to protect your privacy, then you should contract a VPN service with very clear privacy policies. Other than that, I don't know what else could be done. The nature of p2p requires that you disclose your IP address, otherwise you won't be able to download.

I agree with using IPBlock (IPList) and a VPN provider.  Also, I2P has torrents inside it and a version of Transmission built just for I2P (for i386 only).  I2P lets you balance speed over security by choosing how many tunnel layers of encryption you wish to have.  The more tunnel jumps, the slower but more secure, and vice versa.

---

