---
title: "confused about Ad Hoc networking and static IPs"
date: 2019-10-25
forum: Networking &amp; Wireless
---

### Post by heaneye on 2019-10-25
Hi,

I'm trying to set up an ad-hoc network on my Raspberry Pi (running Ubuntu Mate) so that I can SSH into it from my laptop. 

Several of the guides I've found online (like this: [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc) and this: [https://askubuntu.com/questions/1032497/ubuntu-will-not-connect-to-existing-ad-hoc-network](https://askubuntu.com/questions/1032497/ubuntu-will-not-connect-to-existing-ad-hoc-network)) have said that I need to assign a static IP address to both devices before I can connect to the ad-hoc network. But all the tutorials on how to assign a static IP seem to imply that static IPs are assigned for a device's connection to a specific network.

So I'm having this chicken-and-egg problem: I can't assign my laptop a static IP for my ad-hoc network without first having a connection to it, and I can't connect to it without a static IP.

Am I understanding this correctly? Is there a way to set up a static IP for my laptop that corresponds to my Pi's ad-hoc network?

Thanks!

---

### Post by TheFu on 2019-10-25
You need to be on the console of each device to setup static IPs.  This cannot be accomplished any other way if all you have are 2 computers.

As for the network setup information on each computer, they just need to be on the same LAN.  You get to pick that subnet.  For simplicity, let's say you choose the 10.1.1.1/24 subnet.

Assign the **computer** to 10.1.1.2 with a netmask of 255.255.255.0 and a default gateway of 10.1.1.3

Assign the **r-pi** to 10.1.1.3 with a netmask of 255.255.255.0 and a default gateway of 10.1.1.2

Now, if you use the IP addresses for all connections, then both systems can talk to each other.

How you would accomplish this with a wifi network, I don't have any clue.  There are a few security problems with ad hoc networks and wifi.

But if you have $5 and a goodwill store nearby, you can get a cheap, used, router and connect both devices with $2 ethernet cables, let the router provide DHCP addresses and not have to setup static IPs on either device. Much easier, especially if both systems run avahi.  [https://manpages.ubuntu.com/manpages/bionic/man8/avahi-daemon.8.html](https://manpages.ubuntu.com/manpages/bionic/man8/avahi-daemon.8.html)  Avahi has been installed on Ubuntu desktop releases for a while.  I don't know about raspberry pi OSes and avahi.

If you'd like to understand IPv4 networking better, google for "Security Now Ep 25".  Ep 25, 26, 27, explain how the internet works for IPv4. It is simple, elegant, and easy to understand without getting too bogged down in the bit masking. There are transcripts and a podcast.  Some other people have cut up the audio to remove all the "banter" that Steve and Leo add into the podcasts, getting to the point more quickly.  Vaguely remember seeing a re-do of those episodes years later, but I wasn't listening to them anymore.

---

### Post by DuckHook on 2019-10-26
*Thread moved to **Networking & Wireless** as the more appropriate forum.*

---

