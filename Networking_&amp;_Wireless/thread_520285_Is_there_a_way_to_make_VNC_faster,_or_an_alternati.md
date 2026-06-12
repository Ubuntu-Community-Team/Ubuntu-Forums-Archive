---
title: "Is there a way to make VNC faster, or an alternative?"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by ownaginatious on 2007-08-08
For some reason the built in RDC VNC server support in ubuntu is really slow when I log into my ubuntu computer from other machines. This is on my LAN, and it's really disappointing. I've never really been a fan of VNC due to this problem. Is there a way to simply make it faster, or a better alternative? I may give other VNC software a try if others suggest it. Any help will be greatly appreciated, thanks!

---

### Post by kevdog on 2007-08-08
TIghtVNC works -- its nearly universal  -- on both windows and linux, but its speed is a major drawback.  Im not expert in the area, but did manage to setup as an alternative a nxserver which I have found to be much faster than vnc.

The only difference between the two, is that freenx actually gives you a separate login shell into the server, whereas in vnc a client and server user could physically interact in the same session or on the same screen.  This isnt possible with nxserver since it acts as a remote login creating a separate session.  The speed however is amazing

Here is a link to get you up and going if you are at all interested in trying it out to see if it meets your needs:
[http://ubuntuforums.org/showthread.php?t=467219](http://ubuntuforums.org/showthread.php?t=467219)

---

