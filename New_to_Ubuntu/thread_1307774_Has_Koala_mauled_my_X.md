---
title: "Has Koala mauled my X"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by nnjond on 2009-10-31
Hi,

I'm coming to you Jaunty live, because after I installed Koala ok, I messed around in synaptic trying to fix the scrn res, and I seem to have deleted or conflicted the Nvidia pkges. Now when i try to boot, i just get a bit of flickering text after the grub thingy. Can I fix this from where i am or do i need to re-install?

Thanks.

---

### Post by ibuclaw on 2009-10-31
Boot into recovery mode, select "Root Shell".

then (type in)
```
cd /etc/X11
```
and
```
mv xorg.conf xorg.conf.old
```
then
```
reboot
```
And see if the problem still occurs.

Regards
Iain

---

### Post by nnjond on 2009-10-31
Thanks for your help.

I don't think i can get a recovery mode at strtup, but live ctrl+ alt +f6 gets me to:

ubuntu@ubuntu /etc/X11$

then:

mv: target 'old' is not a Directory

wait, made an E

nope, 'old" is not a Dir

---

