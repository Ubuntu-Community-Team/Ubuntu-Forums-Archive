---
title: "Ubunto won't boot"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by richie42 on 2009-08-11
Yeah so it won't boot, like it said and it keeps giving me this

Starting up ...
mp bios bug 8254 timer not connected to IO APIC

Loading please wait...
19 + 0 records in
19 + 0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/627ed602-8827-4c23-a03d-c27636eb09ec) = d ev(8.5_
knit: trying to resume from /dev/disk/by-uuid/627ed602-8827-4c23-a03d-c27636eb09ec
knit: No resume image, doing normal boot ...
mount: mounting dev/disk/by-uuid/627ed602-8827-4c23-a03d-c27636eb09ec

Other stuff too but I gotta write it all down and all.

Can I get some help please.?

---

### Post by LewRockwell on 2009-08-11
> **richie42 said:**
> Yeah so it won't boot, like it said and it keeps giving me this

Starting up ...
mp bios bug 8254 timer not connected to IO APIC

Loading please wait...
19 + 0 records in
19 + 0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/627ed602-8827-4c23-a03d-c27636eb09ec) = d ev(8.5_
knit: trying to resume from /dev/disk/by-uuid/627ed602-8827-4c23-a03d-c27636eb09ec
knit: No resume image, doing normal boot ...
mount: mounting dev/disk/by-uuid/627ed602-8827-4c23-a03d-c27636eb09ec

Other stuff too but I gotta write it all down and all.

Can I get some help please.?

Let's establish a baseline and work from there

We'll need machine and operating system(s) information including versions

We'll also need to know a little history regarding your system before this difficulty

.

---

### Post by richie42 on 2009-08-11
OK, Compaq Presario. Uhhhh it runs Ibex, just Ibex.

Uhhh what do you mean history?

---

### Post by jrothwell97 on 2009-08-11
When we talk about 'history', we mean what happened recently with the system. For example, did you install any updates or any new pieces of software before this problem? Did you change your hardware?

---

### Post by Tek-E on 2009-08-11
If you just installed it for the first time and have had issues.
I would recommend that you just try and re-install ubuntu see if that clears up. An error might have occurred during the installation process.

---

### Post by richie42 on 2009-08-11
> **jrothwell97 said:**
> When we talk about 'history', we mean what happened recently with the system. For example, did you install any updates or any new pieces of software before this problem? Did you change your hardware?

I mean I had it installed like months ago and it just acted like this. Would reinstalling it work or just make it worse?

---

### Post by jrothwell97 on 2009-08-11
> **richie42 said:**
> I mean I had it installed like months ago and it just acted like this. Would reinstalling it work or just make it worse?
I mean, did you install any new software or did you update Ubuntu recently? Because that _may_ have caused the problem.

---

### Post by wojox on 2009-08-11
At the grub boot screen, use your arrow keys to highlight "kernel /boot/linuz-2.6.15-25-386 root=/dev/sda3 ro quiet splash" (your exact paths and numbers might be a little dfferent). Then type 'e' to edit the boot options; you will be taken to another screen. Append 'noapic' to the end of the boot options, and hit enter. Then just type 'b' to boot.

---

