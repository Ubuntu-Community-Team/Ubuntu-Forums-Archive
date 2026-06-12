---
title: "can i get a wider range of screen resolutions?"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by cosmicappuccino on 2009-04-18
Hi,

I only have 3 screen resolutions available in the drop-down menu, at the moment. Is it possible to get more?

Some googling has revealed suggestions to use:

```
sudo dpkg-reconfigure xserver-xorg
```

But that only seems to take me through keyboard settings, with no mention of the display. Am I missing something?

Any instructions would be much appreciated, thanks a lot...

---

### Post by halitech on 2009-04-18
what video card do you have?

---

### Post by cosmicappuccino on 2009-04-18
:S It's an nvidia one but I don't know exactly. Do I have to know? - if so, how can I find out?

---

### Post by halitech on 2009-04-18
it would help to know. open a terminal and post the output of```
lshw -C video
```

you may be able to enable the restricted drivers as well - System - Admin - Restricted drivers (if its there)

---

### Post by davec64 on 2009-04-18
Just a thought, be careful and research your monitors capabilities as well!! :)

You don't want to send your monitor into early retirement!

---

### Post by NESFreak on 2009-04-18
> **davec64 said:**
> Just a thought, be careful and research your monitors capabilities as well!! :)

You don't want to send your monitor into early retirement!

nowadays monitors are protected and show an out of range error.

In ye olde days you could indeed blow them up. So unless yours is older than say 15 years i wouldn't worry to much.

---

### Post by davec64 on 2009-04-18
> **NESFreak said:**
> nowadays monitors are protected and show an out of range error.

In ye olde days you could indeed blow them up. So unless yours is older than say 15 years i wouldn't worry to much.

Point taken!
I'm an old git, wishing it was still the 80's :)

---

### Post by nandemonai on 2009-04-18
> **cosmicappuccino said:**
> Hi,

I only have 3 screen resolutions available in the drop-down menu, at the moment. Is it possible to get more?

Some googling has revealed suggestions to use:

```
sudo dpkg-reconfigure xserver-xorg
```

But that only seems to take me through keyboard settings, with no mention of the display. Am I missing something?

Any instructions would be much appreciated, thanks a lot...

Are the restricted drivers for NVIDIA installed? That's the only way I've been able to get good resolutions on my systems with NV cards.

---

### Post by cosmicappuccino on 2009-04-19
Thank you all for your replies!

I will try your suggestions out when I am on that computer again (it's currently in use by someone else)...

(:

---

