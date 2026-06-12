---
title: "Bits? Aren't those units of data?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by icyest on 2008-12-17
While trying to download the program [HandBreak]("http://handbrake.fr/?article=download"), I did not know what to choose out of the 4 choices. 

I keep hearing this stuff about 64bit and 32bit Operating Systems. I thought bits were a unit of data? Don't they also have something to do with sound and video? It's so poorly defined, used everywhere, and It makes people like me frown :[


How would I even know what bit I have? The Systems-->About Ubuntu reveals nothing.

---

### Post by jerome1232 on 2008-12-17
Yes a bit is the smallest unit of data, it's either a 1 or 0 and 8 of them make a byte (10011101 would be a byte of data); but as far as whether your operating system is 32 bit or 64 bit (meaning the proccessor handles 32 bit chunks of data or 64 bit chunks of data) can be found with this command.

edit: To use this command open a terminal; Applications -> Accessories -> Terminal

```
uname -m
```

if it comes back as i386, i486, i586, or i686 then you are running 32 bit

if it comes back as x86_64 you are running 64 bit.

Hope that helps.

edit: When your talking about audio video your probably thinking of the quality, for example an audio song that is 128kbps means that it sends 128 kilobytes of data per second, or 128,000 bytes of data per second.

---

### Post by Poyntz on 2008-12-17
64bit processors have wider memory addresses than the 32bit. Consequently the processor can directly access more memory and should consequently be faster.

---

### Post by icyest on 2008-12-17
The Ubuntu website states that 64bit "May provide additional capabilities to computers that are able to use 64bit software"

How do I know if a computer is capable of running 64bit?

---

### Post by jerome1232 on 2008-12-17
All modern Desktop Processors are capable of running a 64 bit OS.

Really the advantages are that you can have >4 GB's of RAM and the proccessor is faster at number crunching (audio/video encoding, 3d modeling, compiling, gaming)

For the most part the average user won't notice a diffrence though.

Do you know what kind of processor you have? If you could post the output of this command we can figure out if your proccessor is 64 bit or not.

```
cat /proc/cpuinfo
```

---

### Post by noerrorsfound on 2008-12-17
> **icyest said:**
> The Ubuntu website states that 64bit "May provide additional capabilities to computers that are able to use 64bit software"

How do I know if a computer is capable of running 64bit?
For a computer to run 64-bit software it's got to be running on a 64-bit operating system, which means it's also got to have a 64-bit processor. A 64-bit processor can also run a 32-bit operating system, but then it'll only be able to run 32-bit programs.

If you want to find out if a computer has a 64-bit processor, you can find out the model number of the computer from somewhere on its case and type that into Google. From there you can find a website (like the manufacturer's website) that will tell you what type of hardware the computer has. As a last resort you could always open it up and see what's printed on the processor, but with a pre-built system that shouldn't be necessary.

---

### Post by mrbiggbrain on 2008-12-17
> **jerome1232 said:**
> All modern Desktop Processors are capable of running a 64 bit OS.

Really the advantages are that you can have >4 GB's of RAM and the proccessor is faster at number crunching (audio/video encoding, 3d modeling, compiling, gaming)

For the most part the average user won't notice a diffrence though.

Do you know what kind of processor you have? If you could post the output of this command we can figure out if your proccessor is 64 bit or not.

```
cat /proc/cpuinfo
```

not to say jerome is wrong, but trying to say 64-bit is only about memory and speed is like saying a light bulb is only about lights... it produces heat, radiation, consumes power, etc. though light is the main see-able item of a light bulb it inst all of it

64-bit does allow more then 4 g, but it also cleans up a lot of overused address space. take a pc that has 4GB of ram exactly, on 32bit you get about 3.2GB of ram, though the theoretical limit of 32-bit is 4GB because other things use the address space (hardware, ROM, etc) you don't get as much address space...on 64-bit, 4GB = 4GB

BUT! becuse every address takes up 64-bits versus 32-bits the overhead is doubled! so under theory a program could add alot to adress space (32-bit adress + 8-bit int = 40-bit, 64-bit address + 8-bit int = 72-bit almost 100% more overhead!

this is not to say that 64-bit is bad, i use it,  it is indeed more powerful, gives you full access to the speed of your processor, but will any way you put it, take more ram! if you have a low ram, ram dependent system, stay 32-bit, if you have a decent amount of ram, and want to unlock your processor, go 64-bit.

---

### Post by jerome1232 on 2008-12-17
> **mrbiggbrain said:**
> not to say jerome is wrong, but trying to say 64-bit is only about memory and speed is like saying a light bulb is only about lights... it produces heat, radiation, consumes power, etc. though light is the main see-able item of a light bulb it inst all of it

64-bit does allow more then 4 g, but it also cleans up a lot of overused address space. take a pc that has 4GB of ram exactly, on 32bit you get about 3.2GB of ram, though the theoretical limit of 32-bit is 4GB because other things use the address space (hardware, ROM, etc) you don't get as much address space...on 64-bit, 4GB = 4GB

BUT! becuse every address takes up 64-bits versus 32-bits the overhead is doubled! so under theory a program could add alot to adress space (32-bit adress + 8-bit int = 40-bit, 64-bit address + 8-bit int = 72-bit almost 100% more overhead!

this is not to say that 64-bit is bad, i use it,  it is indeed more powerful, gives you full access to the speed of your processor, but will any way you put it, take more ram! if you have a low ram, ram dependent system, stay 32-bit, if you have a decent amount of ram, and want to unlock your processor, go 64-bit.

Very true, if you are in a low ram situation don't go 64 bit, I guess I neglected to mention that. There's actually a sticky for this discussion though :)

[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428) We've pretty much hit on everything that the sticky does though.

---

### Post by icyest on 2008-12-17
> **jerome1232 said:**
> All modern Desktop Processors are capable of running a 64 bit OS.

Really the advantages are that you can have >4 GB's of RAM and the proccessor is faster at number crunching (audio/video encoding, 3d modeling, compiling, gaming)

For the most part the average user won't notice a diffrence though.

Do you know what kind of processor you have? If you could post the output of this command we can figure out if your proccessor is 64 bit or not.

```
cat /proc/cpuinfo
```

As requested:
```
t@t:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2600  @ 2.16GHz
stepping	: 8
cpu MHz		: 1000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr
bogomips	: 4331.34
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2600  @ 2.16GHz
stepping	: 8
cpu MHz		: 2167.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr
bogomips	: 4327.88
clflush size	: 64

```

Thank you so much for doing this.

---

### Post by cariboo on 2008-12-17
From the info you provided, it looks like you have a dual core 32bit cpu. I would suggest haveing a look at your bios settings, as one core is running at 1000Mhz, while ther other core is running at 2167Mhz.

JIm

---

### Post by icyest on 2008-12-17
> **cariboo907 said:**
> From the info you provided, it looks like you have a dual core 32bit cpu. I would suggest haveing a look at your bios settings, as one core is running at 1000Mhz, while ther other core is running at 2167Mhz.

JIm

What exactly is a bios? and what do those thousand numbers mean?

---

### Post by The Cog on 2008-12-17
The BIOS is the setup in the computer that's there on the motherboard even before the operating system loads from hard disk.

The figure in MHz is the sped the CPU is running at. I don't think the CPU can run the 2 halves at different speeds, so I guess that maybe the OS automatically put the clock rate up because it was busy, right between when the lshw program was measuring the speed of the two cores. I don't think you need to worry about these numbers. If you want faster speeds, you buy a faster computer is what it boils down to.

---

### Post by mrbiggbrain on 2008-12-17
yeah i have a 1.8ghz santa rosa, and it reads 800mhz most of the time, sometimes one core is just busy and is given a speed boost, as long as none of the numbers go above the clock speed of your processor your fine. (well unless you run a core i7 and thats just a whole diffrent beast altogether)

---

