---
title: "Bit Processor"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by ssdt on 2009-08-04
I am using Dell's 530N Desktop. I want to find what my bit is cause in most of the dowloads it says 32 bit or 64 bit processor. How can I find that information in Ubuntu?

---

### Post by Soulcage on 2009-08-04
sudo lshw
in a terminal

---

### Post by OffAxis on 2009-08-04
a 32-bit operating system could still be installed on 64-bit hardware.

```
uname -m
```

would tell you what version of the OS you have.

---

### Post by ibuclaw on 2009-08-04
To find out what your **CPU** is capable of:
```
grep "flags" /proc/cpuinfo
```
And if you see the following capability:
[LIST]
[*]**lm** - Long Mode, it is a 64 bit capable processor
[/LIST]

If you don't see that, your CPU only supports 32bit (granted that it is an Intel/AMD desktop processor ;))

Regards
Iain

---

### Post by ajgreeny on 2009-08-04
I couldn't resist trying this tinivole and this is my output, which doesn't contain any of the codes you mentioned.  So what does this tell me?
```
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up
```It's a Sempron 2400+, by the way, so should show **tm** according to what you said above.

---

### Post by ibuclaw on 2009-08-04
> **ajgreeny said:**
> I couldn't resist trying this tinivole and this is my output, which doesn't contain any of the codes you mentioned.  So what does this tell me?
```
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up
```It's a Sempron 2400+, by the way, so should show **tm** according to what you said above.

It tells you that you aren't running on an Intel CPU. ;)

---

### Post by ajgreeny on 2009-08-05
OK, Thanks tinivole.

---

### Post by 3rdalbum on 2009-08-05
A quick Google told me that those machines come with a Core 2, Pentium Dual Core, or a Celeron. In short, they're all Core 2-generation CPUs, so you can use 32-bit or 64-bit.

