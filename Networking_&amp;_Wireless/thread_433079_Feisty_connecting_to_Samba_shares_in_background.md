---
title: "Feisty connecting to Samba shares in background"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by muecker on 2007-05-04
Since upgrading to Feisty, I have had a problem with my network account getting locked out.  I finally started running Wireshark and monitoring my TCP/IP access looking for login attempts.  In the logs I found several attempts to connect to Windows shares I have configured via Places->Connect to Server.  It seems that my machine is attempting to connect to these shares even though I have made no attempt to do so myself.  Worse yet, I have no idea what password it is attempting to use and it never prompts me so my account is getting locked out.

I deleted every one of the network shares I had mapped and the problem continued.  I shut down samba and it continued to attempt to connect.  Today I found a lot of smb files under ~/.nautilus/metadata and deleted those.  Unfortunately there is a x-nautilus-desktop (looks like positions of the icons) file that also lists those shares, but I cannot edit it :(  Hopefully that file isn't being used to establish connections.

I reported the following bug yesterday when I thought I had figured out the complete problem but I'm still working on a final solution.

[https://bugs.launchpad.net/bugs/112220](https://bugs.launchpad.net/bugs/112220)

---

### Post by ronocdh on 2007-05-04
I would try trashing the x-nautilus-desktop file (rather than editing it). Also, have you purged Samba and reinstalled, reconfiguring your setup?

It sounds from your introductory statement that you did not install Feisty from a CD, but rather used the update commands. If this is the case, I think purging Samba and reconfiguring, although a pain, would be beneficial.

---

