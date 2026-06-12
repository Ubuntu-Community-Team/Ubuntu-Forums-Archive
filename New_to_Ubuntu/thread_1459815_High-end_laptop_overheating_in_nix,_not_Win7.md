---
title: "High-end laptop overheating in *nix, not Win7"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by Zerp64 on 2010-04-21
This is pretty annoying. Running any sort of application that uses a good amount of CPU cycles for more than a few seconds, even with the CPU clocked down to ~300MHz. The system freezes instead of shuts down, and trying to do a hard reboot doesn't work either. I'm force to remove the battery and yank out the power cord.

This is pretty annoying, because the system works fine with Windows installed. I mean, the thing is a mobile furnace, but that's not anything new.

The system is a Fujitsu Lifebook n5010. Its got a radeon card in it, but I don't think that's a part of the problem.

---

### Post by achase79 on 2010-04-21
are you using cpu scaling? or bios underclocking?

---

### Post by Mark Phelps on 2010-04-22
Sorry, don't have a solution for you.  I've seen an alarming number of posts from folks that are experiencing much the same overheating problems using laptops and Ubuntu 9.10.  Evidently, the newer kernel versions in 9.10 have problems handling CPU scaling such that the CPU tends to run at full speed nearly most of the time -- causing the laptops to overheat.

All I can suggest for now is that you try running the 10.04 LiveCD to see how it behaves.  Perhaps the newer kernel versions in that can better handle CPU scaling.

---

### Post by nhasian on 2010-04-22
> **Mark Phelps said:**
> All I can suggest for now is that you try running the 10.04 LiveCD to see how it behaves.  Perhaps the newer kernel versions in that can better handle CPU scaling.

based on his profile it appears he is already using the developmental version of 10.04.

Zerp64, even with lucid, its still using the linux 2.6.32 kernel.  you can try the 2.6.33 kernel instead as they have made a lot of changes for ATI cards:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)

and since your are already using a prerelease version of ubuntu you may also be comfortable with the 2.6.34RC5:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/)

---

### Post by badrra on 2010-05-12
Lucid and Karmic boast of a quick boot. Actually that uses a lot of CPU cycles. I had the same problem and I realized that the issue is really "ondemand". As you require more cpu power, it swtiches to a higher frequency but the fans does'nt appear to respond quick enough to cool down the PC. 

What I did? I switched to userspace and set the frequency to the lowest. That way it doesnt heat up my laptop. 

Now I am compiling, watching videos, downloading all at the same time and my PC temp? never went up to 60c (normal for my PC). 

Laptop is a lot cooler, and performance is the same.

---

### Post by Zerp64 on 2010-05-31
Hang on. Wouldn't lowering CPU freq cause the chip to become much slower? Anyways, even running the CPU at the lowest setting (300MHz) still causes the machine to overheat after a bit of use.

Oh, and an update: Even using the latest (final) Lucid w/ all updates doesn't help. The laptop still overheats.

---

### Post by nhasian on 2010-05-31
can you verify that its indeed the cpu causing all the heat?  have you checked the temperatures for the GPU and hard disk?  also have you cleaned the dust out of the fans and are they spinning properly and getting enough airflow?

---

### Post by Zerp64 on 2010-06-02
The laptop is totally clean: no dust inside of it at all. Fans are spinning just fine, and Speedfan (although this is when Windows is installed, so it may be totally invalid) reports that the CPU is always hottest, not the GPU. CPU can reach 90-100c, while the GPU sits at ~70c while running, say, a youtube video and Win7 not-quite-compiz running.

How would I check the temps in a *nix install? I know there's a command for it, but I've forgotten it. I think it involves a simple cat command, right?

---

### Post by nhasian on 2010-06-02
you can use the command:

```
sensors
```

---

### Post by gsocker on 2010-06-02
You could try using the 'conservative' governor, if available. This ramps the speed up/down slower than ondemand - brief bursts of full CPU load will not cause cpufreq to jump straight to the max processor speed like ondemand will. 

Also, 90C seems quite hot for a CPU. My laptop will force the lowest CPU speed possible at 89C, and shut itself down at 91C. 

Try cat /proc/acpi/thermal_zone/THRM/temperature.
Note: "THRM" varies depending on the manufacturer's BIOS code. 
My desktop uses THRM, laptop is THRM0.

---