Also, this Ubuntu Forums post told me the same thing: [http://ubuntuforums.org/showpost.php?p=4316889&postcount=22]("http://ubuntuforums.org/showpost.php?p=4316889&postcount=22")

If you've got 4 gigabytes of RAM or more you should preferably use the 64-bit edition in order to address that much RAM. But either edition will work.

---

### Post by ibuclaw on 2009-08-05
> **3rdalbum said:**
> If you've got 4 gigabytes of RAM or more you should preferably use the 64-bit edition in order to address that much RAM. But either edition will work.
A 64bit architecture isn't mandatory to access 4Gb+ of RAM, all you require is a PAE enabled kernel. Both 32bit and 64bit support this.

---

### Post by jerome1232 on 2009-08-05
> **3rdalbum said:**
> A quick Google told me that those machines come with a Core 2, Pentium Dual Core, or a Celeron. In short, they're all Core 2-generation CPUs, so you can use 32-bit or 64-bit.

Not this sempron all x86_64 cpu's will have lm in their flags, this one doesn't so it's an x86 processor. It's 32 bit.

I'm having issues today I swear that post said op had a celeron, but it says sempron lol. They are practically the same thing :P

---

### Post by ibuclaw on 2009-08-05
> **ajgreeny said:**
> OK, Thanks tinivole.

hmm... I've just stumbled upon this information, seems that I was wrong in the first instance. It seems that you only can tell a 64bit capable machine from a none 64bit capable machine, rather than a tag for each arch. I've corrected the first post to supplement this.


Here is an extensive list (as found in cpufeatures.h in the Linux kernel source):
should probably make a reference thread of this, as information is nearly impossible to find:

```

Intel-defined CPU features:
	fpu	Onboard FPU/Hardware FPU support 
	vme	Virtual Mode Extensions 
	de	Debugging Extensions 
	pse	Page Size Extensions 
	tsc	Time Stamp Counter 
	msr	Model-Specific Registers 
	pae	Physical Address Extensions 
	mce	Machine Check Architecture 
	cx8	CMPXCHG8 instruction 
	apic	Onboard APIC 
	sep	SYSENTER/SYSEXIT 
	mtrr	Memory Type Range Registers 
	pge	Page Global Enable 
	mca	Machine Check Architecture 
	cmov	CMOV instructions (plus FCMOVcc, FCOMI with FPU)
	pat	Page Attribute Table 
	pse36	36-bit PSEs 
	pn	Processor serial number 
	clflsh	"clflush" CLFLUSH instruction 
	ds	"dts" Debug Store 
	acpi	ACPI via MSR 
	mmx	Multimedia Extensions 
	fxsr	FXSAVE/FXRSTOR, CR4.OSFXSR 
	xmm	"sse" 
	xmm2	"sse2" 
	selfsnoop	"ss" CPU self snoop 
	ht	Hyper-Threading 
	acc	"tm" Automatic clock control 
	ia64	IA-64 processor 
	pbe	Pending Break Enable 
	xmm3    "pni" SSE-3
	pclmulqdq       PCLMULQDQ instruction
	dtes64  64-bit Debug Store
	mwait   "monitor" Monitor/Mwait support
	dscpl   "ds_cpl" CPL Qual. Debug Store
	vmx     Hardware virtualization
	smx     Safer mode
	est     Enhanced SpeedStep
	tm2     Thermal Monitor 2
	ssse3   Supplemental SSE-3
	cid     Context ID
	fma     Fused multiply-add
	cx16    CMPXCHG16B
	xtpr    Send Task Priority Messages
	pdcm    Performance Capabilities
	dca     Direct Cache Access
	xmm4_1  "sse4_1" SSE-4.1
	xmm4_2  "sse4_2" SSE-4.2
	x2apic  x2APIC
	aes     AES instructions
	xsave   XSAVE/XRSTOR/XSETBV/XGETBV
	osxsave XSAVE enabled in the OS
	avx     Advanced Vector Extensions
	hypervisor      Running on a hypervisor



AMD-defined CPU features:
	syscall	SYSCALL/SYSRET 
	mp	MP Capable. 
	nx	Execute Disable 
	mmxext	AMD MMX extensions 
	fxsr_opt	FXSAVE/FXRSTOR optimizations 
	gbpages	"pdpe1gb" GB pages 
	rdtscp	RDTSCP 
	lm	Long Mode (x86-64) 
	3dnowext	AMD 3DNow! extensions 
	3dnow	3DNow! 
	lahf_lm	LAHF/SAHF in long mode 
	cmp_legacy	If yes HyperThreading not valid 
	svm	Secure virtual machine 
	extapic	Extended APIC space 
	cr8_legacy	CR8 in 32-bit mode 
	abm	Advanced bit manipulation 
	sse4a	SSE-4A 
	misalignsse	Misaligned SSE mode 
	3dnowprefetch	3DNow prefetch instructions 
	osvw	OS Visible Workaround 
	ibs	Instruction Based Sampling 
	sse5	SSE-5 
	skinit	SKINIT/STGI instructions 
	wdt	Watchdog timer 


CPU types for specific tunings:
        k8      Opteron, Athlon64
        k7      Athlon
        p3      P3
        p4      P4
        constant_tsc    TSC ticks at a constant rate
        up      smp kernel running on up
        fxsave_leak     FXSAVE leaks FOP/FIP/FOP
        arch_perfmon    Intel Architectural PerfMon
        nopl    The NOPL (0F 1F) instructions
        pebs    Precise-Event Based Sampling
        bts     Branch Trace Store
        syscall32       syscall in ia32 userspace
        sysenter32      sysenter in ia32 userspace
        rep_good        rep microcode works well
        mfence_rdtsc    Mfence synchronizes RDTSC
        lfence_rdtsc    Lfence synchronizes RDTSC
        11ap    Bad local APIC aka 11AP
        nopl    The NOPL (0F 1F) instructions
        amdc1e  AMD C1E detected
        xtopology       cpu topology enum extensions
        tsc_reliable    TSC is known to be reliable


Virtualization flags:
	tpr_shadow	Intel TPR Shadow 
	vnmi	Intel Virtual NMI 
	flexpriority	Intel FlexPriority 
	ept	Intel Extended Page Table 
	vpid	Intel Virtual Processor ID 


Other features:
	cxmmx	Cyrix MMX extensions 
	k6_mtrr	AMD K6 nonstandard MTRRs 
	cyrix_arr	Cyrix ARRs (= MTRRs) 
	centaur_mcr	Centaur MCRs (= MTRRs) 
	p2_flush_bug	Need to flush the cache in P2 area 
	mmu_page_assoc	SH3: TLB way selection bit support 
	dsp	SH-DSP: DSP support 
	perf_counter	Hardware performance counters 
	ptea	PTEA register 
	llsc	movli.l/movco.l 
	l2_cache	Secondary cache / URAM 
	op32	32-bit instruction support 


Transmeta-defined CPU features:
        recovery        CPU in recovery mode
        longrun Longrun power control
        lrti    LongRun table interfac


Auxiliary flags:
	ida	Intel Dynamic Acceleration 


VIA/Cyrix/Centaur-defined CPU features:
	xstore	"rng" RNG present (xstore) 
	xstore_en	"rng_en" RNG enabled 
	xcrypt	"ace" on-CPU crypto (xcrypt) 
	xcrypt_en	"ace_en" on-CPU crypto enabled 
	ace2	Advanced Cryptography Engine v2 
	ace2_en	ACE v2 enabled 
	phe	PadLock Hash Engine 
	phe_en	PHE enabled 
	pmm	PadLock Montgomery Multiplier 
	pmm_en	PMM enabled 


```

Now that, my friend, is too much information. :)

Regards
Iain

---

### Post by ssdt on 2009-08-05
Thank you all. I found out that my system is a 32 bit desktop. Thank you for helping me out.

---

