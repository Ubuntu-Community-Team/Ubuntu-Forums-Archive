---
title: "Graphics Card"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-04-27
Earlier I upgraded my computer to Natty beta and realized my computer couldn't handle the graphics. The day after the launch of Natty is my birthday, and my parents told me I will be getting a good graphics card for by birthday. My computer has PCI slots. I need to know:

1. Graphics card requirements for Natty and Unity to run smoothly.
2. Graphics card recommendations.

I have a Dell Dimension 8110

---

### Post by Frogs Hair on 2011-04-27
1. I don't know yet , maybe the beta users have better idea what works best.
2. I prefer Nvidia , but without knowing what your parents are going to spend it's hard to make a suggestion . I would make sure it has at least 1 gb of memory and if you play games pay attention to the graphics card requirements. Be sure your power supply is big enough to support the card !

---

### Post by cek on 2011-04-27
The requirements aren't too high.  I've been running gnome-shell with out any issues on an integrated nVidia 6150.  Any modern nVidia or ATI card should suffice to run Unity pretty well.

That said, while ATI cards generally have better performance for the money (according to most reviews I've read), I'd suggest going with an nVidia card for the much better linux support.

However, from the looks of the dell site, your options will be severly limited with a Dimension 8100.  Stated there it only has a 250W power supply and AGP 4X/PCI ports for graphics cards.  Not much to choose from in that category any more I'm afraid.

---

### Post by K_45 on 2011-04-27
With DirectX10 too:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814125296&cm_re=nvidia_PCI-_-14-125-296-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16814125296&cm_re=nvidia_PCI-_-14-125-296-_-Product)

$30, $20 if you use the rebate.

---

### Post by doppel.ganger on 2011-04-27
What is DirectX10?

---

### Post by K_45 on 2011-04-27
> **doppel.ganger said:**
> What is DirectX10?

Doesn't really matter. Its the API (application programming interface) for some games. Its an extra feature that is good to have at that price. The only other choice worth considering is the old 8400GS, but I'd go for this 210.

---

### Post by Jerry N on 2011-04-27
Some of these replies miss the point - OP says he has AGP 4x/PCI slots, NOT PCI Express.  

Newegg has a bunch of AGP boards but I don't what ones might be best.  Let's don't talk him into PCIe board that he can't use.

Jerry

---

### Post by papibe on 2011-04-27
For what I've read [here]("http://support.dell.com/support/edocs/systems/dsleest/techovu.htm"), you do not have a PCIe, but regular PCI slots. If that's true, you are left with cards that are a bit out of date.

As K_45, I would also think the Nvidia Geforce 8400 GS, would be your best bet.

BTW, you could have a PCIe, as sometimes the documentation is not that accurate. If so, that opens the door for newer cards.

I hope it helps.

---

### Post by doppel.ganger on 2011-04-27
How do I tell if I have PCIe or PCI?

---

### Post by K_45 on 2011-04-27
Run:

```
sudo lshw -html > specs.html && firefox specs.html
```

and have a look at what's inside.

---

### Post by Jerry N on 2011-04-28
> **doppel.ganger said:**
> How do I tell if I have PCIe or PCI?
See: 
[http://support.dell.com/support/edocs/systems/dsleest](http://support.dell.com/support/edocs/systems/dsleest)

You have PCI and AGP slots.  You DO NOT have PCIe.  AGP cards would be the most suitable.  

Jerry

---

### Post by K_45 on 2011-04-28
That is for the 8100, not 8110, anyway this is a good choice:  [http://www.newegg.com/Product/Product.aspx?Item=N82E16814161308](http://www.newegg.com/Product/Product.aspx?Item=N82E16814161308)  AGP, but supports HDMI and HDCP.

---

