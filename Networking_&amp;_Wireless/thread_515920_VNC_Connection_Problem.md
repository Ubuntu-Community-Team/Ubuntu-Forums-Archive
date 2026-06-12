---
title: "VNC Connection Problem"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by jdb1981 on 2007-08-02
I'm having a problem with the speed of my VNC connection to my server. When accessing it remotely, it was previously a bit sluggish, and the color went in and out a little, but nothing that really affected usability. Yesterday, I switched my JVM from gij to Sun Java 6, and it really helped my torrent speeds, but when accessing the server remotely on VNC now, it's so slow as to be unusable. The color goes much further down in quality, and the refresh rate is much worse. Most of the other posts I read concentrate on VNC that just plain doesn't work, but mine just slowed to a crawl. I'm running Ubuntu Server Feisty, Xubuntu desktop, fully updated, with x11vnc on the server side, and UltraVNC Viewer on a windoze XP box on the client side, all appropriate ports forwarded, etc...

I can't imagine what would be holding things up; except that possibly much more (almost all?) of the available bandwidth is being used by Azureus to DL/UL torrents, and this is somehow squeezing out VNC bandwidth, and that it worked OK before because prior to updating Java, Azureus wasn't running to it's full potential... It is WAY faster now... If so, how do I prioritize for VNC service on the server, rather than on the router by port? The  server's bandwidth is already throttled according to activity on other clients on the local network, (which have a higher priority, so torrents slow down/stop if I surf from another computer,) so I'd like to find a solution within the server, if that's even my problem... 

Anyone have any ideas?

---

### Post by jdb1981 on 2007-08-02
I have worked out a fix, by specifying a connection speed on the client side  that was consistent with the connection speed being reported by VNC Viewer at login (the default is a variable "AUTO" setting,) and decreasing the max Upload speed for torrents by 5k/sec from 40 to 35 in Azureus. This seems to have stabilized the whole thing, though at the expense of full-resolution graphics. (Boo Hoo, 256 color will have to do...) I may have been experiencing some ISP slowdown that was contributing to the situation, as well, it certainly wouldn't be the first time.

 Anyhow, unless anyone who happens to read this knows of trouble I may run into down the line with the above setup, or it craps out again, I can close the book on this one... Thanks!

---

