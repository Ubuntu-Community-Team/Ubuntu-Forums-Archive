---
title: "Bootup stalled by wireless config..."
date: 2005-12-05
forum: Networking &amp; Wireless
---

### Post by vinoloco on 2005-12-05
Hi all,

I'm running Ubuntu Breezy on a nice IBM Thinkpad T43 with built in wireless (Intel ipw2200).  Everything works great.  The only issue is when I boot up the machine I have to wait about 5 min. during the process for the system to "configure network".  I think it is looking for the network and then timing out because it eventually gives me a failure message and then continues on.  When the system comes up I can re-associate to the AP I want and everything is fine from there.  Is there a way I can get rid of the delay on bootup?  I'm sure there is, I just don't know how.  Thanks in advance for the help.

  vino

---

### Post by jakev383 on 2005-12-05
[QUOTE=vinoloco]Hi all,

I'm running Ubuntu Breezy on a nice IBM Thinkpad T43 with built in wireless (Intel ipw2200).  Everything works great.  The only issue is when I boot up the machine I have to wait about 5 min. during the process for the system to "configure network".  I think it is looking for the network and then timing out because it eventually gives me a failure message and then continues on.  When the system comes up I can re-associate to the AP I want and everything is fine from there.  Is there a way I can get rid of the delay on bootup?  I'm sure there is, I just don't know how.  Thanks in advance for the help.
[/QUOTE]

If you're brave, you can edit the rc files. Read this post:
[http://www.ubuntuforums.org/showthread.php?t=59420](http://www.ubuntuforums.org/showthread.php?t=59420)
Or you can hit CTRL-C while it's sitting there and it will stop trying to bring the  network up and move on.

---

