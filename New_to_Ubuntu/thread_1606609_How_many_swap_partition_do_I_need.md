---
title: "How many swap partition do I need?"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by beew on 2010-10-26
This is probably a simple question. Suppose I want to make a dual boot (or multi boot)  system with different Ubuntus (or different Linuxes) do I need to make a swap partition for each of them? Does it matter where they locate. So for example, I already have Ubuntu installed in such a way that I have, from left to right, a root partition, a /home partition and in the right end a swap partition. Now I want to carve up the /home partition to say, install Xubuntu (just a hypothetical scenario), that would disconnect the swap partition of the original Ubuntu installation from its  /root and /home partition. Is this ok?

---

### Post by albert s on 2010-10-26
as far as I know you only need one swap as you are only using one version at a time.
I only have one swap anyway, and sometimes have 2 or 3 versions to try them out.

---

### Post by ironic.demise on 2010-10-26
> **beew said:**
> This is probably a simple question. Suppose I want to make a dual boot (or multi boot)  system with different Ubuntus (or different Linuxes) do I need to make a swap partition for each of them? Does it matter where they locate. So for example, I already have Ubuntu installed in such a way that I have, from left to right, a root partition, a /home partition and in the right end a swap partition. Now I want to carve up the /home partition to say, install Xubuntu (just a hypothetical scenario), that would disconnect the swap partition of the original Ubuntu installation from its  /root and /home partition. Is this ok?

One, All Linux Distributions will make use of any swap space on the computer.
Correct me if I'm wrong.

Bear in mind that you never "associate" a distro with a swap partition, thus no partition is ever "keeping" a swap space.

---

### Post by uRock on 2010-10-26
Just one. All Linux installs can share it.

---

### Post by beew on 2010-10-26
Thanks guys, I guess I will mark this as solved. That was fast. :)

---

