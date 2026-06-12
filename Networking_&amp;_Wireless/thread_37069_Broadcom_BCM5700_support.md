---
title: "Broadcom BCM5700 support?"
date: 2005-05-25
forum: Networking &amp; Wireless
---

### Post by ajft on 2005-05-25
I've just "upgraded" what was a working Debian workstation to Ubuntu and am
very surprised to find that there's no support for the Broadcom ethernet BCM5788
that I _was_ using for several months. I've been trying to work my way through
the circuitous Ubuntu way of creating a module that I thought would be in the base
system.

From another thread I found that I had to download the source package bcm5700-source and compile and install it.

> Type "sudo m-a" and select "PREPARE" (creates a link in /usr/src to the headers)
> then exit and:

> $ sudo m-a build bcm5700
> $ sudo m-a install bcm5700

These work, although after the first step i get told to run
"m-a install bcm5700-source"

This ends up with a module in /lib/modules/2.6.11-1-686-smp/bcm/bcm5700.ko

However, attempting to load it results in:
fafnir:/lib/modules# modprobe bcm5700
FATAL: Error inserting bcm5700 (/lib/modules/2.6.11-1-686-smp/bcm/bcm5700.ko): Invalid module format

fafnir:/lib/modules# uname -r
2.6.11-1-686-smp

From 'dmesg':
bcm5700: disagrees about version of symbol struct_module

Can anyone help?

---

### Post by mrbright on 2005-06-04
I think I came across the same problem too, or atleast a similar one

---

