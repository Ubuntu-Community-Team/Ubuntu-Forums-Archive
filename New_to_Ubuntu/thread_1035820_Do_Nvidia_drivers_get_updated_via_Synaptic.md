---
title: "Do Nvidia drivers get updated via Synaptic?"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by RedMartin on 2009-01-10
I'm using Ubuntu 8.04 with an Nvidia GeForce 8600M GS gpu.

I've done the propriety drivers install thing but I'm still on driver 169.xx

I've picked up on the news that version 180.xx is out and subsequent Googling reveals that there have been other versions too.

Why am I not getting upgraded? Is it always done manually or should the updated driver be getting delivered via Synaptic?

Thank you.

---

### Post by wizard10000 on 2009-01-10
I think you'll find that Ubuntu 8.04 is a LTS release - they provide long term support and what gets released is a little bit removed from the bleeding edge.  I'm running 8.10 and 177.xx drivers are available in the repos.

Hope this helps -

---

### Post by Therion on 2009-01-10
New versions of apps and drivers and such get added to the repo's very, very slowly if at all.  Your best bet if you want the 180.xx nVidia drivers is download and install them from source.

What I did to install them -- and I most certainly DO NOT put this out as a recommendation -- was add and enable the Intrepid backport(?) repo, snagged and installed the 180.xx driver, ***dis***abled the Intrepid backport repo and got on with life.

Crude, but effective.

---

### Post by RedMartin on 2009-01-10
> **Therion said:**
> What I did to install them -- and I most certainly DO NOT put this out as a recommendation -- was add and enable the Intrepid backport(?) repo, snagged and installed the 180.xx driver, ***dis***abled the Intrepid backport repo and got on with life.

Crude, but effective.

I like your style.

Would I get more regular updates with Envy NG? I ask as I have that installed too but still the same drivers.

---

### Post by Therion on 2009-01-10
> **RedMartin said:**
> I like your style.
Laugh...  Well, I just HATE installing from source so I've gotten clever about working around it.

> **RedMartin said:**
> Would I get more regular updates with Envy NG? I ask as I have that installed too but still the same drivers.
Envy is a pretty nifty little app, but the only problem you face with it is that you will have to reinstall your video driver each time you get a kernel header update.  Not saying that's necessarily a BAD thing, but if you're not prepared for that little eventuality, it can be a bit of a shock when you reboot after some routine updates and... GOOD MORNING! Your video driver is borked.

I've done some reading and it appears that the 180.xx driver and all its dependencies are in the Intrepid repos (not only backported).  A clever use of Google might lead you to those repos or show you how to use, say for instance, **apt-get install** to download and install those drivers without having to worry about post-kernel-header update borkage.

---

### Post by RedMartin on 2009-01-10
I'm off to Google.

Thank you.

---

