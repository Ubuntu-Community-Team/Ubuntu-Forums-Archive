---
title: "No Usplash Screen in Ubuntu 10.04!"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by fslezak on 2010-06-16
Hello.

I have an HP laptop, (ZE4900) which does not show the Ubuntu boot screen (unless there is a filesystem check.).

How can I get my boot screen installed?

P.S. I had to use this command to get X working a while ago...

```
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf

```But my Usplash didn't work, even before I ran the above command.

---

### Post by migs73 on 2010-06-16
See post 3 on this thread.

[http://ubuntuforums.org/showthread.php?p=9451760#post9451760](http://ubuntuforums.org/showthread.php?p=9451760#post9451760)

My problem was different, but if you have the option to select a splash screen, just type in the number of the one you want.

---

### Post by philinux on 2010-06-16
> **fslezak said:**
> Hello.

I have an HP laptop, (ZE4900) which does not show the Ubuntu boot screen (unless there is a filesystem check.).

How can I get my boot screen installed?

P.S. I had to use this command to get X working a while ago...

```
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf

```But my Usplash didn't work, even before I ran the above command.

10.04 doesn't use usplash it uses plymouth.

See the General Help forum Sticky.

---

### Post by fslezak on 2010-06-17
Still. No PLYMOUTH at startup. VERRRRRY ANNOYING!

---

