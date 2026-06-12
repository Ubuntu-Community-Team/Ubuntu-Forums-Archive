---
title: "Please recommend a pci card??"
date: 2011-03-17
forum: New to Ubuntu
---

### Post by migrate from windows on 2011-03-17
Hi Im using Ubuntu 10.10 in my old pc and happy with it. I cannot run compiz bcoz my pci card is blacklisted. Can anyone suggest the best PCI video card for my old PC which can handle compiz ( pls do not suggest AGP or PCIe cards my mother board has only PCI slot)

---

### Post by MartyBuntu on 2011-03-17
GeForce 6200 PCI?

It should get the job done.

---

### Post by _0R10N on 2011-03-17
Anyone but ATI. Nvidia, if possible.

---

### Post by Frogs Hair on 2011-03-17
Include pci graphics card in your search terms you will find many . I prefer Nvidia

---

### Post by sleepingdragon on 2011-03-18
I'm running on an nVidia 6200 PCI, no problems here.

If I recall correctly, the nVidia 5200FX does a similar job to the 6200. Tried one about 6 months ago, certainly seemed to work fine back then.

---

### Post by migrate from windows on 2011-03-18
Thanx guys more suggestions welcome.

---

### Post by coffee412 on 2011-03-18
> **migrate from windows said:**
> Thanx guys more suggestions welcome.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814187034](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187034)

I crammed one of these in a build for a customer running Ubuntu and it was remarkably fast! Of course, In my surfing box I run a 8400gs that is fair. Gets the job done.

I have a 9500gt that was given to me that the fan seized. I got a replacement and just havent worked on it yet. 

I think its a great card to use and not expensive really. The link above provides the fanless for longlife.

my .02c worth there.

---

### Post by MartyBuntu on 2011-03-18
> **coffee412 said:**
> [http://www.newegg.com/Product/Product.aspx?Item=N82E16814187034](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187034)

I crammed one of these in a build for a customer running Ubuntu and it was remarkably fast! Of course, In my surfing box I run a 8400gs that is fair. Gets the job done.

I have a 9500gt that was given to me that the fan seized. I got a replacement and just havent worked on it yet. 

I think its a great card to use and not expensive really. The link above provides the fanless for longlife.

my .02c worth there.


Except, that is a PCI-**E** card, not PCI.

---

### Post by coffee412 on 2011-03-18
> **MartyBuntu said:**
> Except, that is a PCI-**E** card, not PCI.

Sorry about that. Didnt quite catch that. Its been along day.

---

### Post by qyot27 on 2011-03-18
Another vote for the GeForce 6200 here.

Be aware that you may still have problems with Compiz due to problems with integrated graphics not being able to be disabled on the motherboard.  Intel boards/graphics have this issue sometimes, especially if the computer is old; I encountered it because my setup is from 2001 and the mobo manufacturer didn't include an option to disable the i810e graphics.

Previous versions of Ubuntu didn't mind this and could enable Compiz anyway, but something changed in 10.04 and/or 10.10 that disallows it based on some of the configuration rules or modes changing.

If that happens, then using the xorg-edgers PPA to update from can probably solve it.  It did here.

---

### Post by coolbrook on 2011-03-18
There's a GeForce 9500 GT with PCI interface as well.  The vendor is Jaton. (32 processing cores FWIW.)

---

### Post by migrate from windows on 2011-03-20
Thank you, nice to know that I have so many options. Still I will keep the thread alive for more .

---

