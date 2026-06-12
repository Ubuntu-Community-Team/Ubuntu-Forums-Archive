---
title: "No signal. How to set nomodeset from grub2 menu?"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by pissedoffdude on 2010-10-16
I've just installed ubuntu 10.10 but have not been able to get it to boot.  When I try booting, I'm told that there is no signal.  I was not able to get the ubuntu cd to boot unless I used the nomodeset paramater under other options by pressing f6.  This was a problem with lucid as well, but I was able to keep the nomodeset paramater after installing lucid.  How would I add the nomodeset paramater to the grub2 entry so that I could boot ubuntu? My gfx card is an nvidia 9600gt btw.\\

Problem solved!
For anyone having a similar issue, add the "nomodeset" paramater (no quotes) after quiet splash in the grub menu.  From there, install appropriate video drivers and you should be good to go.

---

