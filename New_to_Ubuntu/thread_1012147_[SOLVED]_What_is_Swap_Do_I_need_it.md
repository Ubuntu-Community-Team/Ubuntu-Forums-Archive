---
title: "[SOLVED] What is Swap? Do I need it?"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by looi76 on 2008-12-15
Hi, what is swap memory? and why is it needed?

---

### Post by Kellemora on 2008-12-15
Hi Loo

Simply put:  Swap is used to store what's needed in memory when the memory is full, so the part that's on hold is stuck into the swap file while the other part is worked on.  Then that part will be stuck into Swap while the part in Swap is loaded back in and worked on.

EG, while the machine is working on page 1, page 2 is held in swap, and vice versa.  The lower your memory, the larger your swap file needs to be.  If you have Tons of Memory, the swap file is rarely used, if at all.

TTUL
Gary

---

### Post by mapes12 on 2008-12-15
Goes back to the steam age days of unix to when RAM was not as plentiful as today. The OS used the swap area as extra memory for intensive applications. You still need to have it because your system will not work properly unless it's there. As a rule of them set the swap partition size to twice your installed RAM.Takes up minimal space. Alternatively,at the partitioning stage of the install select the default "Guided-use entire disk" and the installer will set its size for you.

---

### Post by waspbr on 2008-12-15
sonner or later we all use the swap regardless of your memory size, it is true what the dude above said tho. If you have a large memory, it is unlikely you will use your swap a lot (depending on what you use your computer for). I have had the pleasure of of making computers with 16 GB of Ram rely heavily on their swap files :D.

rule of the thumb is to make your swap files 2x the size of your RAM

---

### Post by oldsoundguy on 2008-12-15
and if you are into heavy photo processing or doing video editing or music composition, make the swap about 4x your memory.  Just makes things easier!

---

### Post by Paqman on 2008-12-15
> **waspbr said:**
> 
rule of the thumb is to make your swap files 2x the size of your RAM

My rule of thumb for desktop systems is swap=RAM if you need to hibernate, otherwise 1GB.

The system monitor applet that you can put on a panel is handy. You can use it to monitor your RAM and swap usage. It's pretty straightforward to either shrink or expand swap, so don't feel like whatever amount you choose is set in stone. There really is no wrong answer for how much you need.

---

### Post by nhasian on 2008-12-15
the SWAP faq is a good read:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

