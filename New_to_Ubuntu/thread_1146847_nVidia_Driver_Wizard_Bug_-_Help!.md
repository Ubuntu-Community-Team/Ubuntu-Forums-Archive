---
title: "nVidia Driver Wizard Bug - Help!"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Bezmotivnik on 2009-05-03
I can't believe how well 9.04 installed on this older system I wanted to use for a P2P server.  Perfect!

Detecting the 5200 GeForces card, the little drivers wizard icon up in the RH corner advised that I should download the proprietary driver and I went for it.

It went to the progress bar and hung at 0%. After twenty minutes, I could neither cancel or close the window.  I had no other option but to shut down.

When Ubuntu was shutting down, the progress bar finally woke up and showed 80%.

On reboot, there was a long hang as the nVidia drivers were trying to load and when they finally gave up and loaded Ubuntu there was a message that the video drivers weren't right.

So...how do I dig myself out of this mess?

Thanks for any help!  Aside from this, 9.04 is apparently working excellently.

---

### Post by cariboo on 2009-05-03
Open an Applications__>Accessories-->Terminal and type:

```
sudo apt-get -f install
```

this should complete the installation of the restricted drivers.

---

### Post by Bezmotivnik on 2009-05-03
It took a couple of more steps than that, but I **think** it's working right now. :rolleyes:

Is there a sure-fire way to tell? 

Administration> 
nVidia X Server Settings> 
System Information  

...shows driver 173.14.16, so I assume everything's as it should be now?

---

