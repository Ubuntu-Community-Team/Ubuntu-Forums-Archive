---
title: "Looking for method of proxy'ing all network data to another machine"
date: 2017-03-05
forum: Networking &amp; Wireless
---

### Post by richgreder on 2017-03-05
Hello,

I have two computers, in two very different regions of the world.  In the name of market segmentation and geographic marketing, or governmental censorship, certain sites are blocked or limited.  I've used an SSH SOCKS proxy in the past, and that has been helpful for most cases, for example, getting the 'correct' Google or Bing to load, but I frequently see websites incorporating various forms of active content that reveals my location.  (Especially flash player which I'm occasionally forced to use).

I have an Ubuntu server at home.  I travel with my MacBook and my Parallels Ubuntu image.  I want to basically extend the cozy bubble of my home LAN to travel with me, no matter where in the world I might be.

I expect that there is some root-level one-liner I could type on each machine's command line to make ALL data be delivered to my home computer, encrypted, and then handed to my portable machine (and vise versa).  I cannot find such a tool...

What have other globe-trekkers done about this?  i.e.  Watching certain BBC web-video content outside England, listening to [good] Youtube music in Germany, posting on Facebook in Iran, et cetera?

Also, I'm not concerned with being questioned about the content of encrypted data in authoritarian regimes.  That is a political topic that I'm not interested in discussing in a software/engineering forum.

---

### Post by TheFu on 2017-03-05
You want **openvpn**. It isn't a one-liner, however.  Also, be certain to use either the IPSec or L2TP protocols. Avoid all the others.  OpenVPN is extremely powerful, hence it has hundreds of options, each with pros and cons.

There are openvpn clients for pretty much every networked OS.

Or you can use an efficient remote desktop that uses ssh tunnels to make the connection.  I use **x2go**, which uses ssh (keys/keyfiles/passwords) and feels about 2-3x faster than any VNC solution.  Basically, all the data is handed at the remote location (your house?) and displayed where ever you are. This is why just TCP tunneling is needed. No UDP would be leaked, since that traffic would all happen at the remote location.  I consider it safe.  There are clients for OSX, Linux and Windows. The Linux and Windows clients are extremely solid, since I've been using them daily for a few years.  Not good for video or audio playback when remote, but for standard office-type stuff, browsing and emails, it is sufficient. It doesn't suck.   I use x2go daily to connect to my primary desktop, running inside a virtual machine in a private cloud.  That VM is available to me from anywhere in the world with internet, my ssh-keys, and the x2go client.

I cannot help with watching geo-locked videos.

---

