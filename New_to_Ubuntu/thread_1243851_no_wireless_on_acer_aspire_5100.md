---
title: "no wireless on acer aspire 5100"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by yoshiki2 on 2009-08-18
Any ideas how can I active my wireless card?

---

### Post by LewRockwell on 2009-08-18
> **yoshiki2 said:**
> Any ideas how can I active my wireless card?

[http://ubuntuforums.org/showthread.php?t=490800](http://ubuntuforums.org/showthread.php?t=490800)

.

---

### Post by k3lt01 on 2009-08-19
My father has this exact model so hopefully I can be of help. 

Can you tell me what version of Ubuntu are you using?
8.04 you need to do a fair bit of work.
8.10 is a bit easier.
9.04 is all self contained and no work should need to be done at all as it works out of the box (that is straight away).

---

### Post by isee on 2009-08-19
Even with 9.04, I had to plug my laptop into a LAN and download the packages to get my Broadcom Wireless card to work thru Update Manager.

If I remember correctly I got a message telling me to do so when I installed Jaunty Jackalope, and it used something called fwcutter to achieve this after I plugged in.

I had to enable things in Synaptic, can't recall exactly how, but I think I had to enable restricted packages.

Synaptic>Settings>Repositories>UbuntuSoftware -- enable main, universe, restricted, multiverse then Reload

You have to be plugged in though.

Cheers!

---

### Post by yoshiki2 on 2009-10-10
I have 9.04 and 9.10.. no one of them work out of the box.. so i only need to enable restricted? or something else?

---

### Post by philinux on 2009-10-10
> **yoshiki2 said:**
> I have 9.04 and 9.10.. no one of them work out of the box.. so i only need to enable restricted? or something else?

Plug it in wired then update the machine. Post before yours says the same.

---

### Post by sandyd on 2009-10-10
> **isee said:**
> Even with 9.04, I had to plug my laptop into a LAN and download the packages to get my Broadcom Wireless card to work thru Update Manager.

If I remember correctly I got a message telling me to do so when I installed Jaunty Jackalope, and it used something called fwcutter to achieve this after I plugged in.

I had to enable things in Synaptic, can't recall exactly how, but I think I had to enable restricted packages.

Synaptic>Settings>Repositories>UbuntuSoftware -- enable main, universe, restricted, multiverse then Reload

You have to be plugged in though.

Cheers!
```

bcm43xx-[I]fwcutter

```
but his card ain't broadcom
[/I]

---

### Post by k3lt01 on 2009-10-10
> **yoshiki2 said:**
> I have 9.04 and 9.10.. no one of them work out of the box.. so i only need to enable restricted? or something else?It should work out of the box. My fathers laptop does with 9.04, there are a few small difficulties with 9.10 Alpha 6 but 9.04 just works without any work being done at all.

Are you able to try 9.04 on its own? in other words don't have 9.10 on the laptop at all.

---

