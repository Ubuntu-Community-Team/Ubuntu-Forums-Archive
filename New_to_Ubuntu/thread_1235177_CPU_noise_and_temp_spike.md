---
title: "CPU noise and temp spike"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by stalkier on 2009-08-08
OK here is the skinny on this issue. I have a ASUS AS8-X motherboard (socket 939), AMD AthlonX2 3800+ CPU (not over-clocked). I have a MASSIVE CPU cooler on the CPU. It is running fine with no fan issues etc. I have been having some high pitched sound coming from the CPU. At first I thought it was from the hard drive but this is not the case. The sound is defiantly coming from the CPU. I am using a temp monitoring app enabled on the taskbar (I am guessing default app). When the sound starts I noticed the CORE0 temp going from 29C to 31C. Not much of a jump but as soon as the sound stops the temp drops back down. CORE1 remains at around 21-22C. Is there any solution to this. I have noticed a lot of people having this issue all the way back to 2005. All related to ASUS and AMD CPUs. No solutions though.

---

### Post by 3rdalbum on 2009-08-08
It's probably one of the components around the socket that is making that noise when your CPU starts drawing more power. I don't think there would be a solution to this.

---

### Post by stalkier on 2009-08-08
Would it be beneficial to use sound damping material in the case? I am willing to spend a little bit of money. (under $50US) or maybe a little more over time. Also why would it only make this sound using Ubuntu? I only know of it making this sound in Linux OS not Windows. (could be a coincidence)  

What is a safe or ideal temp for CPU, HDD, and Video card?

CPU: AMD socket 939 Athlon 3800+ (not overclocked)(CORE0 28C CORE1 21C)
HDD: Western Digital Blue Caviar 320GB SATA3 (43C)
VID: XFX GeForce 8500GT Silent model (65C)

---

### Post by shae on 2009-08-09
Perhaps try disabling CPU scaling or setting it to performance?  Have you tried disabling ACPI?

Those temps look fine

---

### Post by stalkier on 2009-08-09
> **shae said:**
> Perhaps try disabling CPU scaling or setting it to performance?  Have you tried disabling ACPI?

Those temps look fine

How do I do these things? Sorry I have never done it before. Thanks for the help.

---

### Post by halitech on 2009-08-09
have you thought that maybe its the bearings in the fan causing the noise? Thats where I'd look first. Maybe when it starts to warm up the fan starts to spin faster causing the noise.

---

### Post by XCan on 2009-08-09
I would say that the sound you are hearing is coming from the voltage/current regulators around the socket. Typically current changes can cause coils to vibrate and sudden charge/discharge of the condensators can similarily cause noise (dunno the exact origin though).

---

### Post by shae on 2009-08-09
> **XCan said:**
> I would say that the sound you are hearing is coming from the voltage/current regulators around the socket. Typically current changes can cause coils to vibrate and sudden charge/discharge of the condensators can similarily cause noise (dunno the exact origin though).

This is along the lines of what I am thinking the problem could be, but it does not occur in windows according to OP so I was suggesting things that might be software related.

If it is indeed a hardware problem, then Motherboard replacement might be the only option.

---

### Post by mrgreggie on 2009-08-09
On my parents system (powered by an X2 3800), the chirping actually comes from the PC speaker when the chip is overheating (there is a temperature monitor in their BIOS under "PC Health").  Look in the BIOS and see if there is an alarm set up  If it is an alarm, try some compressed air in the case or consider raising the alert temerature.

Talk about coincidence, my mom just asked me about it for the first time today.

---

### Post by stalkier on 2009-08-09
Thanks for all the input guys. I will do a full investigation on Wednesday (my day off). I will go thru everything I can think of plus everything you posted and I will post back results.

---

### Post by stalkier on 2009-09-02
Noise was PSU. Not sure if it is going bad or not. I guess we will find out soon enough.

---

