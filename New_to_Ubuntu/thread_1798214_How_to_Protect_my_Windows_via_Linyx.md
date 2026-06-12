---
title: "How to Protect my Windows via Linyx ?"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by Linyx on 2011-07-06
Currently i have Ubuntu Lucid and i had Installed both windows(7 & Xp) and i have virus in My drive, i have removed that Virus via Linux but it Appear again and it has **Spoiled** my both **Windows**.Thanks GOD! Viruses has No Effect on Linux.

How can i remove that virus Permanently within Linux..?? I Don't want to Use Anti-Virus(within windows) Coz it will also Effect my Data...

Any help will be Appreciated,

---

### Post by Perfect Storm on 2011-07-06
Which one did you use?

Tried Avast? [http://www.avast.com/linux-home-edition#tab4](http://www.avast.com/linux-home-edition#tab4)
F-Prot: [http://www.f-prot.com/products/home_use/linux/](http://www.f-prot.com/products/home_use/linux/)

---

### Post by Linyx on 2011-07-06
> **Artificial Intelligence said:**
> Which one did you use?

Tried Avast? [http://www.avast.com/linux-home-edition#tab4](http://www.avast.com/linux-home-edition#tab4)
F-Prot: [http://www.f-prot.com/products/home_use/linux/](http://www.f-prot.com/products/home_use/linux/)

Thanks 4 Reply,

I haven't use any one of them yet, now i'm Downloading avast-Home-Edition for linux, i will Scan it and will post back...

---

### Post by Jonny87 on 2011-07-06
> **Linyx said:**
> Currently i have Ubuntu Lucid and i had Installed both windows(7 & Xp) and i have virus in My drive, i have removed that Virus via Linux but it Appear again and it has **Spoiled** my both **Windows**.Thanks GOD! Viruses has No Effect on Linux.

How can i remove that virus Permanently within Linux..?? I Don't want to Use Anti-Virus(within windows) Coz it will also Effect my Data...

Any help will be Appreciated,

> How can i remove that virus PermanentlyDelete your Windows partition. Though thats probably not an option.

Try installing clamAV into you Linux system and run regular scans on you windows partitions. 

> I Don't want to Use Anti-Virus(within windows) Coz it will also Effect my DataI'm not sure what you mean here by that it will effect your data. Usually your data should be fine. You could try something like Microsoft Security Essentials inside your windows partition. Malwarebytes is good for malware too.

---

### Post by Linyx on 2011-07-06
Their isn't avast in for x64...! i have donwload it and it says wrong Arcitecture, it requires i386

---

### Post by Jonny87 on 2011-07-06
> **Linyx said:**
> Their isn't avast in for x64...! i have donwload it and it says wrong Arcitecture, it requires i386

LOL i was curious about that to and tried it downloading and got the same thing. Avast is a good anti-virus too, shame that its only available on x86 machines.

---

### Post by jtarin on 2011-07-06
> **Linyx said:**
>  I Don't want to Use Anti-Virus(within windows) Coz it will also Effect my Data...

Any help will be Appreciated,Please educate me on how running an anti-virus program within windows will affect your data?????

---

### Post by Perfect Storm on 2011-07-06
You can easely use it on 64-bit as well.

Download the file to your Desktop.

```
sudo apt-get install ia32-libs build-essential dpkg-dev fakeroot
cd ~/Desktop
mkdir avast
dpkg-deb --extract avast4workstation_1.3.0-2_i386.deb avast
dpkg-deb --control avast4workstation_1.3.0-2_i386.deb avast/DEBIAN
gedit avast/DEBIAN/control
```

Under Architecture: change i386 to amd64

```
dpkg --build avast
```
Now you have a package you can install, though it stills rquire 32libs (which you have installed earlier in this guide)



If you get invalid argument when starting avast, do this when you want to run avast:
```
sudo sysctl -w kernel.shmmax=128000000
kernel.shmmax = 128000000
```

---

### Post by Linyx on 2011-07-06
> **jtarin said:**
> Please educate me on how running an anti-virus program within windows will affect your data?????

On my XP windows, Sometimes when i had Run an Anti-Virus, it Effect some of my backup, Like it Sometimes  mess up my setups that won't run after a scan, and sometimes it also effect the speed.

Sorry 4 my bad English

---

### Post by jtarin on 2011-07-06
> **Linyx said:**
> On my XP windows, Sometimes when i had Run an Anti-Virus, it Effect some of my backup, Like it Sometimes  mess up my setups that won't run after a scan, and sometimes it also effect the speed.

Sorry 4 my bad EnglishI've always been able to configure my anti-virus to ignore certain folders. Sorry for my bad English too.:P

---

### Post by Linyx on 2011-07-06
Thanks to all, Its DOne :P

---

### Post by mastablasta on 2011-07-06
> **Jonny87 said:**
> LOL i was curious about that to and tried it downloading and got the same thing. Avast is a good anti-virus too, shame that its only available on x86 machines.
 
 
heh so much for every software is now 64 bit. and 64 bit works perfectly. well it seem good command of command line is needed to get certian software run there.

---

