---
title: "Ok, new question, lol.  Should I use 64 bit?"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by bustedbit on 2010-05-08
Ok, I know I shouldn't have to ask, but I will.  My system has 4 gigs of ram, my processor is "Intel Pentium Dual T3400 2.16 GHz".  Is it a good idea to run 64 bit on this hardware?

---

### Post by thane1 on 2010-05-08
IMHO go for it.  I've had relatively few problems over the last few years with ubuntu 64 bit and I think they were probably going to be problems to sort out even if I was on 32 bit (mostly proprietary program related as in video formats, etc).  Why limit yourself?  Cheers.

---

### Post by -humanaut- on 2010-05-08
I have a Single core AMD chip (2.2ghz 2 Gb's of Ram) I've been running 64bit systems on it for awhile.

---

### Post by paydaydaddy on 2010-05-08
You will get different opinions on this. Here is mine. It depends on what you do with your computer. The biggest difference between 32 bit and 64 bit is how much memory they are capable of using and how they use it. If you are doing memory intensive things (virtual machines, video encoding, cad, etc.) then you will probably benefit from loading up with tons of RAM on a 64 bit system. For the average user with a 64 bit system there is little to be gained. Some have said they have seen a performance increase by going 64 bit. For most it is a 64 bit system in a 32 bit world. If you have the time and inclination there is no harm in trying it. I set up a 64 bit win 7 system on older equipment for the experience, but then I am a glutton for punishment.

---

### Post by bustedbit on 2010-05-08
> **paydaydaddy said:**
> You will get different opinions on this. Here is mine. It depends on what you do with your computer. The biggest difference between 32 bit and 64 bit is how much memory they are capable of using and how they use it. If you are doing memory intensive things (virtual machines, video encoding, cad, etc.) then you will probably benefit from loading up with tons of RAM on a 64 bit system. For the average user with a 64 bit system there is little to be gained. Some have said they have seen a performance increase by going 64 bit. For most it is a 64 bit system in a 32 bit world. If you have the time and inclination there is no harm in trying it. I set up a 64 bit win 7 system on older equipment for the experience, but then I am a glutton for punishment.
Laright, so let me ask you this.  If I decide to upgrade to 64 bit, will I lose all the packages and programs I've so painstakingly accumulated?  I'd hate to have to start over again, that's such a pain in the ***.

---

### Post by BT1 on 2010-05-08
If you can, and your processor supports 64 bit, then I personally feel YOU MUST. Lol. It's like having a Ferrari and only going half as fast as you could. 32 bit is just for those who haven't yet upgraded to a 64 bit processor.

If you don't know if your processor is 64 bit compatable, and you're running linux right now, you can find out this way:

1.) GO to Accessories in your applications menu and select "Teminal"
2.) When the box pops up with a blinking curser, type this:

```
sudo lshw -c cpu
```This will tell Linux to show you the stats of your processor. This is what I get when I run that command on my test machine:

```
optimusprime@OPHP:~$ sudo lshw -c cpu
[sudo] password for optimusprime: 
  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
       slot: U10
       size: 800MHz
       capacity: 800MHz
       width: 64 bits
       clock: 200MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr
 pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx
** _x86-64_** constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor
 ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm ida tpr_shadow vnmi
 flexpriority cpufreq

```The "Capabilities" section shows what your processor is capable of. I bolded and underlined "x86-64" and this tells me if my processor is 64 bit capable since "x86-64" is another designation for "64 Bit". I'm a nub so that's about all I know.

Now it's not going to be "OMG IT IS SO MUCH FASTER" but it's noticable when compiling, doing intense data functions, and when or if you ever decide to mess with Virtual Machines (running operating systems inside your desktop), having a 64 bit base system becomes reeaaally helpful.

Hope it works out for you.

---

### Post by barkej on 2010-05-08
As stated previously you will see people on both sides of the fence. 
I tend to prefer having the 64bit system myself.

I would say give 64bit a go. If you don't like it you can always reload 32bit.

---

### Post by paydaydaddy on 2010-05-08
To my knowledge there is no way to convert to 64 bit without wiping out your settings. You don't just upgrade, you do a clean install. If you have a seperate home partition you may save some stuff, but I'm not the expert to tell you for sure. If I were in your position I would dual boot. Actually I wouldn't, I would build a seperate machine, but I realize that is not practical for for most.

---

### Post by bustedbit on 2010-05-08
> **paydaydaddy said:**
> To my knowledge there is no way to convert to 64 bit without wiping out your settings. You don't just upgrade, you do a clean install. If you have a seperate home partition you may save some stuff, but I'm not the expert to tell you for sure. If I were in your position I would dual boot. Actually I wouldn't, I would build a seperate machine, but I realize that is not practical for for most.
Youve given me plenty to think about.  I guess I could just make a list of my packages and reinstall afterwards.  But I will still have my personal files right?  Music, video, etc.?

---

### Post by BT1 on 2010-05-08
> **paydaydaddy said:**
> To my knowledge there is no way to convert to 64 bit without wiping out your settings. You don't just upgrade, you do a clean install. If you have a seperate home partition you may save some stuff, but I'm not the expert to tell you for sure. If I were in your position I would dual boot. Actually I wouldn't, I would build a seperate machine, but I realize that is not practical for for most.

Lol, or use clonezilla and save the structure (after resizing and making it smaller) onto an external hard drive, then install a 64 bit system, then use virtualbox or whatever to run the old system in a virtual machine mwa ha ha:p.

---

### Post by uRock on 2010-05-08
> **bustedbit said:**
> Youve given me plenty to think about.  I guess I could just make a list of my packages and reinstall afterwards.  But I will still have my personal files right?  Music, video, etc.?
If you installed with  a /home partition along with the / partition, then yes.

---

### Post by paydaydaddy on 2010-05-08
What BT1 said. That way you are getting some practical use out of your 64 bit memory capabilities. Don't forget to load up on RAM first.

---

### Post by BT1 on 2010-05-08
> **bustedbit said:**
> Youve given me plenty to think about.  I guess I could just make a list of my packages and reinstall afterwards.  But I will still have my personal files right?  Music, video, etc.?

When you installed, did you make two separate partitions, namely, "/" and "/home"? If you did then you can just format the "/" partition and re-install on that and you'd get your music and stuff from the /home as if nothing happened (in my experience). Or just save that stuff to an external and re-install.

---

