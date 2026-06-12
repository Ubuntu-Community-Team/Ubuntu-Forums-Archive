---
title: "ekiga on LAN"
date: 2022-10-31
forum: Networking &amp; Wireless
---

### Post by jvglynnjr on 2022-10-31
I'm trying to use *ekiga* to videoconference with several Linux computers on a wifi LAN. They all have identical configurations, but some pairings will randomly fail to connect with a "User is not available" message. 

In the contacts display, "Neighbors" seem to show up arbitrarily. Sometimes a connection can be made from A to B but not from B to A. 

I don't even know where to start troubleshooting this. I don't see *ekiga* show up in the syslog. 

Can I fix this, or is *ekiga* too unstable?  Is there a better program for this application?

---

### Post by TheFu on 2022-11-03
I have a netcloud talk server.  There are nextcloud talk clients for android devices and any web browser with webRTC can use the nextcloud talk webapp from the nextcloud GUI.  On a LAN, this is pretty easy to use.  Voice, video, text, desktop sharing .... [https://nextcloud.com/talk/](https://nextcloud.com/talk/)  The desktop sharing is new in NC 13+.

I use Jitsi Meet for hours each week. Spinning up your own server instance took an intermediate Admin about 20 minutes.  I suspect there's a Docker image.  Again, there's an android app for it or any webRTC capable browser can be used.
[https://community.jitsi.org/t/jitsi-quick-install-and-lxd-in-ubuntu-18-04/19142](https://community.jitsi.org/t/jitsi-quick-install-and-lxd-in-ubuntu-18-04/19142) Ubuntu LXD/LXC.
[https://github.com/jitsi/docker-jitsi-meet](https://github.com/jitsi/docker-jitsi-meet) - Docker

I don't use Apple stuff, so don't know anything about those.

If you already use nextcloud, it would make sense to add talk to that server.  If not, I'd got for a jitsi meet container solution.

---

### Post by jvglynnjr on 2022-11-03
> **TheFu said:**
> I have a netcloud talk server.  There are nextcloud talk clients for android devices and any web browser with webRTC can use the nextcloud talk webapp from the nextcloud GUI.  On a LAN, this is pretty easy to use.  Voice, video, text, desktop sharing .... [https://nextcloud.com/talk/](https://nextcloud.com/talk/)  The desktop sharing is new in NC 13+.

Correct me if I'm wrong, but this looks like a link offering to sell me a service. I don't want to buy a service; I just want to run free, open-source software on my LAN.

> 

I use Jitsi Meet for hours each week. Spinning up your own server instance took an intermediate Admin about 20 minutes.  I suspect there's a Docker image.  Again, there's an android app for it or any webRTC capable browser can be used.
[https://community.jitsi.org/t/jitsi-quick-install-and-lxd-in-ubuntu-18-04/19142](https://community.jitsi.org/t/jitsi-quick-install-and-lxd-in-ubuntu-18-04/19142) Ubuntu LXD/LXC.
[https://github.com/jitsi/docker-jitsi-meet](https://github.com/jitsi/docker-jitsi-meet) - Docker

These links look hideously complicated, like I would have to be a network programming expert to make any sense of them. Isn't there anything simpler, out of the box, like *ekiga*?

---

### Post by TheFu on 2022-11-03
> **jvglynnjr said:**
> Correct me if I'm wrong, but this looks like a link offering to sell me a service. I don't want to buy a service; I just want to run free, open-source software on my LAN.
Nextcloud is a self-hosted, 100% F/LOSS server. It has addons that are also 100% F/LOSS.  I suppose some people don't want the hassles that running their own server entails.  I can assure you, I have a nextcloud server running on my LAN and it has the "Talk" application add on.


> **jvglynnjr said:**
> 
These links look hideously complicated, like I would have to be a network programming expert to make any sense of them. Isn't there anything simpler, out of the box, like *ekiga*?

"Jitsi meet" is provided to make connecting trivial for end-users, but as with most server stuff, the setup is non-trivial. It is also 100% F/LOSS, but again, you can pay someone else ... or use meet.jit.si for free.
[https://alternative.me/jitsi](https://alternative.me/jitsi) says that it is simple to deploy for video conferencing. [https://jitsi.org/](https://jitsi.org/)

Sorry you felt the links weren't useful.  I didn't look too closely, but tried to find the project pages from the project teams.

In computing, things that seem simple usually mean that some admin somewhere spent great effort to make it that way or the vendor behind it is stealing our information without asking.  Apple's video conferencing is like that.  We get sucked into a walled garden and only they run the servers. Nobody else is allowed.  Same for Amazon's Chat or Google's Talk.  They run the servers and grab all our information, connections, and other metadata without asking.

When you run the servers yourself, there are complications, flexibility AND some effort involved.

I was never able to get ekiga working when I tried previously.  OTOH, NC Talk sorta "just worked" and has been working for years now.  Every 3-6 months, I have to patch the NC program manually and weekly I patch the OS as I patch the rest of my systems.

But not every solution meets everyone's needs.  Just providing options that I know work, because I use them.

---

### Post by jvglynnjr on 2022-11-03
Your point is well taken, and I thank you for your thoughtful reply.

---

