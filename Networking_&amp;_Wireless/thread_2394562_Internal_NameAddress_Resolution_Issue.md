---
title: "Internal Name/Address Resolution Issue"
date: 2018-06-18
forum: Networking &amp; Wireless
---

### Post by regnumimbriumx on 2018-06-18
Hi all, I'm a casual server hobbyist so please forgive my ignorance. 

I recently put up an 18.04 home server with Nextcloud. Nextcloud provides a smartphone app which connects to the server. I want to be able to put in my external server address, cloud.example.com, and have it work both outside of AND within my home. However, I find that while it works flawlessly over VPN our outside of my home, connections over the LAN within my home are sporadic, and I often receive "page couldn't load" errors. Refreshing a few times will eventually restore the connection for a few seconds or minutes, but it persistently drops out.

I have modified the /etc/hosts file **as such**:

127.0.0.1     localhost.localdomain     localhost
::1               localhost6.localdomain6     localhost6
[B]127.0.0.1     localhost.localdomain     example.com
127.0.0.1     localhost.localdomain     cloud.example.com[/B]

The firewall is accepting all necessary Apache connections. There do not appear to be rules in my router affecting access. For those familiar with Nextcloud, I have also added several permutations of my internal IP and domain name to the trust domains list. 

Can someone help me determine why my within-network connection is so unreliable? Am I forgetting some settings which would allow better within-network name/server resolution? Thank you!! :KS

---

### Post by TheFu on 2018-06-18
Android only uses DNS for name resolution, so you must setup DNS server inside your home for the correct, static, nextcloud server to be found using the internal LAN IP.  You can thank google for this. I think it is in Android 6.1.1 and later, but it may have happened in v6.0
[https://superuser.com/questions/1160425/configuring-android-7-1-device-to-use-local-dns-server](https://superuser.com/questions/1160425/configuring-android-7-1-device-to-use-local-dns-server)

127.0.0.1 is**Not** the correct LAN IP, so it appears you need to learn a little more about IPv4 networks and subnetting.  [https://en.wikipedia.org/wiki/Private_network#Private_IPv4_addresses](https://en.wikipedia.org/wiki/Private_network#Private_IPv4_addresses) has a table of private IP networks that are seen in the world.  If you want to connect from the outside world, then your internal LAN subnet should be one that isn't commonly used by anyone else.  That means avoiding 192.168.[01].x and 10.1.x.x and 172.16.x.x subnets.  After all, you can't route VPN connections from 192.168.1.x at a library to 192.168.1.x inside your home.  Routing doesn't work that way.

First thing you need is to make the nextcloud system have a static IP, no DHCP (unless you want to setup DHCP reservations).

BTW, I run a nextcloud server here and an openvpn VPN server for secured connections from the outside world.  I do not allow direct https:// connects to nextcloud over the internet.

---

### Post by regnumimbriumx on 2018-06-18
Hi Fu, thank you for the informative response! I miscommunicated some things in my initial post, so let me add some details.

Although I would love to connect from the Android at home (and now understand that this won't be possible, since I don't want to maintain a DNS server), I'm also experiencing the sporadic connectivity when using **any **computer inside my network. It's more important to me to fix it for those (Windows) computers.

Also, I misremembered when I said that I edited the hostnames file, previously; I actually edited the /etc/hosts file. **Sorry!** I assumed that the connectivity issue might be due to some kind of name resolution problem, which is why I started there. I actually know a bit more than I've let on, as I've maintained an Ubuntu server for over a decade - I just took 2 years off so I'm shaking off the rust (though I'm still essentially casual/novice). So, a few additional questions, if you don't mind:

On-topic:
1)  Would it be possible to fix the connectivity issue for PCs inside the network trying to speak to my server? If so, could you recommend a few avenues to start investigating?

2) I tried to set up the static IP prior to posting, but was having a little trouble figuring it out using netplan. I'll make that my first priority, though. Is it the nature of how DHCP works that is causing my connectivity issues? I figured that as long as my router didn't allocate a new address to my server that I would be okay working off of a non-static IP for a short while.

Off-topic:
1) Why would you recommend against direct https:// connections over the internet? 

2) Would you mind elaborating on your configuration - and the reasons why - a bit? Do you make external connections to your VPN server, which then accesses your nextcloud server? Or is your nextcloud server literally only accessibly from within the network? 

If nextcloud is simply an insecure platform, it would be helpful to know, and I'll be sure to explore other platforms. Thank you again, Fu!

---

### Post by TheFu on 2018-06-19
I don't trust php webapps. Too many reasons to list. You can google - "owasp php" to start. That means allowing access to any of those over the internet is something I won't do.  But some are very useful, so access over a VPN from outside my network is the compromise.  It prevents anyone in the world from being able to hack 24/7/365 while letting trusted VPN users have access.

Risk mitigation is important.  php webapps have large security risks.

My network is more complicated than most. Describing it isn't useful for people not willing to run an internal DNS server or multiple subnets and if they won't require wifi clients to use VPNs, forgetaboutit.

A newly published IoT attack: [https://www.wired.com/story/chromecast-roku-sonos-dns-rebinding-vulnerability/](https://www.wired.com/story/chromecast-roku-sonos-dns-rebinding-vulnerability/)  basically, DNS can be abused much more than most people understand.  There are always issues like this, unpublished.  Always.  Across all platforms.

---

