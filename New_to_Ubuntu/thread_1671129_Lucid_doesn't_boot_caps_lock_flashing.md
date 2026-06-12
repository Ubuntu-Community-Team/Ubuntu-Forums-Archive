---
title: "Lucid doesn't boot caps lock flashing"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by ufc on 2011-01-19
Hi. I'm running ubuntu 10.04 netbook edition on acer aspire one a110L. After bios splash screen screen goes black hard drive light shows activity then caps lock light flashes. No change after that and have to force power off by holding power button. 
Control alt delete does not do anything. 
 
Any fixes out there?

---

### Post by JohnHeikkila on 2011-01-19
My best guess right now would be, that the kernel is "panicking".
I'm no kernel expert, so the best advice I can give with the information you have provided, is to reinstall Ubuntu :(

---

### Post by JohnHeikkila on 2011-01-19
My best guess right now would be, that the kernel is "panicking".
I'm no kernel expert, so the best advice I can give with the information you have provided, is to reinstall Ubuntu :(

---

### Post by JohnHeikkila on 2011-01-19
My best guess would be, that the kernel is "panicking". I don't know why it panics so early, or whether it's even panicking, but you didn't give much info about your system specs or about your Ubuntu install ;)

---

### Post by JohnHeikkila on 2011-01-19
My best guess would be, that the kernel is "panicking". I don't know why it panics so early, or whether it's even panicking, but you didn't give much info about your system specs or about your Ubuntu install ;)

---

### Post by ufc on 2011-01-20
hmmmm.... mayhaps time to up to 10.10 then.  or try boot a previous kernel. sorry rambling to myself

---

### Post by ufc on 2011-01-20
hmmmm.... mayhaps time to up to 10.10 then.  or try boot a previous kernel. sorry rambling to myself

---

### Post by Paqman on 2011-01-20
If you've got the option, definitely try booting a previous kernel, or try booting into recovery mode and seeing if you can get to a command line. If you can boot to a command line, run:
```
startx
```

---

### Post by NickJones on 2011-01-20
Hold down shift during bootup and select, "failsafeX" then hit enter.

---

### Post by NickJones on 2011-01-20
Hold down shift during bootup and select, "failsafeX" then hit enter.

---

### Post by ufc on 2011-01-20
holding down shift gets me to grub menu but previous kernels don't load, get flashing caps lock again. gonna try fresh install of ubuntu now.

---

