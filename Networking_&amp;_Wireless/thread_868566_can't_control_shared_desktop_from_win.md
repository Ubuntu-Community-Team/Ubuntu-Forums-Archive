---
title: "can't control shared desktop from win"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Njem on 2008-07-24
Trying to control Linux box from Win XP box. 

This is all in-house, no router issues.

My Linux box can fetch files from XP shares. It can connect to XP boxes by KRDC Remote Desktop Connection (this is Kubuntu). It comes close to working the other way, the XP box controlling the Linux box but...

I have desktop sharing set to accept uninvited connections and to not need confirmation (so I can do remote admin). If I try to connect by Win RDP it comes back with a "protocol error code 0x1104" which MS knowledgebase makes no reference to. The Linux box will show there was a request to connect and ask confirmation. I click OK and it says the other end has terminated.

If it did connect I can only assume it would have connected to the current or 1st desktop.

So I tried TightVNC. It works and connects to the Shared Desktop and to the current or 1st desktop, which would allow me to help a novice Linux user. But it still insists on confirmation from the Linus user, which is no good for remote admin.

If I set Desktop Sharing to have no password (unsafe but something to try) it allows connection without confirmation but doesn't give control.

Suggestions appreciated. This is the first Linux box in a Win network and if I can get these support pieces working could make the difference in acceptance. Maybe being a novice I'm just going at it wrong.

Thanks,
Tom

---

### Post by sonofusion82 on 2008-07-24
for me, I usually use VNC over SSH connection, so it is somewhat secure enough even for remote from internet.
have a look at this page: [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)
alternatively, I have heard of good comments about NoMachine NX from my friends although I have not really try it since VNC over SSH solution, although not the easiest way, but works good enough for me.

---

### Post by IguanaC64 on 2009-07-15
I have the exact same problem.  Just installed Ubuntu 9.04, XBMC, LIBUSB stuff, and Wiimote stuff...that's it.  I configured remote desktop server w/ password.  I'm using TightVNC v1.3.9 as the client on WinXP.  I connect just fine...get the screen (reso = 1920x1080).  Will not let me gain control of the desktop.

I don't want to use Nomachine NX because it looks like a pay product and this free solution should be working...

---

