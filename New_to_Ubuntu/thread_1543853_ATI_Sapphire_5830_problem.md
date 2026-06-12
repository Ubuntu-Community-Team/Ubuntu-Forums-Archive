---
title: "ATI Sapphire 5830 problem"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by auroraa9420 on 2010-08-01
yes i bougth this card 1 week ago and i cant install the drivers because i dont have the new kernel for it

iv been trying to compile and install the kernel but i got a system panic

thats because i left the configs alone, can a pro help me on this

---

### Post by jtarin on 2010-08-01
Where did you get instructions for rebuilding the kernel with this driver enabled? I have always avoided ATI cards like the plague. Not a good history in Linux or Windows when it comes to system compatibility. Good buy, but buyer beware.[Info]("http://hyperom.com/2010/05/25/ati-still-making-horrible-linux-drivers-5830-included.html")

---

### Post by auroraa9420 on 2010-08-01
> **jtarin said:**
> Where did you get instructions for rebuilding the kernel with this driver enabled? I have always avoided ATI cards like the plague. Not a good history in Linux or Windows when it comes to system compatibility. Good buy, but buyer beware.[Info]("http://hyperom.com/2010/05/25/ati-still-making-horrible-linux-drivers-5830-included.html")


well usualy all kernel compilation instructions are pretey much the same soo

i cant help you

---

### Post by jtarin on 2010-08-01
> **auroraa9420 said:**
> well usualy all kernel compilation instructions are pretey much the same soo

i cant help youThat's odd because I have never compiled a kernel with that card or for that matter any other ATI card enabled, as it would be redundant to do so, in my case as I do not use ATI cards and I would not want something in my kernel that I don't use. By the same token if my kernel is missing a feature that I want and there are specific instructions for building that feature I would follow them. If you want to enable a module that is not built in to the kernel you have to add it to the compilation. If your just going to use a generic kernel then you'll have to be satisfied with any ATI modules built in and enabled.

---

### Post by clhsharky on 2010-08-01
auroraa9420

What release are you on?
Latest cat works fine in Lucid.

Sharky

---

### Post by auroraa9420 on 2010-08-01
> **clhsharky said:**
> auroraa9420

What release are you on?
Latest cat works fine in Lucid.

Sharky

cat??

---

### Post by auroraa9420 on 2010-08-01
> **jtarin said:**
> That's odd because I have never compiled a kernel with that card or for that matter any other ATI card enabled, as it would be redundant to do so, in my case as I do not use ATI cards and I would not want something in my kernel that I don't use. By the same token if my kernel is missing a feature that I want and there are specific instructions for building that feature I would follow them. If you want to enable a module that is not built in to the kernel you have to add it to the compilation. If your just going to use a generic kernel then you'll have to be satisfied with any ATI modules built in and enabled.


well now im recompiling the kernel and i hope that its going to work

and its a fail that developers dont work with fail software :S

---

### Post by clhsharky on 2010-08-01
> Latest cat
Catalyst 10.7

---

### Post by jtarin on 2010-08-01
> **auroraa9420 said:**
> cat??
[I think he is trying to point you to.......]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")
This is available through Synaptic....[Catalyst Control Center for the ATI Radeon and FireGL graphics accelerators]("http://www.amd.com/us/products/technologies/ati-catalyst/Pages/catalyst.aspx")

---

### Post by auroraa9420 on 2010-08-02
> **jtarin said:**
> [I think he is trying to point you to.......]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")
This is available through Synaptic....[Catalyst Control Center for the ATI Radeon and FireGL graphics accelerators]("http://www.amd.com/us/products/technologies/ati-catalyst/Pages/catalyst.aspx")

yes afraid that this will make something that i was torturing my self for a long time :S

OUT OF RANGE 75GHZ/60mhz

---

