---
title: "shutting down"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by LB0308 on 2011-08-22
I recently installed ubuntu on a older laptop.  It is a Lenovo.  Not sure how old it is but windows vista was installed on it when i got it.  I replaced windows with ubuntu and everything was working great.  It only has 512 mb of ram and a 80gb hardrive.  But Im pretty sure thats good enough to run ubuntu.  Oh and it has a celeron processor that I think is 1.6ghz in speed.  Well I gave it to my brother to use and he tells me it is randomly shutting down.  He isn't doing any thing in particular when it happens.  Just shuts down prolly within 30-60 mins after powering it back up.  I realize this is not a very informative post but I was hoping someone could point me in the right direction.  And yes I am new to Ubuntu and Linux in general.  Anything to help is appreciated.  Only thing I could think of is the power supply jack on the laptop is in bad shape.  But I had it on for 5-6 hrs and it was fine.

---

### Post by magic8ball on 2011-08-22
By shutting down I assume that you mean it instantly shuts off (like all power taken away) vs Ubuntu going into some controlled shut-down or hibernation mode.  If it's going into some kind of controlled shut-down, you could check under System->Preferences->Power Management and make sure something isn't being initiated from there.

Otherwise, it sounds like more of a hardware problem than a software one.  Make sure that your brother is using it in a way that it's well ventilated (e.g. on a table and not his lap).  You might also have him look at the underside and make sure that the vents aren't dusty (he could vacuum them for good measure).  If it's shutting down when only on battery power, it could be that the old laptop's battery is pretty much bad.  If it's shutting down with the power adapter attached (and it's in rough shape), it could be that he's moving the laptop a bit when he's using it and causing a bad electrical connection.

Good Luck.

---

### Post by 123456789123456789123456 on 2011-08-23
another thing to add, check the temperature of the cpu.  if you go to the bios, most of them have a monitor to monitor the heat of the cpu, if it very hot, running close to 200 degrees, it could correspond to fan issue.  If the cpu gets too hot, to reduce damage to the cpu, it will tell the power supply to terminate all power, and the computer in turn turns off.  also if this is the issue, if you try to turn the computer back on the second after it turns off, it will not turn on, the cpu will not allow the system to power on, until it coos off enough.

---

### Post by kyletstrand on 2011-08-23
Ick, that's never a good situation.  I had this happening on an old laptop of mine and it was because the fan wasn't working to par.  I replaced the fan and it improved, but would still occasionally shut down after.  I got a new laptop and took that one apart and my processor was melted slightly.  So I cringe when I see that kind of stuff on the forums.

Also, I think the recommended ram for ubuntu is 1GB, but should run on 512mb. If you are noticing some issues, try Xubuntu or Lubuntu as they are more lightweight and require less from your PC.

---

### Post by sidzen on 2011-08-23
Get [Lubuntu 10.04]("http://phillw.net/lubuntu-10.04.iso")  for two reasons -- beginning with Meerkat, 'buntus no longer support older CPUs like yours; and with 512MB RAM, performance with Gnome as configured in ubuntu will suck.

Otherwise, go with something like Lucid [Puppy 5.2.8]("ftp://distro.ibiblio.org/puppylinux/puppy-5.2.8/") and use a USB stick to save config files before logout.

Best wishes to you and your bro!

---

### Post by stefangr1 on 2011-08-23
> **sidzen said:**
> Get [Lubuntu 10.04]("http://phillw.net/lubuntu-10.04.iso")  for two reasons -- beginning with Meerkat, 'buntus no longer support older CPUs like yours; and with 512MB RAM, performance with Gnome as configured in ubuntu will suck.

Otherwise, go with something like Lucid [Puppy 5.2.8]("ftp://distro.ibiblio.org/puppylinux/puppy-5.2.8/") and use a USB stick to save config files before logout.

Best wishes to you and your bro!


The minimum system requirements needed to install Ubuntu 11.04 desktop can be found [here](https://help.ubuntu.com/community/Installation/SystemRequirements). Your system is not too old to run Ubuntu. Though you could indeed consider to switch to a more lightwight version, it isn't strictly neccesary.

Having that said, I'm not sure your problems are related to software. Software issues generally result in the system stalling, error messages, etc.. A complete shutdown (where the system really turns off to the extent that even the fans are no longer running) is almost always hardware related. It could be that the laptop becomes too hot, and is shut down to prevent further overheating.

Installing a lightweight version might help a little though, as average system utilization will be lower such that the system generates less heat.

What I would personally also try if I were in your situation (but I wouldn't neccesarily recommend this as you could easily damage the computer during the process) is open it up and vacuum clean it from the inside. If a lot of dust has accumulated during the years, that gets things pretty well isolated. However, before you start opening up your system it's probably better to do some more troubleshooting first such that other options are ruled out.

---

### Post by sidzen on 2011-08-23
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)
"Linux kernel 2.6.35
RC includes the 2.6.35-22.33 kernel which is based on the 2.6.35.4 Upstream stable kernel.  . . . With 10.10 we have also dropped support for i586 and lower processors, as well as i686 processors without cmov support."

---

### Post by stefangr1 on 2011-08-23
> **sidzen said:**
> [https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)
"Linux kernel 2.6.35
RC includes the 2.6.35-22.33 kernel which is based on the 2.6.35.4 Upstream stable kernel.  . . . With 10.10 we have also dropped support for i586 and lower processors, as well as i686 processors without cmov support."

I understand what you're trying to say, but the thing is i586 refers to (mostly) the Pentium-I processor line, while the first i686 processor was the Pentium II processor. So while the release notes you mention are really bad news for all those Pentium I owners desparately wanting to run 11.04, it doesn't apply to the OP.

---

### Post by sidzen on 2011-08-23
While the Dothan family of Mobile processors has cmov support (see below) . . .
-------------------------------------------------------------------------------
From
[http://lists.debian.org/debian-laptop/2005/04/msg00216.html](http://lists.debian.org/debian-laptop/2005/04/msg00216.html)
Radoslav Kolev says, . . . 
Here's the output of 'cat /proc/cpuinfo':
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Celeron(R) M processor         1.30GHz
stepping        : 6
cpu MHz         : 162.168
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 apic mtrr pge mca
**cmov** pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe
bogomips        : 2555.90
-------------------------------------------------------------------------------
why should the OP prefer a distro that bogs down his limited resources laptop 
to one that performs quickly on his machine?

And while yes, I was slightly amiss on the technical definitions,  I learned 
something in the process but still stand by my recommendation of lubuntu (to 
which I now add [Peppermint One]("http://peppermintos.com") or [Mint-11-LXDE]("http://blog.linuxmint.com/?p=1802")).

---

### Post by LB0308 on 2011-08-28
Sorry for getting back to you guys so late.  But I would like to say thank you to all of you for your posts.  I wasn't expecting so many responses lol.  I'm happy I became a member.  I will take all responses and apply.  Once again thank you and I will update my progress!

---

### Post by LB0308 on 2011-08-28
And yes I do know other than using a antistatic vacuum you should only use compressed air to clean the inside of your computer weather it be a laptop or desktop.

---

