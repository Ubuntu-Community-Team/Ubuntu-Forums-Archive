---
title: "Need help configuring swtichable graphics"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by Jb-1 on 2011-09-04
[SIZE=2]I've just installed ubuntu 11.04 on my HP Pavilion dv6-3120sa (so previously windows 7 user), currently using my intel hd graphics but obviously I'd like to be able to switch  to my radeonhd 5470 card. I'm a complete novice and I've been reading the beginners guides  but I'd really appreciate some definitive answers on how to sort the drivers and other aspects.

Thanks in advance [/SIZE]:)

---

### Post by TeoBigusGeekus on 2011-09-04
I think this should be done in BIOS.

---

### Post by Jb-1 on 2011-09-04
Through the GRUB thing mentioned in several simillar threads?

---

### Post by TeoBigusGeekus on 2011-09-04
No, no, no...
Grub is ubuntu's bootloader: it helps you choose which os to boot (ie. ubuntu, windows, older ubuntu kernel, etc.)
To enter bios you have to press a certain key during boot up (and well before entering grub): f1, f2, del, etc. I don't know which button applies to your motherboard; there should be a brief message indicating it during boot up though.

---

### Post by Jb-1 on 2011-09-04
Oh, apologies, I understand what you mean now. I think I press delete to enter BIOS. so upon entering BIOS I 'blacklist'the discrete card? 
Or is there another confirmed way of switching while in Ubuntu? 
And can i even just use the ati card in ubuntu as opposed to using the intergrated intel one?

---

### Post by TeoBigusGeekus on 2011-09-04
> **Jb-1 said:**
> Oh, apologies, I understand what you mean now. I think I press delete to enter BIOS. so upon entering BIOS I 'blacklist'the discrete card? 
Or is there another confirmed way of switching while in Ubuntu? 
And can i even just use the ati card in ubuntu as opposed to using the intergrated intel one?

I don't know about ways to do it in ubuntu, but blacklisting it from bios is the surest way.
Once it's blacklisted in your bios, ubuntu will have no other choice but to use your ati card instead of your inter one.

---

### Post by Jb-1 on 2011-09-04
Thanks for your help. I'll report back once I've tried your advice.

---

### Post by madjr on 2011-09-04
yes, the bios is your best bet for now if not we'll try to further assist you.

---

### Post by Jb-1 on 2011-09-04
How would I do this in BIOS? I don't want to screw anything up through guesswork.

---

### Post by madjr on 2011-09-04
> **Jb-1 said:**
> How would I do this in BIOS? I don't want to screw anything up through guesswork.

dont worry you wont screw up anything.

all BIOS have the option to load DEFAULT SETTINGS in case you want to go back to how it was before. Just use common sense and dont go crazy switching everything on or off. You can also google some of the options you see.

anyway, if you still unsure, you can use a camera and upload/attach pics of your bios screens and we'll tell you which one it is.

Note: some early models may not have the bios option.

---

