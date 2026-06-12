---
title: "DX Diag equivalent"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Phædrus2401 on 2009-03-23
Hey, I was wondering if there was a Linux equivalent of Windows' dxdiag app--a program that creates a report of your hardware, drivers, codecs, graphics software, and all that rot. I found it convenient several times when running Windows, so I was curious to know if there's something similar for Linux. 

Mostly I just want it on general principles, as something one should know how to do, but I also wanted to check and see if my Nvidia drivers got uninstalled when I installed my ATI drivers.

---

### Post by finer recliner on 2009-03-24
for a profile of the hardware in your system use this command:

```
sudo lshw -html > specs.html
```

the above command will output a file in your home directory called specs.html


EDIT: this command is not very universal across linux distriubtions, i only know it works in ubuntu for sure.

---

### Post by GepettoBR on 2009-03-24
sysinfo is quite similar to dxdiag, minus the sound tests and etc.

---

