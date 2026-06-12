---
title: "Linux ON Windows"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-12-01
I've heard of this before, Linux inside Windows in a program like wubi, w/out having to reformat and repartition. and without a virtual. how does this work? how is it possible? does it still keep you safe from windows viruses using the browser in the linux os? or are you more vulnerable this way? is it similar to a virtual? just curioius.

---

### Post by gn2 on 2009-12-01
What it does is to create a Linux file system inside the Windows file system.

My personal opinion is that this is a parasitic arrangement and there is no benefit to using it over a conventional dual-boot.

Theoretically it's possible that when booted into Windows a virus could erase your entire Linux Wubi installation.

---

### Post by Paqman on 2009-12-01
> **gn2 said:**
> there is no benefit to using it over a conventional dual-boot.

The obvious (and very substantial) benefit is that you don't have to repartition the drive. Partitioning can be immensely intimidating for people who've never done it before.

**kakashi_12:** Using the Wubi installer to get Ubuntu onto the machine is very different from a VM. IN a VM you run both systems at the same time, one on the real hardware, and one on virtual hardware that's really just software running on the host OS.

What Wubi does is install a dual-boot system, but instead of installing Ubuntu into it's own partition it installs it into a virtual partition located on the Windows partition. It then uses a slightly different bootloader setup to boot the two different systems.

On a Wubi system, when you're in Ubuntu no part of Windows is running. It's just as safe as a traditionally installed system. Likewise when you're in Windows, Ubuntu isn't running either.

---

### Post by gn2 on 2009-12-01
> **Paqman said:**
> The obvious (and very substantial) benefit is that you don't have to repartition the drive. 

You don't have to do that to create a dual-boot.
You can use an additional drive, either internal or external.

---

### Post by Paqman on 2009-12-01
> **gn2 said:**
> You don't have to do that to create a dual-boot.
You can use an additional drive, either internal or external.

True. But Wubi does an excellent job of getting Ubuntu installed without either doing scary things to your disk or opening your wallet. And don't forget that most people have no idea that you can install extra drives in the machine so easily (a fact the USB external drive manufacturers exploit very effectively)

Bottom line: Wubi isn't aimed at you or me. But for the people it is aimed at it does a great job.

---

### Post by gn2 on 2009-12-01
> **Paqman said:**
> Bottom line: Wubi isn't aimed at you or me. But for the people it is aimed at it does a great job.

Agreed. :)

---

