---
title: "Networking stops unexpectedly"
date: 2015-08-07
forum: Networking &amp; Wireless
---

### Post by MrGibbage on 2015-08-07
This happens about every 30 minutes or so. I'll be watching a movie on Plex, when all of a sudden I get a Media not available error. So today I started troubleshooting. I was watching a movie, and the error popped up. I immediately went and VPN'ed in to start troubleshooting. OK, since I VPNed in, the networking must be OK, right? Well, I couldn't ping google. And I couldn't ping my gateway on 192.168.1.1 (100% packet loss). But the other computers on my network still could reach the gateway and surf the web, so it's only my Ubuntu box. I stopped and restarted the network, and bam, everything started working again. All the while, no other error messages have popped up on the box.

This is all relatively new. I've been using this box for a few years, and haven't done anything to in in the last few months. But I would say this all started a month or two ago.

I am on Ubuntu 13.10, and can provide other information as needed. I am pretty decent on Linux, but not a rock star like some of you guys/gals. But I sure do hope someone can give me some ideas.

Skip

---

### Post by papibe on 2015-08-07
Hi MrGibbage.

A few questions:

Is this a desktop or a server edition?

Is it on vanilla DHCP, a reservation, or using a static IP?

Who's the DHCP server on your network?

Are you watching the movie locally on your network, or remotely over the Internet?

Regards.

---

### Post by MrGibbage on 2015-08-07
It is a desktop edition.
I have statically assigned the IP address
I am watching the movie on Chromecast, so I think it is using the local network. Looking through the plex logs, I see errors referring to plex not being able to reach certain external services. I think Plex needs to talk periodically to these sites to do it's thing and when that can't happen, plex just says the media isn't available. The bottom line is, the networking is going wonky, and I need to figure that out.

I guess one thing I could do next time it happens is see if I can play the video locally on the machine. Based on what I have gathered here so far, my suspicion is yes, I will be able to.

Thanks for replying!!!

Skip

---

### Post by papibe on 2015-08-07
Thanks.
> **MrGibbage said:**
> I have statically assigned the IP address
How? Using the network-managet GUI tool, or using directly '/etc/netork/interfaces'?

Are you accessing the server by name or IP?

Regards.

---

### Post by MrGibbage on 2015-08-07
I set the IP using the nm-connection-editor. I have had this system running for a couple of years without trouble, which makes it even stranger.

Remember, it's not that I am having a problem reaching the server. It's that the box forgets how it is connected to the internet and won't make any connections. I can reach the box from other boxes on the network, and it can reach other boxes as well. It can't however, ping google or even the gateway (my cable modem) on 192.168.1.1. So, pinging other boxes is no problem, but finding the gateway is. All this time, all of my other computers that use the same gateway are doing just fine, so I know the gateway is up. I just need to figure out why my Ubuntu box can't. What's more, if I turn the Ubuntu network connection off and back on, everything works fine. I gotta think this is the smoking gun here.

---

### Post by gordintoronto on 2015-08-08
Ubuntu 13.10 reached end of life over a year ago, which makes the resolution that much more difficult.

---

### Post by MrGibbage on 2015-08-09
I upgraded to 14.04 today. So far so good. Thanks for the help, and if I start having troubles again, I'll be sure to shout it out here.

---

