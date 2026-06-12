---
title: "copy /b 0.bin + 1.bin + 2.bin wii.iso"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by RealG187 on 2009-04-03
I am copying Wii games using a dumper that dumps the games in 3 parts. 0.bin, 1.bin, and 2.bin, the readme says to enter "copy /b 0.bin + 1.bin + 2.bin wii.iso" at a DOS prompt. I am using Linux, is there a way to combine the 3 bins into a single ISO from the terminal, basically what I am asking is what is the Linux terminal command equivalent to "copy /b 0.bin + 1.bin + 2.bin wii.iso"?

---

### Post by Peasantoid on 2009-04-03
If they're just simple file segments, you can do something like this:
```
cat 0.bin 1.bin 2.bin > wii.iso
```

---

### Post by RealG187 on 2009-04-04
> **Peasantoid said:**
> If they're just simple file segments, you can do something like this:
```
cat 0.bin 1.bin 2.bin > wii.iso
```
Thanks, I'll try that and compare the output file to the output file from my VM.

---

