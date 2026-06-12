---
title: "Suspend modus not working"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by al-iksir on 2011-02-01
Hi there, 

when I try to put my laptop (Thinkpad T400) into the suspend modus (Fn-F4 or from the menu) it locks the screen instead and the screensaver appears. I am using Ubuntu 11.04. Any ideas what is wrong / how to solve that?

Thank you, 
al-iksir.

---

### Post by [Snc] on 2011-02-01
> **al-iksir said:**
> Hi there, 

when I try to put my laptop (Thinkpad T400) into the suspend modus (Fn-F4 or from the menu) it locks the screen instead and the screensaver appears. I am using Ubuntu 11.04. Any ideas what is wrong / how to solve that?

Thank you, 
al-iksir.

I don't know that thinkpad, but maybe it does not support suspending or your swap partition is too small, to fit all the memory pages inside it.

---

### Post by al-iksir on 2011-02-07
Hey, 

I had no problems with the same laptop and previous versions of Ubuntu, but somehow this function was messed up by one of the more recent updates. Any more ideas where to look for the problem or how to solve it?

---

### Post by ranbo on 2011-02-09
I'm having a similar problem, with a Lenovo T500 thinkpad.  With previous versions of Ubuntu, suspend and hibernate worked fine.  Now they don't work at all.

When I select "suspend" (either by closing the lid or selecting it explicitly from the menu), it just goes back to the blank screen with a password prompt (like when the screen is locked by the screensaver).  Sometimes I see a brief error message, but I can't get that to happen right now.

---

### Post by ivanovnegro on 2011-02-09
First of all dont forget that Ubuntu 11.04 is in Alpha state, so this could be the explanation for some weird behaviors. For problems go to the Natty Testing Discussion.
Second, I know that some HP machines have problems with the suspend mode, mines included. Anyway it could be because the SWAP space on your disk is too small.

---

### Post by OpenSage on 2011-09-21
> **al-iksir said:**
> Hi there, 

when I try to put my laptop (Thinkpad T400) into the suspend modus (Fn-F4 or from the menu) it locks the screen instead and the screensaver appears. I am using Ubuntu 11.04. Any ideas what is wrong / how to solve that?

Thank you, 
al-iksir.





I know this is a really late reply, but I think I have this issue figured out. I have had the same problem running both Ubuntu 10.10 64 bit and Ultimate Edition 9/on Ubuntu 10.10 64 bit. I came across this fix by accident. Before suspending the machine, go to a different console by pressing (CTRL+ALT+F2) all at the same time. You should be in a new console. Log into that console then press (CTRL+ALT+F7) to take you back to your Graphical User Interface and then Suspend you machine. This works for me every time. Hope this helps some people.\\:D/

---

