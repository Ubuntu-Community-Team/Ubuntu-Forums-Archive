---
title: "Google doesn't work, can't log into forums?"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by bobpur on 2009-07-01
My Toshiba Tecra S2 laptop with Ubuntu v9.04 will type into the Google search window (both of them) on the Firefox startup page. When you hit enter or click on search nothing happens. Also, when I found my way to the Ubuntu forums, I entered my log in info and clicked on log in and my pass code disappeared and nothing. Same thing using enter instead of clicking. 

I've tried rebooting with the same results. The windows side works fine so I don't think it's my mouse.

Has anyone else experienced this that can clear it up.

Thanks

---

### Post by nhasian on 2009-07-01
question: does it work if you boot off of a liveCD?

if so it may just be your firefox configuration files.  you can try closing firefox then typing in a terminal:

```
mv ~/.mozilla ~/.mozilla_bak
```

then relaunch firefox.  this will start firefox from scratch.

---

### Post by bobpur on 2009-07-02
I didn't get to try your fix. 

I had some spare time and downloaded the v9.04 ISO and re-installed the OS. The version that was on this laptop was a much updated release candidate. 

It works better now than it did before. I think some bugs were still present in the release candidate I was using.

Thanks for the reply.

---

