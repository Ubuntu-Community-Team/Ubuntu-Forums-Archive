---
title: "Root running programs"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by spillage2 on 2010-12-05
my comp has been running slowly so i ran $top and root is running xorg whith high %cpu.

should this be happening and if not how do i put things right.

cheers,

spill.

---

### Post by matt_symes on 2010-12-05
Hi

> my comp has been running slowly so i ran $top and root is running xorg whith high %cpu

What are the specs of your computer and video card?
What desktop effects are you using (Compiz etc)?

What version is *buntu are you using?
Is this a recent problem or has it always happened?

Did it start happening after a software update?

How high is high CPU?

Kind regards

---

### Post by mcduck on 2010-12-05
> **spillage2 said:**
> my comp has been running slowly so i ran $top and root is running xorg whith high %cpu.

should this be happening and if not how do i put things right.

cheers,

spill.

All of the system itself is ran by root (or in case some other system account), it's absolutely normal. (actually you don't even have the permissions to run xorg as yourself).

If xorg is using lot of CPU it could be related to your graphics card drivers. But you'll have to tell a bit more about your hardware before anyone can help with that.

---

### Post by spillage2 on 2010-12-05
ok thanks for the replies..glad root is supposed to be running xorg.

im running a GeForce 8600 GT
i have a amd 2.8Ghz quad core 
running 10.04 bunt
running compiz

this has only just started doing this. every thing just freezes up. so i can run a gdm restart and a few seconds in it starts again.

just thought 65% cpu usage for xorg was high?

its working not to bad now but its temperamental. 

cheers,

spill.

---

### Post by matt_symes on 2010-12-06
Hi

That is rather high CPU for the specs of your PC.

What driver are you using for the card?  At the terminal type

lspci -k | grep -C2 VGA

this should tell you.

Kind regards

---

