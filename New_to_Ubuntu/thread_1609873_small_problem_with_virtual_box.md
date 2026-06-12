---
title: "small problem with virtual box"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2010-10-30
i have tried to install virtual box 64 bit for ubuntu and it tells me the im missing the driver libqtcore4  so i went into the package manager and installed it, and it keeps saying that Error: Dependency is not satisfiable: libqtcore4 (>= 4:4.7.0~beta1)

any tips

---

### Post by tajiknomi on 2010-10-31
[SIZE=2][I]Go to synaptic...then **right-click** on the virtual Box which you had installed and go to Properties..Their you will see the list of **Dependencies**,check it one-by-one that these dependences are installed or not...?

Also see **Marked recommended** for virtual box by right clicking in it icon in synaptic...
[/I][/SIZE]

---

### Post by Omnomnom on 2010-10-31
Are you 64 bit or 32? Just wondering. As it's common sense that 64 bit applications will not work on a 32 bit machine.

---

### Post by pyrofreak99 on 2010-10-31
my system is a 64 bit   but its not letting me install virual box  beause of the missing dependency  and i installed the dependency  but it wont let me install the program

---

### Post by ario on 2010-10-31
> **pyrofreak99 said:**
> i have tried to install virtual box 64 bit for ubuntu and it tells me the im missing the driver libqtcore4  so i went into the package manager and installed it, and it keeps saying that Error: Dependency is not satisfiable: libqtcore4 (>= 4:4.7.0~beta1)

any tips

It's hard to judge this problem as a dependency problem in synaptic system. It just tells you to install libqtcore4. But pay attention that version of libqtcore4 version must be more than 4:4.7.0~beta1. It must be for example 4:4.8.2 . Check if you installed new version. Click reload button on synaptic and after a while click mark all upgrades, then apply button, and finally try installing of Virtual Box again.

---

### Post by snowpine on 2010-10-31
Where are you installing VirtualBox from? If you install it from the Ubuntu repositories using the Ubuntu Software Center or Synaptic Package Manager, all dependencies should be automagically installed for you. :)

---

### Post by pyrofreak99 on 2010-10-31
well i checked it and i have got libqtcore4   4:4.6.2-oubuntu5.1     i have hit the reload button and checked for upgrades but it stays the same

---

### Post by psycho5 on 2010-10-31
I had the same problem, if you're using the latest kernel, then virtualbox from ubuntu won't install, you can go to oracle's website and download virtualbox for ubuntu maverick from there, they have deb. packages. Enjoy =D

---

### Post by pyrofreak99 on 2010-10-31
thats the thing i have downloaded
 it via deb file to make it easier but it stills tells me i need that dependency to install it

---

### Post by snowpine on 2010-10-31
It sounds like you are trying to install the 10.10 Maverick version on a 10.04 Lucid system. :)

To repeat my advice from above, if you install from the Ubuntu repos using the Software Center, you don't have to worry about dependencies.

---

### Post by pyrofreak99 on 2010-10-31
wow that actually helped  thanks abunch guys i thought i was running 10.10

---

### Post by GrouchyGaijin on 2010-10-31
Just a note - if you want to use USB I believe that you have to install the version of Virtual Box from the website not via Synaptic.

---

### Post by hantms on 2010-12-14
No it doesn't.

I run plain jane 32 bit Ubuntu Maverick, and downloaded the Virtualbox .deb.

It wants libqtcore4 >= 4:4.7.0~beta1.

Ubuntu repository has 4:4.6.2-0ubuntu5.1 , and indicates this is the latest avalable version.

So...  Ubuntu Maverick users cannot install current Virtualbox versions.  Until a more recent version of libqt4 is made available.

Dependency hell seems back, due to updates not making it into the repositories.

---

### Post by cencithomas on 2011-01-23
^This. This is exactly the problem I'm having. 32-bit 10.10, VBox won't install because it wants libqtcore >=4:4.7.0~beta 1, my only option from Synaptic is 4:4.6.2-0ubuntu5.1. Any ideas where I can go to get the latest libqtcore4 package?

---

### Post by TransitMan on 2011-01-23
> **cencithomas said:**
> ^This. This is exactly the problem I'm having. 32-bit 10.10, VBox won't install because it wants libqtcore >=4:4.7.0~beta 1, my only option from Synaptic is 4:4.6.2-0ubuntu5.1. Any ideas where I can go to get the latest libqtcore4 package?

Until the updated libqtcore4 hits the repos, why not try to install from VirtualBox the 32-bit version for Ubuntu 10.04. 
I realize you all may want the latest and greatest, but sometimes rolling back on version helps until the newer one catches up with the needs of the program.

---

### Post by cencithomas on 2011-01-23
Will that work? Sure I'll try it, not so interested in 'latest/greatest' as in something that actually works ;) will let you know how it goes...

---

### Post by TransitMan on 2011-01-23
> **cencithomas said:**
> Will that work? Sure I'll try it, not so interested in 'latest/greatest' as in something that actually works ;) will let you know how it goes...

Will it work, don't know. 
I haven't run into this problem before, but if all else fails, fall back 1 version until the repos catch up to what is needed for Virtual Box.

---

