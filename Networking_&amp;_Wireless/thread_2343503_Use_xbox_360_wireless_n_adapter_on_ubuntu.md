---
title: "Use xbox 360 wireless n adapter on ubuntu?"
date: 2016-11-16
forum: Networking &amp; Wireless
---

### Post by frank72 on 2016-11-16
Hello all,
I'm trying to figure out how to use an xbox 360 wireless adapter, N,usb, on my ubuntu pc.
Ive found references to it working on windows machines and also reference to using windows drivers on ubuntu to activate pci wireless adapters with no released ubuntu drivers using Ndiswrapper. i assume usb adapters may be different.

2 questions...

Has anyone done this?

Is it safe to experiment with things like Ndiswrapper or could it ruin my wired connection?

Please help guys. Ive found a few reference to people who tried unsuccessfully and a solution would be real cool.
Please let me know if u need more info and

Thanx in advance...

---

### Post by DuckHook on 2016-11-17
Without further specs on your adapter chipset, it is impossible to advise. ndiswrapper will only work with Win XP drivers. Newer or non-XP drivers won't work. Since XP is long past end of life, you can imagine how dated and obsolete any instructions found on the net actually are.

Experimenting with kludges like ndiswrapper are always fraught with potential pitfalls. After all, the nature of ndiswrapper is trying to shoehorn a foreign piece of code into an OS it was not designed for. The wonder is not what goes wrong, but that it can be done at all. Working with ndiswrapper is always prefaced with the implicit warning that you proceed at your own risk.

I do not own an XBox, nor its USB WiFi modem, so can be of no technical help to you. However, from a general standpoint, I would advise that you only try experimenting with this foreign adapter if this is a secondary machine that you don't care about trashing or having to reinstall. If it is a production machine, I would strongly advise using only proven WiFI adapters natively supported in the Linux kernel. Such adapters are very cheap these days and it isn't worth the headache trying to wrestle with a half-man-half-horse.

---

### Post by frank72 on 2016-11-19
Thanx for the time you took to reply. sounds like sound advice. 

i set these challenges for myself and hate to take no for an answer, how else learn,.
but im taking your advice cause everything's running great and i don't want to screw it up  :)

---

### Post by DuckHook on 2016-11-19
> **frank72 said:**
> i set these challenges for myself and hate to take no for an answer, how else learn,.Actually, yours is a wonderful attitude. When I started out with Linux, I learned more from having to fix my own catastrophes than I did in any other way. But I made sure to break only boxes that weren't critical to my workflow. I also learned quickly that backups are my very best friend. They saved me on occasions where I didn't follow my own advice and broke my production box.> but im taking your advice cause everything's running great and i don't want to screw it up  :)I'm sure that, as you get further into Linux, you will get a gut feel for when to take chances and when not to (and what sort of chances to take and what to avoid).

Good luck and Happy Ubuntuing!

---

### Post by jeremy31 on 2016-11-19
Post results for ```
lsusb
```
With this device plugged in

---

### Post by frank72 on 2016-11-23
Thank you for your interest,

lsusb gives me this output..

Bus 001 Device 006: ID 045e:0292 Microsoft Corp. Xbox360 Wireless Networking Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I hope this helps and thank you again for your replys  id love to see this work, having trouble finding the drivers but i think there out ther. Looking now 

EDIT:ADDED: 
Think i have the drivers. Found references to needing windows .sys and.inf. Feel like i'm getting close....

---

### Post by frank72 on 2016-11-23
Ndiswrapper atheros drivers

win7-9.2.0.19-whql-full.zip   install but says device not connected

and 

win7-2.0.0.49-whql.zip

Same with this 1

ndisgtk is a nice gui for Ndiswrapper

wonder if its because its not a pci adapter

---

### Post by frank72 on 2016-11-23
A word of warning to anyone following this thread.

As warned I am now getting a system error at startup...

---

### Post by frank2222 on 2016-12-16
Error went away after removing wrapper and restarting a few times. Still curious if someone with a test machine can pull this off.
Has anyone done this on windows?

---

