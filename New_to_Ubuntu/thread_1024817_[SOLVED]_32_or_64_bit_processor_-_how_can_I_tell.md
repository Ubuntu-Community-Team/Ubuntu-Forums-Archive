---
title: "[SOLVED] 32 or 64 bit processor - how can I tell?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by loobyloo on 2008-12-29
Hi

When I installed Ubuntu I used dxdiag in Windows to tell me whether I had a 32 or 64-bit processor.  I can't remember what the answer was.  Would anyone be able to tell me how can I tell whether the computer I'm using uses a 32 or 64 bit processor?  I have Googled but the answers aren't conclusive.

Many thanks

Cliff
Ubuntu 8.10
Dell Inspiron 640m

---

### Post by Dedoimedo on 2008-12-29
Check here:

```

cat /proc/cpuinfo

```

Dedoimedo

---

### Post by loobyloo on 2008-12-29
That produces:

cpu MHz		: 800.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr
bogomips	: 3192.21
clflush size	: 64
power management:
---------------

Er...am I to take that 64 next to the clflush size as my answer?

Cliff

---

### Post by Efros on 2008-12-29
No but the fact that its a dual core suggests that it is 64 bit. Also you seem to have Cool'n Quiet enabled or some other form of frequency throttle with your cpu being clocked at 800MHz.

---

### Post by vambo on 2008-12-29
try:

```
lshw | less
```

The 1st screen full should show your cpu details
Note: Ignore any warnings to run lshw as superuser - you don't have to.

---

### Post by ELF_O8 on 2008-12-29
If its a Core 2 Duo its 64 bit.

---

### Post by Efros on 2008-12-29
sudo apt-get install cpuid

and then

cpuid

should give you all the info you need on your processor

---

### Post by loobyloo on 2008-12-29
Thanks!  That says 

cliff-laptop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1000MiB
     *-cpu
          product: Genuine Intel(R) CPU           T2050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 32 bits

So 32 bit then?

Cliff
["description: computer".  What a relief. I thought I'd been using a jam jar :) ]

---

### Post by vambo on 2008-12-29
Looks like it.
For jam-jar mode you'll have to see Microsoft to turn your comp into one ;)

---

### Post by loobyloo on 2008-12-29
I mean, that's the output from lshw.

The output from cpuid is 

 eax in    eax      ebx      ecx      edx
00000000 0000000a 756e6547 6c65746e 49656e69
00000001 000006e8 01020800 0000c189 bfe9fbff
00000002 02b3b001 000000f0 00000000 2c04307d
00000003 00000000 00000000 00000000 00000000
00000004 04000121 01c0003f 0000003f 00000001
00000005 00000040 00000040 00000003 00022220
00000006 00000001 00000002 00000001 00000000
00000007 00000000 00000000 00000000 00000000
00000008 00000000 00000000 00000000 00000000
00000009 00000000 00000000 00000000 00000000
0000000a 07280201 00000000 00000000 00000000
80000000 80000008 00000000 00000000 00000000
80000001 00000000 00000000 00000000 00100000
80000002 756e6547 20656e69 65746e49 2952286c
80000003 55504320 20202020 20202020 54202020
80000004 30353032 20402020 30362e31 007a4847
80000005 00000000 00000000 00000000 00000000
80000006 00000000 00000000 08006040 00000000
80000007 00000000 00000000 00000000 00000000
80000008 00002020 00000000 00000000 00000000

Vendor ID: "GenuineIntel"; CPUID level 10

Intel-specific functions:
Version 000006e8:
Type 0 - Original OEM
Family 6 - Pentium Pro
Model 14 - 
Stepping 8
Reserved 0

Extended brand string: "Genuine Intel(R) CPU           T2050  @ 1.60GHz"
CLFLUSH instruction cache line size: 8
Initial APIC ID: 1
Hyper threading siblings: 2

Feature flags bfe9fbff:
FPU    Floating Point Unit
VME    Virtual 8086 Mode Enhancements
DE     Debugging Extensions
PSE    Page Size Extensions
TSC    Time Stamp Counter
MSR    Model Specific Registers
PAE    Physical Address Extension
MCE    Machine Check Exception
CX8    COMPXCHG8B Instruction
APIC   On-chip Advanced Programmable Interrupt Controller present and enabled
SEP    Fast System Call
MTRR   Memory Type Range Registers
PGE    PTE Global Flag
MCA    Machine Check Architecture
CMOV   Conditional Move and Compare Instructions
FGPAT  Page Attribute Table
CLFSH  CFLUSH instruction
DS     Debug store
ACPI   Thermal Monitor and Clock Ctrl
MMX    MMX instruction set
FXSR   Fast FP/MMX Streaming SIMD Extensions save/restore
SSE    Streaming SIMD Extensions instruction set
SSE2   SSE2 extensions
SS     Self Snoop
HT     Hyper Threading
TM     Thermal monitor
31     reserved

TLB and cache info:
b0: unknown TLB/cache descriptor
b3: unknown TLB/cache descriptor
02: Instruction TLB: 4MB pages, 4-way set assoc, 2 entries
f0: unknown TLB/cache descriptor
7d: unknown TLB/cache descriptor
30: unknown TLB/cache descriptor
04: Data TLB: 4MB pages, 4-way set assoc, 8 entries
2c: unknown TLB/cache descriptor

---

### Post by scorp123 on 2008-12-29
> **loobyloo said:**
> That produces:

cpu MHz		: 800.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr
bogomips	: 3192.21
clflush size	: 64
power management: That's a 32-bit CPU. 64-bit CPU's have the "**lm**" (= Long Mode) bit flag, and that one is clearly missing in your case (in the "flags" section above).

---

### Post by scorp123 on 2008-12-29
> **Efros said:**
> No but the fact that its a dual core suggests that it is 64 bit.  Where did you get that idea from? Older Intel Core Duo CPU's are 32-bit! Only the newer series and then the successors "Core 2 Duo" are 64-bit.

---

### Post by Efros on 2008-12-29
> **scorp123 said:**
> Where did you get that idea from? Older Intel Core Duo CPU's are 32-bit! Only the newer series and then the successors "Core 2 Duo" are 64-bit.

It's why I said suggests, my expertise in Intel mobile processors is somewhat limited, hunting around yielded this.
[Intel Docs]("http://ark.intel.com/cpu.aspx?groupId=27231")

---

### Post by scorp123 on 2008-12-30
> **Efros said:**
> It's why I said suggests, my expertise in Intel mobile processors I am not an expert either, but you can tell whether a CPU is 64-bit or 32-bit by looking at the CPU flags. If there is an "lm" (**_l_**ong **_m_**ode) flag then it's a 64-bit CPU (works for both Intel and AMD). If that flag is absent it's a 32-bit CPU.

---

### Post by Efros on 2008-12-30
> **scorp123 said:**
> I am not an expert either, but you can tell whether a CPU is 64-bit or 32-bit by looking at the CPU flags. If there is an "lm" (**_l_**ong **_m_**ode) flag then it's a 64-bit CPU (works for both Intel and AMD). If that flag is absent it's a 32-bit CPU.

So we learn something new everyday.

---

