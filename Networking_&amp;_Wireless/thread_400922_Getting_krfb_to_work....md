---
title: "Getting krfb to work..."
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by rillip on 2007-04-04
So, I'm trying to set up krfb to run so that I can connect to my home machine from work.

I'm behind a DL-604 broadband router, which is plugged into my cable modem with one other machine.

I've set up port forwarding for the outside port of XXXXX to the private port of 5900 (you can know my private port, since you can't use it! ;)) for my computer's private IP.

I have krfb setup to allow uninvited sessions, using a password, without conformation, using port 5900 and announce service on network.  I have it allowing the background image.

When I open krdc, I type in my public: publicPort  (xxx.xxxx.xxx.xxx:XXXXX ) (without the space, but it turned into the :p smiley if I left it as I type it)

It sits there for a reaaaally long time "establishing connection" then gives me the error "Connection failed. No server running at the given address and port."

I tried running a netstat -l | grep 5900, but it never returns. I run nestat -a | grep 5900 but it never returns. I runa  netsat -l and netsat -a and they return, EVENTUALLY (we're talking reaaally slow) but I do not see the port listed as listening or connected.

It seems like the krfb isn't actaully running... what am I missing here? :confused:

Update: Okay, issue partially resolved.  I finally got the output of netstat and the port was listening.  Tried to connect and bingo, it worked.  I don't understand why it took so long for the port to start listening though.  Anyway, once connected, I could see everything, but my mouse just blurred whenever I moved it, and I couldn't interact.  Uninvited connections are allowed to control the desktop.  Then after about a minute, it told me I had been disconnected.

Now, keep in mind I'm connecting from the local machine TO the local machine, so I imagine that's a very very bad idea and might have caused that, but wanted to get everyone else's opinion on this, just in case I'm missing something.

---

