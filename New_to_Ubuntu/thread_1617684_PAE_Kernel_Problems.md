---
title: "PAE Kernel Problems"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by dashpilot79 on 2010-11-09
I installed the linux-generic-pae package and now the computer will only boot to a command line.  If i select the old kernel on Grub it will still come up to the desktop.  Is there sometype of setting that I have wrong that will make it go to the desktop when booting the PAE kernel?

Thank You,
Casey

---

### Post by Hippytaff on 2010-11-09
Do you know if you have an Nvidia Graphics card?

As far as I know PAE Kernels can take some configuring.

---

### Post by dashpilot79 on 2010-11-09
I have a ATI Radeon HD 3200 Graphics Card.
Its in an HP Laptop running a AMD Dual Core Processor
4 Gigs of Ram

---

### Post by migs73 on 2010-11-09
Do you know if PAE is supported on your machine?

Try this command;

```
cat /proc/cpuinfo | grep flags
```

If one of the returned flags is 'nx' then it is. If not your processor 'should' support the NX bit required for PAE addressing but may be switched off in your BIOS; See here for details;  [https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures)

---

### Post by dashpilot79 on 2010-11-09
Yes as far as I can tell

flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit lbrv svm_lock nrip_save
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit lbrv svm_lock nrip_save

---

### Post by migs73 on 2010-11-09
Did you download it following the procedures here;

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

If so, try it again in case the download was bad.
If not, try it as described.

:)

---

### Post by dashpilot79 on 2010-11-09
Well apparently the Header files are important.  

No Seriously though I was following directions on a different webpage that didn't have you install the Header files.  Its working fine now.

Thank you so much.

---

### Post by migs73 on 2010-11-09
Result!!

Glad to be of help.

Could you please mark the thread as solved (at the top of the first post, click on thread tools and 'mark as solved')

:)

---

