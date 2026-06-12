---
title: "dual boot: ubuntu and windows 7"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by alien8predator on 2009-11-08
I have the following problem. I had ubuntu installed and I had Win7 RC installed. I then Installed windows 7 (full version) and I lost my grub loader and was not able to boot in ubuntu. I found a solution to fix that problem by booting with the 9.10 alternate cd and reinstalling the grub on the  partition that my ubuntu installation was on. Now my problem is when I want to boot windows 7 I have go into the bios boot device priorty setting to get windows 7 to boot and when I reboot and want to switch back to ubuntu I have to go back into the bios boot device priorty and select my other disc. If I'm not mistaken this probably has to do something with the my mbr. Can someone point me in the right direction as in how to fix this?

---

### Post by yanceypd on 2009-11-08
Have you tried update-grub from terminal?

---

### Post by alien8predator on 2009-11-08
> **yanceypd said:**
> Have you tried update-grub from terminal?

No I didn't, but I just did it after reading your reply and it works fine :) Thanks. I should have searched considering the answer was that easy :) learned a real useful command today :D

---

