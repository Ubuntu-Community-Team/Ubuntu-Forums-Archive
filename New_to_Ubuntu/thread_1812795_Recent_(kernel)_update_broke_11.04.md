---
title: "Recent (kernel?) update broke 11.04"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by TerribleLIar on 2011-07-26
Hello. Just starting like yesterday, I noticed a new section on GRUB about earlier versions of Ubuntu. Also at this same time, I can't pass the login screen. After entering my password and pressing enter, I hear the login sound and it just stays at a blank background and Unity never loads. Using the earlier version on GRUB allows everything to work, but I guess it would be better if I got the new kernel (at least, that's what I'm assuming) to work with my computer, right? I'm on an ASUS 1000HE netbook. Is there anything I can really change to fix it?

---

### Post by rosencrantz on 2011-07-26
Can you post the relevant kernel versions?

(should be in /boot)

---

### Post by lkjoel on 2011-07-26
> **TerribleLIar said:**
> Hello. Just starting like yesterday, I noticed a new section on GRUB about earlier versions of Ubuntu. Also at this same time, I can't pass the login screen. After entering my password and pressing enter, I hear the login sound and it just stays at a blank background and Unity never loads. Using the earlier version on GRUB allows everything to work, but I guess it would be better if I got the new kernel (at least, that's what I'm assuming) to work with my computer, right? I'm on an ASUS 1000HE netbook. Is there anything I can really change to fix it?
I have the same problem. Sometimes I have to boot into Ubuntu Classic, log out, and then boot into Ubuntu.
If you still get the blank screen problem, a simple way of getting back to the login screen (without rebooting) is either by CTRL+ALT+BACKSPACE, or CTRL+ALT+F3, login, and type in the Terminal:
```
sudo kill `pidof X`
```

---

### Post by rosencrantz on 2011-07-26
Another thought - I'd assume the EeePC has on-board graphics, but this was a very common problem with dedicated graphics cards in the past: If applicable, try updating/reinstalling your graphics driver with the new kernel running (do it from the terminal if you can get one with ctrl+alt+F1).

---

### Post by TerribleLIar on 2011-07-26
Trying the new kernel some more, it seems to work sometimes, but not 100'%. I guess I need to boot into both modes more to make sure that the previous kernel isn't also screwing up now and finding out the problem is unrelated to the kernel.

@rosencrantz - New kernel is 2.6.38-10. Old version is 2.6.38-8. As for graphic drivers, do you mean the proprietary driver installer? It doesn't say there are any to install.

@Ikojel - I'll give that a try. Thanks.

---

### Post by lkjoel on 2011-07-26
> **rosencrantz said:**
> Another thought - I'd assume the EeePC has on-board graphics, but this was a very common problem with dedicated graphics cards in the past: If applicable, try updating/reinstalling your graphics driver with the new kernel running (do it from the terminal if you can get one with ctrl+alt+F1).
CTRL+ALT+F1 sometimes is used for logging. I usually use CTRL+ALT+F3 to be safe.

---

