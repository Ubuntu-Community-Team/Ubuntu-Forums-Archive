---
title: "What would be the limitations to install the 64 bit version?"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by bilbo.san on 2010-05-22
Hi everyone!
I was thinking on installing the 64 bit version... but I was wondering, Would I have the same limitations like in Windows?, I mean, I cant install lots of stuff on Win 64 if the program is 32 bit and there is no way around it. 
If you have the 64 bit, and use Wine for several applications?... please let me know what are the advantages and dis-advantages of having it.

---

### Post by howefield on 2010-05-22
32 bit applications can be used in 64 bit Ubuntu.

There are 64 bit versions of pretty much every application you would want to run, but where there aren't, chances are that you'll can use the 32 bit application.

Wine itself is 32 bit, the 64 bit version doesn't come out till next month, (as far as I know). Don't let that stop you, it runs fine on 64 bit Ubuntu.

---

### Post by jerome1232 on 2010-05-22
I've ran 64 bit for a long time. It's nowhere near the insanity that windows is. There may be a few proprietary apps that are difficult to get working or won't work in 64 bit, but I've never run into one.


The only problem I've ever had with 64 bit ironically was because of Windows lack of support for 64 bit. 

I got a wireless card that works in Linux by using it's Windows Driver and a wrapper script that allows it to work, unfortunately there wasn't a 64 bit windows driver so I ended up having to exchange it for another card that works fine.

---

### Post by warfacegod on 2010-05-22
This is all assuming, of course, that you computer has 64 bit architecture.

---

### Post by bowens44 on 2010-05-22
I've been using 64 bit for a since Karmic and have had absolutely no issues. The few 32 bit only apps that I run work perfectly.

---

### Post by bilbo.san on 2010-05-22
Thanks!!!

I wanted to use Wine to run some Adobe applications like PhotoShop and Dreamweaver (which I use on daily basis) and I guess these are 32 bit, but wanted to have the 64 bit on Ubuntu for Blender 3D.
For me, the fact is that the more I use Ubuntu, more I want to get rid of Windows.

To be honest with you guys, I am not sure how to know if my machine has a 64 bit structure, but that is what I asked when I bought it.

e.

---

### Post by corncob on 2010-05-22
> **bilbo.san said:**
> Thanks!!!

To be honest with you guys, I am not sure how to know if my machine has a 64 bit structure, but that is what I asked when I bought it.

e.

When I tried to install 64-bit Ubuntu in a 32-bit machine, It told me "wrong version" right away.

---

### Post by -humanaut- on 2010-05-22
I've been using the 64-bit Version since the alphas works great for me I don't see any limitations.

---

### Post by warfacegod on 2010-05-22
Type:

```
sudo lshw
```

In a Terminal and then scroll to the top. Under cpu look for width. It will say either 32 or 64.

---

