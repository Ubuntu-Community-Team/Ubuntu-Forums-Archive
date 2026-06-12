---
title: "Ubuntu Studio slowww..."
date: 2010-02-28
forum: New to Ubuntu
---

### Post by ktronicon5 on 2010-02-28
Hi folks,
I installed Ubuntu Studio (9.10) a few months ago and it has been very slow since the beginning. My system is an Intel P4 1.6 Ghz with 1.5 GiB RAM.  In system monitor "CPU History" jumps over 100% just from running Firefox and clicking around a little. I tried disabling unused applications like the Bluetooth manager and the Accessibility thing, but that didn't seem to help. Navigating around in Ubuntu is slow and occasionally freezes for several seconds at a time. Any ideas? 

Here is the output from cat /proc/cpuinfo if that means anything. 


```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 1.60GHz
stepping	: 4
cpu MHz		: 1599.735
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
bogomips	: 3199.47
clflush size	: 64
power management:
```

I'm running the i386 install as I believe this processor to be 32-bit? 
Also, if this means anything, I've noticed the response from certain applications, like Hydrogen drum machine, to be much faster than other applications and Ubuntu in general.

Any help greatly appreciated!
Thanks,
k

---

### Post by mickie.kext on 2010-02-28
UbuntuStudio has RealTime kernel which means that is optimized for uses which require high process priority - like audio & video production and such. Bad news for you is that it also requires fast multi-core processor. So because your CPU is very old, I suggest you go with ordinary kernel and ordinary Ubuntu. You can still install all packages and do multimedia creation just fine with plain Ubuntu.

---

### Post by ktronicon5 on 2010-02-28
Ok I'll try that, thanks!
While I have you here, I remeber having a really hard time getting pulseaudio to work and ended up removing it and just using using a combination of Jack and direct ASIO hardware mixing...but it was not at all an easy task and i can by no means remember what i finally ended up doing to make it work (even after removing pulseaudio it took a couple days of fiddling to get it to work...) So i realize this is off-topic but are you aware of this problem? 
My soundcard is a  Hoontech STA (ICE1712) multi-in multi-out
Thanks so much
k

---

### Post by mickie.kext on 2010-02-28
Sorry, I can help you with that since I never dealt with that particular sound card. 

But, it might not be necessary to reinstall whole thing. I know it is possible to install plain Ubuntu and then install RT kernel and Ubuntu Studio via Synaptic and use it that way. I never tried other way around but I think it is possible. You might want to try that before you wipe whole thing.

PS: I also tried normal kernel + Ubuntu Studio packages and all worked well. So you might just need to select normal kernel in Synaptic, install it, reboot machine and then select that kernel in GRUB menu. It is worth a try.

---

### Post by ktronicon5 on 2010-03-01
still new at this... RT kernel is the special kernel that Studio runs off of? is it this kernel that was slowing down my system originally? not sure. 
anyway i re-installed ubuntu original. speed is back up, just have to get the sound working now...
thanks!!
k

---

### Post by mickie.kext on 2010-03-01
> **ktronicon5 said:**
> still new at this... RT kernel is the special kernel that Studio runs off of? is it this kernel that was slowing down my system originally? not sure. 
anyway i re-installed ubuntu original. speed is back up, just have to get the sound working now...
thanks!!
k

Real Time kernel is specially patched kernel which allows user space processes to have higher priority than kernel itself. That is not possible with normal one. RT is obviously one that hase made troubles for you because your hardware is to slow to deal with it.

My previous post was advice how can you get rid of RT kernel without reinstalling whole system (since Ubuntu Studio is just repackaged Ubuntu with RT kernel). But now that you have wiped Ubuntu Studio and installed normal Ubuntu, you can ignore that post:).

I am glad I helped. Good luck with setting up your sound card.

---

