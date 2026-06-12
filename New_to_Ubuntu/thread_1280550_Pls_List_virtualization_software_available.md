---
title: "Pls List virtualization software available"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-10-02
I am using virtual box right now to work on XP as virtual. But it is ultimate slow because it does not use CPU resource available efficiently. I have dual core processor. But when i start using XP, one of the two core become 90-100% loaded. 

So please suggest me some good software for installing virtual system which doesn't slow down guest OS or make burden on core and make use of my dual core efficiently, I will switch to it.

Thanks...

---

### Post by HarrisonNapper on 2009-10-02
I use VBox on a dual core processor and have never had a problem. Have you tried defining your CPU scaling? Another virtualization tool is VMWare, but I'm not sure how that one works on *nix since I've never used it. Also, you can always search in synaptic for this kind of thing.

---

### Post by eshant_engineer on 2009-10-02
CPU scaling!!! How to do that?

---

### Post by HarrisonNapper on 2009-10-02
It's an applet on your gnome panel.

---

### Post by BQAggie2006 on 2009-10-02
Also, you need to make sure your CPU has hardware virtualization extensions or else it won't matter what VM program you use or if you have dual-core.

---

### Post by HarrisonNapper on 2009-10-02
Good point, BQ!

Quick how-to on that:
Boot up the computer, enter your BIOS setup menu, and that's where you can enable virtualization for your CPU. Happy *nixing!

---

### Post by eshant_engineer on 2009-10-03
I have Intel 946GZ Mobo, i checked it's bios but i couldn't find any such option where i can enable it. Please can u guide me in this too.....

(I have 64 bit configured system and using 64 bit OS) So i suppose i can virtualize my CPU!

---

### Post by BQAggie2006 on 2009-10-03
> I have Intel 946GZ Mobo, i checked it's bios but i couldn't find any such option where i can enable it. Please can u guide me in this too.....

This procedure varies by motherboard so it's probably a good idea for you to find your MOBO manual and see if it's a possibility.

> (I have 64 bit configured system and using 64 bit OS) So i suppose i can virtualize my CPU! 	

Not necessarily true. AMD and Intel released their 64-bit CPUs a few years before they released CPUs with hardware virtualization extensions.

---

### Post by inobe on 2009-10-03
hold on, there ar two different versions of virtualbox, you have ose and proprietary, which one ?

vmware is also one you could try

---

### Post by 3rdalbum on 2009-10-04
Did you have a look at the Virtualbox documentation? I think there might be something in there about this; I recall reading something about high CPU use in XP.

---

### Post by inobe on 2009-10-04
> **3rdalbum said:**
> Did you have a look at the Virtualbox documentation? I think there might be something in there about this; I recall reading something about high CPU use in XP.


i heard the ose version with a vista guest has that same issue.

---

### Post by advocate 21 on 2009-10-04
i use wine. you can use gnome-looks.com for the theme to make it feel like an xp, then use wine for the programs. ive never used VBox.

---

### Post by praveesh on 2009-10-04
It's better you contact your processor manufacturer to know whether your processor support intel vt(hardware assisted virtualisation) . I have a core2duo E4600, but it does not support intel vt .

---

### Post by praveesh on 2009-10-04
Open a terminal and run this command :

```
egrep '(vmx|svm)' --color=always /proc/cpuinfo
```

If you get an output(no matter whatever it is) your CPU supports hardware assisted virtualisation  and you need to enable it in your BIOS.

Otherwise your CPU does not support hardware assisted virtualisation

---

### Post by eshant_engineer on 2009-10-05
This is the o/p
```
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow

```

---

### Post by HarrisonNapper on 2009-10-06
> **3rdalbum said:**
> Did you have a look at the Virtualbox documentation? I think there might be something in there about this; I recall reading something about high CPU use in XP.

Yeah, I believe it says that if you're running a 32-bit guest on a 64-bit host, you have to enable virtualization in your bios.

---

