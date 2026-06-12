---
title: "Easiest way to scan hardware on PC?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by PrescottLinux on 2009-04-23
Hi, I'd like to know if there is an easy way to see exactly what hardware is installed in my computer. It's a Dell Athlon 64 system, and I specifically need to know which CD/DVD drive is in it. I tried "Hardware Testing", but that didn't touch the CD/DVD drive. I'm currently using the Ubuntu 8.10 Live CD.

---

### Post by jmszr on 2009-04-23
PrescottLinux,
    This should do it:```
 sudo lshw -html > ~/Desktop/hardware.html

```
It will show up on your Desktop. The only caveat is that I don't know if it runs on Live CD - should.

---

### Post by Ahunt on 2009-04-23
Applications>Accessories>Terminal and at the prompt enter:

sudo lshw

This will show you everything about all your hardware. You can copy it into a text document and save it if you like, too.

---

### Post by PrescottLinux on 2009-04-23
Perfect!

Thanks guys

---

### Post by D1ZZ4ZZT3R on 2009-04-23
if anyone is still listening to this thread, i have a question, also. 

i did sudo lshw on my laptop and i didn't see any listing for my system fans (that i was able to recognize as such). i was hoping to find that out without having to take the computer apart, seeing as i have to know what they are so i can get them replaced. did i miss something? is there another command i can use to find that out?

thanks in advance!

---

