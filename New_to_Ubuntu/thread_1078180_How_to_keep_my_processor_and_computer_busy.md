---
title: "How to keep my processor and computer busy"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by faraz_k86 on 2009-02-23
I think there is some hardware problem in my laptop, as I keep getting a Blue screen of death in windows xp :/  but its fine in ubuntu.

but i dont use ubuntu primarily, and stays on for a little while.

so i want to test my hardware in ubuntu. There are applications in windows that keep the processor and other hardware busy.

is there any command in linux that will keep the hardware busy, like in a loop?

thanks

---

### Post by faraz_k86 on 2009-02-23
just to clarify, im looking for a terminal command and not any software

---

### Post by blazemore on 2009-02-23
You could use Folding@home, SETI@home, or something else that will use your idle CPU time. You can set it to run 100%, that will be kind of like a "stress test", plus you'll be helping science.

A BSoD is most likely driver errors, not hardware.
Run the Memory Test from the Grub menu, to see if your physical memory is working.

---

### Post by faraz_k86 on 2009-02-23
thx for the reply but i was kind of searching for an offline tool

---

### Post by 3rdalbum on 2009-02-23
I'm not aware of any preinstalled terminal command to keep the system busy, but you could install the Phoronix Test Suite from [www.phoronix.com](www.phoronix.com). It's a terminal app that has a whole bunch of benchmarks and tests available that you can use to hammer your hardware. It doesn't actually come with any tests, but the first time you ask it to perform a particular test it will automatically download it from the Internet, and use the local copy each time afterwards.

---

### Post by MJWitter on 2009-02-23
Try typing > glxgears into the terminal.
That should keep your processor and Graphics card busy... Just close the terminal after a while to end the process..

---

### Post by Peter09 on 2009-02-23
Htop will also keep your system ticking over although not as much as glxgears.

---

### Post by HavocXphere on 2009-02-23
Keeping a computer busy with some arb command is fairly useless as a way to test hardware. At best it will max out one specific component on the PC.

e.g. glxgears will makes out *one* part of the graphics card and maybe one of the cores. Memory won't be used at all since glxgears is a simple scene, large parts of the GFX card will remain untouched (shader paths etc).

You'll definitely need to download a program to effectively test the hardware. Since its a BSoD, I'd suggest starting with memtest.

---

### Post by binbash on 2009-02-23
[http://www.linuxquestions.org/questions/programming-9/script-to-get-100-cpudisk-usage-585325/](http://www.linuxquestions.org/questions/programming-9/script-to-get-100-cpudisk-usage-585325/)

---

### Post by LowSky on 2009-02-23
BSoD are most commonly the result of data errors and or driver errors.

most common reason for data errors is not defraging you computer and not keeping up with removal of cookies and trojans that can take up hard drive space that can bog down your hard drive casuing it to not to be able to eaily cache files as it ones has.

Best remedy is a malware remover like Malwarebyte AntiMalware (completly free), and to run Disk Defragment Once a month (In windows start menu, programs>Accessories>system tools>Disk Defragmenter.

---

