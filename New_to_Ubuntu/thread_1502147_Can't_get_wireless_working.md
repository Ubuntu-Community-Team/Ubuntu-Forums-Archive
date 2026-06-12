---
title: "Can't get wireless working"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by xtheunknown0 on 2010-06-05
Hi,

I can use Firefox with a CAT5 but not with wireless. I've created a new wireless network and there's a temporary popup saying connection is established (of course, the CAT5 isn't plugged in in this instance) but with the wireless connection I cannot load any websites in Firefox.

TIA,
xtheunknown0

---

### Post by wojox on 2010-06-05
Can you ping Google from the terminal?

```
ping www.google.com  
```

---

### Post by 3rdalbum on 2010-06-05
> **xtheunknown0 said:**
> Hi,

I can use Firefox with a CAT5 but not with wireless. I've created a new wireless network

No, you don't "create a new wireless network", you need to connect to an **existing** network. The network's SSID should appear in the Network Manager, just left-click that and you'll be prompted for your network's encryption key.

"Create a new wireless network" is where you want to use your computer as a wireless router that other computers will use as their access point.

---

### Post by xtheunknown0 on 2010-06-05
> **wojox said:**
> Can you ping Google from the terminal?

I believe so: [http://sites.google.com/site/xtheunknown0/wireless](http://sites.google.com/site/xtheunknown0/wireless)

---

### Post by xtheunknown0 on 2010-06-05
> **3rdalbum said:**
> No, you don't "create a new wireless network", you need to connect to an **existing** network. The network's SSID should appear in the Network Manager, just left-click that and you'll be prompted for your network's encryption key.<snip>

Alright, kudos for correcting my use of networking terms. :)

---

### Post by mapes12 on 2010-06-05
Is your machine connecting to your router and obtaining a valid IP address? Right click your network icon then select "Connection Information". I've attached a screen shot of mine so you can see what I mean.

Mark

---

### Post by xtheunknown0 on 2010-06-05
> **mapes12 said:**
> Is your machine connecting to your router and obtaining a valid IP address? Right click your network icon then select "Connection Information"<snip>

I've attached a screenshot to the same webpage provided in a previous post of mine.

---

### Post by xtheunknown0 on 2010-06-05
> **3rdalbum said:**
> No, you don't "create a new wireless network", you need to connect to an **existing** network. The network's SSID should appear in the Network Manager, just left-click that and you'll be prompted for your network's encryption key.

"Create a new wireless network" is where you want to use your computer as a wireless router that other computers will use as their access point.

Well, I've been really fustrated so I've re-installed Ubuntu.

Now, Network Manager can't detect any wireless networks. (It used to before I re-installed :|) Can someone please help me with setting up wireless from the beginning? I believe that Ubuntu has the right drivers for it and that it should be able to talk with my router, it's just not doing that at the moment, since I tried going through the troubleshooting guide that one finds when the Google 'wireless ubuntu'.

---

### Post by xtheunknown0 on 2010-06-06
Bump

---

### Post by Hygaphunkik on 2010-06-06
What PC is it?

Have you tried searching for Hardware Drivers in 'system/administration'?

---

### Post by xtheunknown0 on 2010-06-06
> **Hygaphunkik said:**
> What PC is it?

Have you tried searching for Hardware Drivers in 'system/administration'?

I'm using a Lenovo Thinkpad Edge 13" laptop.
Upon clicking on Hardware Drivers, I allowed Ubuntu to install something related to graphics.
At the time of this post, I'm letting Update Manager get all software updates.

---

### Post by Hygaphunkik on 2010-06-06
> **xtheunknown0 said:**
> I'm using a Lenovo Thinkpad Edge 13" laptop.
Upon clicking on Hardware Drivers, I allowed Ubuntu to install something related to graphics.
At the time of this post, I'm letting Update Manager get all software updates.

Probably a good move. I am no expert but had some wireless problems on a dell pc.

---

### Post by xtheunknown0 on 2010-06-06
[QUOTE=xtheunknown0;9417265]...I've re-installed Ubuntu.

...Can someone please help me with setting up wireless from the beginning?...QUOTE]

After System->Administration->Hardware Drivers (which isn't relevant to this problem because it got my laptop the ATI/AMD proprietary FGLRX graphics driver) and using my ethernet cable to update *all* software packages, I was able to detect my existing network. Upon clicking on the existing network, I was prompted for a password and this time it worked (after > 10 attempts at providing the right password but not actually connecting, kept getting the arcs moving up and down).

Thanks guys, I love this forum.

---

