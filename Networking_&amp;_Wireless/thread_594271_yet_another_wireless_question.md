---
title: "yet another wireless question"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by wendallsan on 2007-10-27
Hi all,

After reading many posts here on the forum, I find all sorts of people having problems with wifi but so far I've not found one that matches what mine is doing, so I'll post it . . . 

I have a Gateway GT5056 with a Dlink WDA-1320 wifi card that I've put Ubuntu 7.10 on.  I have other Dlink wifi cards in 3 other desktops that I've installed previous versions of Ubuntu on (6.04, 7.04) on them and have gotten the same results listed below with each of them also.

Under Settings > Admin > Restricted Drivers I have Atheros Hardware Access Layer (HAL) Enabled.

Running lspci | grep 802.11 results in:

04:07.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)

Looking at Settings > Admin > Network shows a Wireless Connection, accessing it's properties and setting it from Roaming to DHCP shows the available networks and signal strengths, and I can set enter my settings business as usual (using WEP encryption and DHCP).  I close the Network windows and run ifconfig ath0 and get:

ath0      Link encap:Ethernet  HWaddr 00:15:E9:3C:0A:01  
          inet6 addr: fe80::215:e9ff:fe3c:a01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Normally I expect to see an IP address in there somewhere . . .

If I manually set up my network settings (instead of DHCP) I get an IP address listed with ifconfig, but still don't get any connectivity.

Pinging the gateway results in a "destination host unreachable" message.

So it seems to me that the restricted drivers are working, that I have established a connecting with the wireless gateway, but don't have an IP address and can't get anywhere beyond the router.  I have also made absolutely sure that I am using the right WEP key in my Network settings.

If anybody has any ideas on what I could try to get some wifi going in this house, I would sure appreciate it.  I love linux.  I hate running cables all over my house like its' 1997 all over again.  Thanks everyone!

---

### Post by SpiritIsReality on 2007-10-27
howdy
lots of wireless help here
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
hope it helps

[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+AR2413&meta=&btnG=Google+Search](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+AR2413&meta=&btnG=Google+Search)

trails

---

### Post by Lambert on 2007-10-28
What type of wep setting are you using? restricted or open?

I haven't used an atheros device in a while but used to have a problem if set to restricted.

[http://madwifi.org/wiki/UserDocs/Troubleshooting#WhywontmywirelessNICassociateproperlywhenIuseenablerestrictedmodeWEPonmyAP](http://madwifi.org/wiki/UserDocs/Troubleshooting#WhywontmywirelessNICassociateproperlywhenIuseenablerestrictedmodeWEPonmyAP)

---

### Post by wendallsan on 2007-10-28
Hi, thanks for the response.

Amazing, that code did the trick, time to hit the man pages and find out what they do.

Once again, THANK YOU THANK YOU THANK YOU.  This problem has plagued me and my DLink cards across multiple PC's for almost 3 years now.  All my linux boxes (lots of them) had to be wired even though every one of them had a wireless card in them.

THANK YOU!

---

### Post by wendallsan on 2008-02-26
As I had to go through and do this again with my laptop (I have now fully migrated to Linux in my household: 5 PC's, no more windoze), I figured it might be helpful to put WHAT I did to make this work.  Since I had to go back to this post and do some brain searching to remember exactly what I did, if nothing else, documenting this will help me to look it up next time I convert a box with wifi to Linux.

The problem seems to be dhclient always pulls my dns server info from my router and this supersedes any settings I manually put in for DNS which means no DNS lookups (makes surfing the web tricky).  While this works fine for Windows somehow, Ubuntu doesn't like it.  I'm using an Actiontec GT-701WG router that I got with by DSL subscription to Qwest. Symptoms are that I CAN connect to the wireless router, put in WEP keys, etc, but I can't ping anything by host name, hit any hosts on the web, etc.

SOLUTION: fire up gedit (or whatever) as root (sudo) and edit /etc/dhcp3/dhclient.conf.  Find the line that looks like this:

request subnet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, host-name, netbios-name-servers, netbios-scope;

remove the reference to domain-name-servers from the line, so it looks like this:

request subnet-mask, broadcast-address, time-offset, routers, domain-name, host-name, netbios-name-servers, netbios-scope;

The only other thing to do is to manually add a DNS server or two with the 'prepend' command.  This adds settings before the request to the router for all the jazz in the above line.  Since we're not asking our router for DNS, we're going to manually tell it to use what we want.  I use freeDNS, it's server IP's are 208.67.222.222 and 208.67.220.220, so the config line looks like this:

prepend domain-name-servers 208.67.222.222,208.67.220.220;

Out of superstition I put this before the request line that we edited above, I'm not sure if it NEEDS to go before that or not.

Hopefully this helps out others, it took me months to figure out so if nothing else it will probably help me again later.  Enjoy!

---

