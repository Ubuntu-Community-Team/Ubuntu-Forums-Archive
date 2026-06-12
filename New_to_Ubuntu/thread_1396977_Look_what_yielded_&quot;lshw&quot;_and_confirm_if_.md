---
title: "Look what yielded &quot;lshw&quot; and confirm if i have 64-word CPU, please"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by Ubunser on 2010-02-02
```
*-memory
          description: System memory
          physical id: 0
          size: 3019MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical

```

Also does it says my RAM is 3Gb or I'm wrong? Cause when I was buying they told RAM is 2Gb. My main question was about CPU though.

---

### Post by Ubunser on 2010-02-02
I'm sorry I thought something else just above that is important too.

```
proggist-laptop           
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3019MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T6500  @ 2.10GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 2100MHz
          capacity: 2100MHz
          width: 64 bits

```

So, I'm puzzled as in the beginning it says: "computer - 32"

---

### Post by l-x-l on 2010-02-02
Looks right to me. The CPU is 64-bits. Do you have 4 GBs of memory installed? Maybe the memory bus is only 32-bits. Same with my laptop. Even though I have a 64-bit capable processor I can only use 3.2 GBs of memory, even when using a 64-bit OS.

---

### Post by Ubunser on 2010-02-02
file /bin/ls    gave:

```
 file /bin/ls
/bin/ls: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, stripped
```


Any suggestions?

---

### Post by bodhi.zazen on 2010-02-02
To see what architecture you have installed , use

```
uname -m
```If it i686, check your processor with

```
grep ' lm ' /proc/cpuinmfo
```Of course you can always google:

[http://www.google.com/search?q=Intel%28R%29+Core%28TM%292+Duo+CPU+++++T6500+specifications&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a]("http://www.google.com/search?q=Intel%28R%29+Core%28TM%292+Duo+CPU+++++T6500+specifications&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")

which yields

[http://ark.intel.com/Product.aspx?id=37255](http://ark.intel.com/Product.aspx?id=37255)

Which in turn tells us your CPU is indeed 64 bit.

As far as your RAM, how much were you expecting to see ? What type of video card do you have and how much ram does it use (assuming it is integrated).

---

### Post by audiomick on 2010-02-02
According to the output in the first post, you have a 64bit CPU.

I am not sure exactly what the file /bin/ls is, but on my system the output of the command "file /bin/ls" is this.

```
mick@ubuntu-desktop:~$ file /bin/ls
/bin/ls: [COLOR="Red"]**ELF 64-bit LSB executable, x86-64, version**[/COLOR] 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

```

I definitely have a 64bit system installed, so I suspect you have a 32bit system installed on a machine with a 64bit CPU.

edit: bodhi.zazen psoted whilst I was writing. Take his advice; he knows more about it than me. ;)

---

### Post by Ubunser on 2010-02-02
Thank you! I figured it thanks to you. Now I know I can get a 64 FreeBSD

---

