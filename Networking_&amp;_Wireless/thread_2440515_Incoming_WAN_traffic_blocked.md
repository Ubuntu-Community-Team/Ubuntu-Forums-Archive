---
title: "Incoming WAN traffic blocked"
date: 2020-04-12
forum: Networking &amp; Wireless
---

### Post by couzin2000 on 2020-04-12
I'm setting up a dedicated Minecraft server. I have this brand spankin' new, freshly installed 18.04 LTS. Did all the upgrades that I could from within Canonical and "partners" repos enabled. 
I've setup my hardware router to allow traffic on ONE specific port. I checked from WAN side, the port is currently CLOSED. All the other ports are STEALTHED. So this one port reports it exists... but doesn't let anything through.
I checked to see if [FONT=Courier New]ufw[/FONT] was turned on by default, it isn't. I haven't installed anything else than just the straight .ISO image with minimal install. I know how to setup port forwarding and I have done it before. It is properly setup inside my router.

My UB game server seems to work from within the LAN - I can connect to the Ubuntu dedicated server from a Windows 10 machine and the system works fine. Somehow something is blocking the port. But it isn't the router's firewall. 

Do any of you know of any software that would block it straight from the default install of LTS? I ask because I'm out of ideas here.
I can sent you screen readouts of anything of you guys beed. And yes, I checked this forum first for answers.

Edit: I just turned on the DMZ on the Ubuntu server's LAN IP, so it is completely opened. YET... I still cannot connect to that port.

---

### Post by TheFu on 2020-04-12
Have you checked the configuration for the specific service?   is  it lock down to just the LAN?
Perhaps use ss or netstat to see which port(s) are listening?

There's nothing else.  Check the ports all along the chain again.  Sometimes when  I&#8217;m asked to prove stuff like this, the effort in double-checking everything makes the config problem jump out.  Start w/ something easy.  Check the static ip of the server.

---

### Post by couzin2000 on 2020-04-13
> **TheFu said:**
> Have you checked the configuration for the specific service?   is  it lock down to just the LAN?
Perhaps use ss or netstat to see which port(s) are listening?

There's nothing else.  Check the ports all along the chain again.  Sometimes when  I’m asked to prove stuff like this, the effort in double-checking everything makes the config problem jump out.  Start w/ something easy.  Check the static ip of the server.

I just did that now. Thanks, that's really what I needed.
I actually also ran a test - installed a server version on my Windows machine and tried to access it from outside. I went into the router to save new Port Forwarding addresses. The test was successful and I connected, so there had to be something that was wrong.

There was. The Port forwarding destination IP was incorrect. Typo, I guess.
Thanks for reading through and pointing to the obvious. :-)

---

