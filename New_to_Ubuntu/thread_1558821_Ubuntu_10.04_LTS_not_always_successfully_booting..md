---
title: "Ubuntu 10.04 LTS not always successfully booting."
date: 2010-08-22
forum: New to Ubuntu
---

### Post by kieran_1979 on 2010-08-22
Hi.

I've just recently installed Ubuntu 10.04 and am having trouble booting on occasion.

What happens usually is that the computer will power up, the Bios splash screen will display then it will drop to a screen with a flashing cursor. The HD will crunch for a few seconds then the whole thing just sits there. Mashing at the keyboard wildly produces no results.

Now if I were to do a hard shutdown and power it up again it does EVENTUALLY, boot successfully. But 9 times out of 10, it just dies. Right now I'm just suspending it instead of shutting down. I haven't even tried to hibernate yet, I'm too scared.

I must say though  that when it does boot, its one of the fastest boots I've ever seen! WinME was the only other GUI OS I've used that came close.

Now I'm not terribly Linux literate so if anyone has any idea what the problem might be, and can point me in the right direction I'd be very appreciative.

Here are the specs for the computer:

Acer Aspire One netbook, Intel atom 1.6 ghz, 1 gig ram and some sort of onboard Intel 8 mg graphics card. It's about 8 months old. I'm not using the netbook remix because I don't have a USB key.

Thanks, 
Kieran.

---

### Post by Rubi1200 on 2010-08-22
First try this:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

For Intel chipsets you need to use the i915.modeset=1 parameter.

If that works to boot into Ubuntu, we can talk about more permanent solutions.

---

