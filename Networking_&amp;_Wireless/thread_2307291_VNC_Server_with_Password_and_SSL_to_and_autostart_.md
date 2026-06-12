---
title: "VNC Server with Password and SSL to and autostart without any prompt before running"
date: 2015-12-23
forum: Networking &amp; Wireless
---

### Post by dirk-lehmann on 2015-12-23
Hello Ubuntu-Users,

I was wondering if anybody would give me a hint which open source license VNC (virtual network connection / mostly on port 5900 or 5901) serversoftware to use. :---)

- The VNC server must autostart after booting and accept password protected SSL-connections after the boot process without any further inputs or prompts. ](*,)

I need that possibilitys to manage a hardware-server from a other client because the server has no display connected at the moment and should therefore be able to get managed by VNC directly after Ubuntu startup phase. \\:D/

The license for the VNC serversoftware should be free of charge even for commercial purposal and should be not to complicated to get installed with these requirements I wrote.

Would be happy to get a answer from someone how has such a VNC software running at startup (maybe also on a maschine without display). =d>

Best regards and merry christmas all around the world! ):P

Dirk

---

### Post by TheFu on 2015-12-24
VNC use requires a VPN for security reasons.
For that reason alone, something like the NX protocol (which includes ssh) could be a better choice. There are a few implementations, but x2go has a fairly stable version with simple instructions.  Add their PPA for the server, install, and if ssh is already configured, it "just works."  BTW, NX feels 2-3x faster than any VNC I've seen.  I'm using it right now from 3 states away. 

x2go has clients for Linux, OSX, and Windows.  The Linux and Windows clients are really stable. I use both daily ... rebooting about once a month.

Ask if you'd like to know more.

With VNC, if you decide that is the only solution, be certain to run the vnc-server with --local options to force folks to ssh into the machine/tunnel to get a secured connection.  Better security begins by not allowing end-users to do stupid things.

Happy Festivous!

---

