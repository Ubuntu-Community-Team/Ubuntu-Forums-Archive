---
title: "8 and 16 bit Windows Applications"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by j_sop@hotmail.com on 2009-06-18
I love Linux OS and have recently settled on Ubuntu. I've worked over just about every hurdle on my own but now I've hit a wall. Wine is unable to run some of my most beloved windows applications. I've tried VirtualBox and VMware with XP but neither support the applications because they are 8 and 16 bit. Is there any alternative or will I have to return to XP.

P.S. I don't want to deal with dual booting.

Thanks for your time!

EDIT: Check second post for more thorough description.

---

### Post by LewRockwell on 2009-06-18
you just need to scrounge up an old machine for those games

not that there is anything wrong or difficult about dual/triple/quad/etc/-booting

I have machines still running windoze 3.1

---

### Post by jerrrys on 2009-06-18
are these DOS programs?  there are dos emulator programs in synaptic package manager

dosbox and dosemu

---

### Post by Mike'sHardLinux on 2009-06-18
What application(s) are you trying to run? Generally, any application (I am not talking about realtime 3D stuff) that runs in XP should run in XP in a VM. 

If it doesn't run in a VM, why do you think it will run in XP at all?

By 8 and 16 bit, do you mean DOS applications? Those should have the same success being run in XP or in XP in a VM. But still, if that is what you are wanting to do, you can use DOSBox.

---

### Post by jerome1232 on 2009-06-18
I don't know about 8 bit but I know Win ME and lower support 16 bit applications. XP dropped support for 16 bit.

So my suggestion is to install Win95 or Win98 or WinMe inside a virtual machine.

---

### Post by j_sop@hotmail.com on 2009-06-18
Wow thank you all for such a quick response. The applications I am trying to run include Starcraft (Runs in Wine but would be nice if i could get it to run full screen in a virtualization) and a number of indie titles such as Soldexus and Flywrench. When trying to run Soldexus or Flywrench I'm prompted with a message saying that drawing surfaces could not be initiated due to requirements not being met on the graphics cards. Both VMware and Virtualbox's Guest addition display drivers don't meet the simple requirements and there are others on the respective softwares forums with the same problem as myself. I've tried running Virtualbox without the guest addition and it periodically crashes without the guest additions.

I love Ubuntu and have finally set my heart on it but if I can't run my independent 2d games I'd have to be forced to choose and indie gaming beats Ubuntu out. =[

Oh and I'm not positive these games are 8 and 16 bit, I'm just assuming on the basis that VirtualBox is prompting me to switch from 32 bit mode to 16 bit mode and warning that Virtualbox runs most efficiently in 16 bit. Also I'm positive these applications run in XP because I was running XP prior to Ubuntu and they worked fine.

Edit: Also my apologies for my possible ignorance of automatically labeling the games 8 and 16 bit although I do believe a majority of the games are 16 bit. Most are stand alone applications made by programs such as Game Maker or Adobe Flash.

P.S. As far as my knowledge goes and from what I've encountered the only hope I could imagine would be some kind of Virtualization program that supports running in a 16 bit mode, but I could be completely off with that.

EditEdit: The reason for me not wanting to dual boot is I enjoy quickly playing for 10 - 15 minutes in between my college classes and being forced to reboot and go through the hassle isn't worth it for me. I like things being centralized onto one OS.

Sorry for being so long-winded =P

---

### Post by presence1960 on 2009-06-18
I for one have never understood the "hassle of rebooting" argument, unless it is rebooting into Vista. How much of a hassle is 30-45 seconds? With jaunty the boot up process is super fast when you use ext 4 filesystem. I setup a dual boot of jaunty/Vista on a friends eMachine and his 9 & 10 year old sons noticed how fast jaunty boots.

Sometimes we can't have our cake and eat it too. If you love Ubuntu but still want those games you may ultimately have to dual boot. I know I wouldn't get rid of an OS for a couple games or even some software that I like. Unless that software was making me a million dollars. The choice is simple, dual boot and have both things you want!

---

### Post by wmcbrine on 2009-06-18
> **jerome1232 said:**
> XP dropped support for 16 bit.I don't think so... not unless you're talking about the 64-bit version. What is true, though, is that XP no longer depended on 16-bit code, as the 9x/ME branch did.

---

### Post by jerome1232 on 2009-06-18
Well maybe it was 8 bit but I know for a fact XP just dropped support for one or both (came with dropping msdos). 

Actually now that I'm thinking about it I am pretty sure it had a compatibility mode for 16 bit and or 8 bit that would work for some programs.

Doing a quick google search about xp and 16/8 bit confirms this for me. It uses a virtual dos emulation machine to run 16 bit applications.

On another note starcraft is most definitly 32 bit, unsure about the other apps you noted.

---

### Post by wmcbrine on 2009-06-20
XP uses a virtual machine* to run DOS apps, yes -- just like other versions of Windows. This should not be confused with 16-bit Windows apps.

What changed was that you couldn't boot into DOS, because XP was not built on top of DOS, as 9x/ME were. There were some really picky games that demanded that.

There is no such thing as an 8-bit app on x86.

* A VM86 session, that is -- mostly done in hardware. Used for DOS sessions in Windows since at least 3.1.

---

