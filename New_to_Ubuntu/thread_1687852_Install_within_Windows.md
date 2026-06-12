---
title: "Install within Windows"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by fdhealy4 on 2011-02-14
There use to be a way to install Ubuntu within Windows and run Ubuntu just like any other windows app. I don't see that option anymore. Please advise if it still exist or not and if so a link to the download.

Thanks Dale):P

---

### Post by sydbat on 2011-02-14
> **fdhealy4 said:**
> There use to be a way to install Ubuntu within Windows and run Ubuntu just like any other windows app. I don't see that option anymore. Please advise if it still exist or not and if so a link to the download.

Thanks Dale):PWhile in Windows, pop the Ubuntu CD in and let it "auto start". It should give you the option of installing via 'WUBI'.

If it does not "auto start", go into your 'Computer' and find the DVD / CD drive and open the Ubuntu CD from there.

---

### Post by Trooper_Max on 2011-02-14
That option is called Wubi (Windows UBuntu Installer), and it is already included in the ISO you download!

I usually just use 7-zip to extract the ISO to a folder. You'll see wubi.exe in that folder. Then I move the ISO to that folder so that it is in the same directory as wubi (this way it won't try to download it again). Then I run wubi and install it. Hope that helps!

For more info check here:
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

~Troop

---

### Post by Frogs Hair on 2011-02-14
Ubuntu won't start from windows . but you can choose it at boot.

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by NightwishFan on 2011-02-14
Here is a link to the download! :)
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

Edit: Oh I see, nvm, was mistaken. You probably should use something such as Virtualbox for that purpose. I remember another application that did this, but I do not recall the name.

Virtualbox: [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by fdhealy4 on 2011-02-14
If I use virtualbox to run Ubuntu within Windows am I isolated from windows keyloggers and other win malware tracking my actions?

---

### Post by NightwishFan on 2011-02-14
I think in some cases possible, but no not entirely, as Windows is still running.

---

### Post by sydbat on 2011-02-14
> **fdhealy4 said:**
> If I use virtualbox to run Ubuntu within Windows am I isolated from windows keyloggers and other win malware tracking my actions?No. You will have to do all the things you would normally do when running Windows, like [installing A/V]("http://www.microsoft.com/security_essentials/"), enabling the firewall, etc. Ubuntu will be effected by anything that effects Windows.

---

### Post by fdhealy4 on 2011-02-14
Thanks Everyone,

I'll just get another laptop dedicated to Ubuntu.

Dale:p

---

### Post by linuxman94 on 2011-02-14
@sydbat 

Ubuntu is not affected by windows malware or viruses even though it is running in windows.  Therefore it is not necessary to install anti virus in ubuntu.

---

### Post by sydbat on 2011-02-15
> **linuxman94 said:**
> @sydbat 

Ubuntu is not affected by windows malware or viruses even though it is running in windows.  Therefore it is not necessary to install anti virus in ubuntu.What I wrote concerned putting A/V etc on Windows. 

The OP was talking about a wubi install, then asked if running Ubuntu in a VM would eliminate Windows malware interacting with Ubuntu. It does not. If Windows picks up malware, it will negatively effect a VM install. 

Regardless of what OS the host is, if the file system becomes corrupted (for whatever reason), it will destroy the VM. This is because the VM is dependant on the host system...and if something happens to the host system, it **will** bork the VM (which is what a wubi install is).

---

### Post by Paqman on 2011-02-15
> **sydbat said:**
> 
Regardless of what OS the host is, if the file system becomes corrupted (for whatever reason), it will destroy the VM. This is because the VM is dependant on the host system...and if something happens to the host system, it **will** bork the VM (which is what a wubi install is).

Wubi isn't a VM. It runs entirely separately from Windows and accesses the hardware directly, it just does it from a loopmounted virtual partition. You are quite correct that it relies on the integrity of the filesystem it resides on though.

---

### Post by sydbat on 2011-02-15
> **Paqman said:**
> Wubi isn't a VM. It runs entirely separately from Windows and accesses the hardware directly, it just does it from a loopmounted virtual partition. You are quite correct that it relies on the integrity of the filesystem it resides on though.True enough, because it can boot separately from the host (whereas a VM can only boot while the host is running).

Semantics...):P

---

### Post by Paqman on 2011-02-15
> **sydbat said:**
> True enough, because it can boot separately from the host (whereas a VM can only boot while the host is running).

Semantics...):P

It's more about the fact that VMs operate on an abstracted layer of virtual hardware. They don't control the hardware themselves. Wubi is just a clever piece of on-disk trickery done to avoid repartitioning, it doesn't have anything in common with VMs at all. It's essentially a dual-boot.

---

### Post by sydbat on 2011-02-15
> **Paqman said:**
> It's more about the fact that VMs operate on an abstracted layer of virtual hardware. They don't control the hardware themselves. Wubi is just a clever piece of on-disk trickery done to avoid repartitioning, it doesn't have anything in common with VMs at all. It's essentially a dual-boot.You are correct. Did a little more reading and learned something new today (which is what should happen). Thanks.

---

