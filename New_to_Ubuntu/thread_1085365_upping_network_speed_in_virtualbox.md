---
title: "upping network speed in virtualbox"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by ntrgc89 on 2009-03-03
Hi all,

I recently installed a Windows XP guest OS (using VirtualBox) in ubuntu 8.10 so I could watch netflix movies right from linux, but I'm having a bit of a problem....

The movies come out very grainy. I can be sure it's not a graphics issue (I'm allocating 64 MB of VRAM to the guest OS), it's definitely a network issue. Is Virtualbox splitting the connection speed between the host and guest OS? And in any case, is there a way to up the connection speed on the guest OS?

Thanks in advance!

---

### Post by oldsoundguy on 2009-03-03
not enough allocated memory for streaming. (no matter the OS!!)

---

### Post by ntrgc89 on 2009-03-03
Are you sure about that? I have 1 gig allocated to the OS. How much is good for streaming and if WinXP is not allocating enough to it, how can I tell it to allocate more?

In any case I'm still of the opinion that it's a network speed issue, having seen no technical evidence to the contrary.

---

### Post by ntrgc89 on 2009-03-03
Anybody have any ideas/knowledge about upping network speed??

---

### Post by ntrgc89 on 2009-03-03
anyone?

---

### Post by ddixonr on 2009-03-03
Same issue here. No luck finding any answers. My issue was mostly upload speed, not download. Some people say to try changing 'Adapter Type' and 'Attached to' settings in vbox. "Attached to: Host Interface" supposedly works for some people, but not for me.

---

### Post by ntrgc89 on 2009-03-03
Meh, doesn't really seem to have had much effect. I did "Attached to:Host interface" and played around with the adapters, but the quality looks pretty much the same (I'm looking at the pixelation in the opening credits so I have some fairly objective measure of it). I wonder if you can tell virtualbox to just take the entire connection from the host OS and give it to the guest one.

---

### Post by ddixonr on 2009-03-03
I definitely believe that it didn't work, but could you test using one of the many bandwidth test sites instead of watching netflix movies?

---

### Post by ntrgc89 on 2009-03-03
lol, good point.

I tried using the one at [www.speakeasy.net/speedtest](www.speakeasy.net/speedtest) (first results for google:bandwidth test), and it was fluctuating wildly (from 600-1200 kbps for download, not so much on upload), It is certainly possible that my internet connection is to blame, but I didn't suspect that as the first culprit since I've had much better quality on the movies before. Oh well, I guess I'll just wait till i get better internet next year when i move back to campus :) Thanks for your help!

---

