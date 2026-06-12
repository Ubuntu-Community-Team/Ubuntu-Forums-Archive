---
title: "Boot up splash screen changed and went lo-res on me..."
date: 2010-10-14
forum: New to Ubuntu
---

### Post by k-sider on 2010-10-14
I'm extremely new here and have limited time due to rigorous work schedule.. so since its late I'm just going to ask this question rather than start reading FAQ's and such right off the rip...

If someone knows the deal with this I'd be extremely grateful.... basically I installed RC version of 10.10 last week and then the official 10.10 a few days ago.  The issue is that the standard Ubuntu splash screen that comes up when loading the OS suddenly changed from a nice looking ubuntu splash screen to a pixelated plain text sort of screen that says Ubuntu 10.10 (iirc)  I'm wondering if something happened to my o.s. that would cause this... it doesn't seem right.  Any thoughts?  

I don't know where to start looking at the moment since I haven't had time the past couple of days to start educating myself on the basics of troubleshooting Ubuntu software.  For what its worth I'm running a Geforce 210 vga card with restricted drivers and a E3300 cpu/Intel P45 chipset motherboard.  Thanks.

---

### Post by amjjawad on 2010-10-14
> **k-sider said:**
> I'm extremely new here and have limited time due to rigorous work schedule.. so since its late I'm just going to ask this question rather than start reading FAQ's and such right off the rip...

If someone knows the deal with this I'd be extremely grateful.... basically I installed RC version of 10.10 last week and then the official 10.10 a few days ago.  The issue is that the standard Ubuntu splash screen that comes up when loading the OS suddenly changed from a nice looking ubuntu splash screen to a pixelated plain text sort of screen that says Ubuntu 10.10 (iirc)  I'm wondering if something happened to my o.s. that would cause this... it doesn't seem right.  Any thoughts?  

I don't know where to start looking at the moment since I haven't had time the past couple of days to start educating myself on the basics of troubleshooting Ubuntu software.  For what its worth I'm running a Geforce 210 vga card with restricted drivers and a E3300 cpu/Intel P45 chipset motherboard.  Thanks.

Welcome to Ubuntu :)

Is it only the Splash Screen? or you have the same problem with your desktop too?

---

### Post by AndyM3 on 2010-10-14
That would be either a KMS problem or the default plymouth theme.

I don't really know if this would work, but try running "sudo update-alternatives --config default.plymouth" and see if there are more than one alternatives. If there are, pick the one labelled "/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth".

EDIT: Whoops, sorry, you specified your card. :D

---

### Post by garvinrick4 on 2010-10-14
Need to answer post #2 first it will make this a lot simpler.

---

### Post by k-sider on 2010-10-14
> **garvinrick4 said:**
> Need to answer post #2 first it will make this a lot simpler.

It's just the boot splash screen that changed... the desktop and gui still looks perfrect.

Thank you everyone for the replies.

---

### Post by El Zoido on 2010-10-14
This is a common problem when activating the restricted Nvidia drivers.
There was a thread with the solution in general very recently.
Just have a look there, I don't have the link myself!

---

