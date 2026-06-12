---
title: "wine memory leak"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by namluc on 2010-04-12
massive wine memory leak when using ie4linux

i took this pictures only 1 minute ago, but wine server is now using 1 gig of my ram and ie 330 meg. 

what to do?

---

### Post by Sir Jasper on 2010-04-12
Hi,

Is that resource usage normal or unusual? If you end processes or kill Wine Server and Internet Explorer and then restart Internet Explorer (or even any other Wine program) is the usage then as expected?

My regards

---

### Post by namluc on 2010-04-14
Thanks for the reply

The resource usage is highly unusual. I don't use wine for much, the odd game, etc. 

ie6 doesn't always work, as it struggles to detect proxy settings, sometimes I find rebooting helps. When it does, as I mentioned in the previous post, there is a memory with both the wine server and ie6. With my opening post, that leak, after five minutes, led to them using 1.5 gigs of ram, and 2 of my 3 cores.

I find that if i kill ie6, i have to reboot to get it to work again.

thanx

---

### Post by Sir Jasper on 2010-04-14
Hi again,

If you sort by Process Name (into alphabetical order) does Internet Explorer 6 show as one or more Zombies? If it does and if you kill those as well you may not have to reboot.

I have used Ubuntu with Xubuntu Desktop versions 8.10, 9.04 and 9.10. I have used Wine v 1.0.1 and Internet Explorer 6 (installed from Wine-Doors) throughout. I used to have occasional problems with IE6 but that was only in conjunction with one particular program and my combined memory usage for wineserver and IE6 is 21 MB at this moment.

I don´t have a deep understanding so I can only relate my own experience.

My regards

---

