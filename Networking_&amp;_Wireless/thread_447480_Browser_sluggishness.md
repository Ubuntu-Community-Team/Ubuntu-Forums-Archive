---
title: "Browser sluggishness"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by Unconscious on 2007-05-18
For quite a while now I, as well as a number of others, have been complaining of bowser sluggishness, in certain environments. I have tested this with numerous browsers under a number of differing conditions. I usually use firefox, and I thought it might have something to do with the browser, but it seems not to. At least some of the problem is Ubuntu, and some of it is my home network environment.

Under Ubuntu (6:10 edgy), I can't even load some pages (weather.com, njtransit.com).  They take so long, they just time out. I tried using different browsers (konqueror, nautilus, lynx), with no improvement. I've disabled IPV6, and made every configuration modification that I've seen suggested in these forums to no avail. On my windows XP box, with the same browser (firefox), on my home network, these same pages load very quickly. For a long time, the yahoo mail signon page would not load under ubuntu, on my home network, but a few months ago, something changed (I didn't knowingly tweak anything to make this happen), and I suspect it was on the yahoo side. Now I can use yahoo mail, although it is still significantly slower to load than in windows.

For other reasons, I installed the VMware player and installed windows 2000 pro on it, using NAT networking. Same sluggishness with firefox, and IE.

At work, I am also using Ubuntu. There the browser loads these problematic pages slowly, but fast enough to complete. I recently installed Ubuntu on a new box, at home. Basically the same as the one I had already set up. Same issues on my home network. I brought it into work to use it there, and the browser works fine. Still slower than windows, but fast enough.

Clearly there is an issue with my home network connectivity, although windows handles that. However, there is clearly an issue with Ubuntu networking as well. Is this issue being addressed? Is there an explanation? How can I resolve this?

---

### Post by stchman on 2007-05-18
> **Unconscious said:**
> For quite a while now I, as well as a number of others, have been complaining of bowser sluggishness, in certain environments. I have tested this with numerous browsers under a number of differing conditions. I usually use firefox, and I thought it might have something to do with the browser, but it seems not to. At least some of the problem is Ubuntu, and some of it is my home network environment.

Under Ubuntu (6:10 edgy), I can't even load some pages (weather.com, njtransit.com).  They take so long, they just time out. I tried using different browsers (konqueror, nautilus, lynx), with no improvement. I've disabled IPV6, and made every configuration modification that I've seen suggested in these forums to no avail. On my windows XP box, with the same browser (firefox), on my home network, these same pages load very quickly. For a long time, the yahoo mail signon page would not load under ubuntu, on my home network, but a few months ago, something changed (I didn't knowingly tweak anything to make this happen), and I suspect it was on the yahoo side. Now I can use yahoo mail, although it is still significantly slower to load than in windows.

For other reasons, I installed the VMware player and installed windows 2000 pro on it, using NAT networking. Same sluggishness with firefox, and IE.

At work, I am also using Ubuntu. There the browser loads these problematic pages slowly, but fast enough to complete. I recently installed Ubuntu on a new box, at home. Basically the same as the one I had already set up. Same issues on my home network. I brought it into work to use it there, and the browser works fine. Still slower than windows, but fast enough.

Clearly there is an issue with my home network connectivity, although windows handles that. However, there is clearly an issue with Ubuntu networking as well. Is this issue being addressed? Is there an explanation? How can I resolve this?

I too experienced this and it even affected applications.  Your host and hostname files need to be fixed.  Follow these procedures as they helped me.

[http://www.stchman.com/conf_host.html](http://www.stchman.com/conf_host.html)

Also use the OpenDNS servers.

[http://www.stchman.com/openDNS.html](http://www.stchman.com/openDNS.html)

They are far better than what your ISP provides.

Hope this helps.

---

### Post by Unconscious on 2007-07-26
I examined my host and domain files, and, as far as I can,  they are ok. 

I switched to opendns, as well. 

Neither of these solutions provided significant improvement. 

Interestingly enough, though. I switched my VMPlayer configuration to bridged networking for my windows VM, and that made a huge improvement in browser performance, within the VM.

Now, browsing in my Windows VM is just as fast as brwosing on a dedicated windows box.
Browsing in the linux desktop, however, is still slow and error-prone. I suspect that there is some interaction between DNS and browsing involving reverse name lookup.

---

### Post by Tecguy2 on 2007-07-26
have you installed your graphics driver
just a suggestion

---

### Post by Unconscious on 2007-12-01
No. I'm using an old compaq with a fairly lo-tech display card.

It doesn't seem likely that it would have anything to do with the graphics driver, since the same browser, on the same machine, running under win 2k in a VM works fine.

---

