---
title: "working with Oprofile on ARM9 hardware in Vmware environment using ubuntu"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by AshishJogeshwar on 2009-12-17
Hi,

I am relatively new to Ubuntu.
I am currently working on ubuntu 9.04 in vmware.
We are developing for ARM9 processor.
I want to use Oprofile as a system profiling tool.

i downloaded and installed Oprofile on my target.
but whenever  i try to start oprofile, i get the following error

[B]root@topas:~ opcontrol --start --no-vmlinux --verbose
mount: mounting nodev on /dev/oprofile failed: Device or resource busy
Kernel support not available, missing opcontrol --init as root ?[/B]


I am not interested in profiling the kernel and hence using the option --no-vmlinux.

Please get back to me if anyone has come across the same or similiar problem.

-Ashish

---

### Post by overdrank on 2009-12-18
Hi and welcome, moved to Absolute Beginner Talk 
Bumped :)

---

