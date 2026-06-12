---
title: "Virtual Box - Can't install 64-bit Vista?"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-01-11
I am trying to install Windows Vista using the recovery disks that came with my laptop on Virtual Box 3.1, but it goes to load and than says this cpu is not compatible with 64-bit mode. How can I get this to work?!?! I really want to install my copy of Windows Vista in some type of virtual-booting program. Please help me out.

---

### Post by sandyd on 2010-01-11
Your processor needs to have the intel VT capabilities to do this. They also need to be enabled in virtualbox (look in the area where it says how many cpus you want to use) If the checkboxes are greyed out, you either have no VT support or have not enabled it

---

### Post by UnknownFear on 2010-01-11
It is greyed out and enabled, but I don't understand why it won't work. I installed Vista fine a few weeks ago.

---

### Post by sandyd on 2010-01-11
> **UnknownFear said:**
> It is greyed out and enabled, but I don't understand why it won't work. I installed Vista fine a few weeks ago.
installed vista on where?
actual computer or virtualbox?
p.s. if its checked and greyed out, it means theirs no support for it. That is, even if its checked.

---

### Post by UnknownFear on 2010-01-11
Actual computer. That sucks! I really wanted to be able to virtualize Windows instead of booting into it :(

---

### Post by UnknownFear on 2010-01-11
I think this is weird as well, seeing as how my Ubuntu 9.10 version is a 64-bit version...

---

### Post by spillin_dylan on 2010-01-11
I had this exact problem, my Toshiba A300 lappy supposedly "supports" Intel VT, but in the BIOS, the option to enable it is greyed out, just like in Virtualbox.  Since then, I updated my BIOS to get better ACPI support, and the option to enable VT was completely removed from the BIOS setup screen.  So, I have to deal with Vista as a dual-boot, and can only try 32-bit Linuxes in Virtualbox now.  

Thank your computer manufacturer for custom tailoring each product to Microsoft's wants.  



[SIZE="1"]And:  Supposedly, if you're really a super-awesome-computer-hacking-IT-professional-code-ninja, there ARE apparently ways to "hack" your BIOS to enable the option to enable VT.  At the risk of turning your computer into a $1000 brick. [/SIZE]

---

### Post by UnknownFear on 2010-01-12
That sucks!!! Honestly, if I could sync my iPhone 3GS to Ubuntu, I would not install Windows. I don't want to install Windows!!!! :( :( :( :(!!!!!

---

