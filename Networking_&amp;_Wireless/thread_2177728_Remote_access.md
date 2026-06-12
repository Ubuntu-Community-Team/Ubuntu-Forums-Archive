---
title: "Remote access"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by Tristan57 on 2013-09-30
OK, your mission, if you accept it is to tell me and guide me through the following, assuming this is doable:
1/ I live in Australia
2/ My elderly mother lives in France.
3/ We both use Ubuntu 12:04LTS 64
4/ I'd like to help her out when she gets lost ad/or confused with "stuff" by taking control of her machine and guiding her through the steps to, let's say, send an email or whatever she'd like to do.

Is there anything, easy for her to install (client/server) and if yes, what are the steps.

I've been using Linux for a few years but try, as much as I can, to avoid the terminal - IT'S SCARY :o)

Thank you so much in advance, oh patient ones.

Tristan

---

### Post by coldraven on 2013-09-30
This might help:
[http://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/](http://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/)

---

### Post by Bucky Ball on 2013-09-30
> **coldraven said:**
> This might help:
[http://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/](http://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/)

That will work for two machines on the LAN side but will take a bit more than that to communicate with anything on the WAN side, especially security wise. Good start though. It would possibly be a tweak of this basic LAN remote setup. ;)

---

### Post by Lars Noodén on 2013-09-30
If you can make your long distance phone call over SIP using Jitsi,  Blink, Ekiga or Linphone you can use them.  I'm pretty sure that they all support screen sharing and the sound quality is better  than Skype (which is going away sooner or later).  

Or you could go the old route of tunneling VNC over SSH, but that takes some setting up.

---

### Post by sammiev on 2013-09-30
Why not try Teamviewer first, likely all you will need. ):P

[HTML]http://www.teamviewer.com/en/download/linux.aspx[/HTML]

---

### Post by Lars Noodén on 2013-09-30
> **sammiev said:**
> Why not try Teamviewer first...

Teamviewer is proprietary, though.  The other solutions above are Free/Libre Open Source Software.  F/LOSS is generallly preferable when it is available.  If for no other reasons than development is usually faster and the support is better.

---

