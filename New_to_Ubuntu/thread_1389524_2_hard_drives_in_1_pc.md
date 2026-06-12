---
title: "2 hard drives in 1 pc"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by Marc St Louis on 2010-01-24
I am currently using windows on my work pc.  I have an old pc that I am not using anymore so I was thinking of removing its hd, formatting and installing it in my work pc then running ubuntu on it.  Can this be done?

---

### Post by jflaker on 2010-01-24
Yes...when you are asked where to install, choose the second disk...Careful, choose the wrong disk and you overwrite your win install

---

### Post by Marc St Louis on 2010-01-24
Ok.  When I boot up will I also be given the choice of which OS I want to load?

---

### Post by 73ckn797 on 2010-01-24
> **Marc St Louis said:**
> Ok.  When I boot up will I also be given the choice of which OS I want to load?


Yes you will.

You may want to install the drive, then once booted from the Ubuntu Installation disk and selecting the first menu option, go to System/Administration/ Gparted and format the drive. The install will also do this for you. At least you can view how Ubuntu reads the drive and you will know which one it is when the choice of which disk you want to install to is asked during the installation.

---

### Post by NCLI on 2010-01-24
Lastly, you will want to choose "Manual Partitioning" in the installer.

---

### Post by 73ckn797 on 2010-01-24
> **NCLI said:**
> Lastly, you will want to choose "Manual Partitioning" in the installer.

+1

A wise choice.

---

### Post by Marc St Louis on 2010-01-24
> **NCLI said:**
> Lastly, you will want to choose &quot;Manual Partitioning&quot; in the installer.

Why?

---

### Post by 73ckn797 on 2010-01-24
> **Marc St Louis said:**
> Why?

You are in control of the installation. Manually choosing the drive to install to will make certain that it is the one you want it to be installed on. It will only extend the installation time a little longer but that is a safe guard for you. Sometimes the installation will want to install to the same drive that the other OS is on. Read what is being communicated during the install.

Also understand that it will install the Grub boot loader. That will automatically add any other OS that you have installed so that once you reboot you will be given a menu selection of OS's to boot into.

Does this make sense?

---

### Post by Miljet on 2010-01-24
Do you know what type drives you are dealing with? Older computer used IDE drives that are connected with thin flat cables. Newer computers use SATA drives that use thinner round cables. They are not compatible.

You can sometimes install an IDE drive in a newer computer by conecting it to the same cable your DVD drive is on, if you only have one optical drive. But I have read numerous threads in this forum concerning boot problems caused by mixing drive types. Just understand what you are doing before diving in.

---

### Post by Marc St Louis on 2010-01-25
> **73ckn797 said:**
> You are in control of the installation. Manually choosing the drive to install to will make certain that it is the one you want it to be installed on. It will only extend the installation time a little longer but that is a safe guard for you. Sometimes the installation will want to install to the same drive that the other OS is on. Read what is being communicated during the install.

Also understand that it will install the Grub boot loader. That will automatically add any other OS that you have installed so that once you reboot you will be given a menu selection of OS's to boot into.

Does this make sense?

Yes it does and that is great.  It's exactly what I was looking for

---

### Post by mikechant on 2010-01-25
> You can sometimes install an IDE drive in a newer computer by conecting it to the same cable your DVD drive is on, if you only have one optical drive.

You can also get adaptors which allow you to plug a PATA/IDE drive into a SATA socket.

---

### Post by Marc St Louis on 2010-01-25
> **Miljet said:**
> Do you know what type drives you are dealing with? Older computer used IDE drives that are connected with thin flat cables. Newer computers use SATA drives that use thinner round cables. They are not compatible.

You can sometimes install an IDE drive in a newer computer by conecting it to the same cable your DVD drive is on, if you only have one optical drive. But I have read numerous threads in this forum concerning boot problems caused by mixing drive types. Just understand what you are doing before diving in.

Both computers use IDE drives, the older drive is slower.

---

### Post by mick222 on 2010-01-25
should be ok make sure you set the second drive to slave and connect t the secondary connection on the cable.Then manually install as above.

---

### Post by Paqman on 2010-01-25
> **Marc St Louis said:**
> I am currently using windows on my work pc.  I have an old pc that I am not using anymore so I was thinking of removing its hd, formatting and installing it in my work pc then running ubuntu on it.  Can this be done?

When you say "my work PC" do you mean one that you own yourself, or one that's provided for you by your employer? If it's the latter, get permission first.

---

### Post by Marc St Louis on 2010-01-25
> **Paqman said:**
> When you say "my work PC" do you mean one that you own yourself, or one that's provided for you by your employer? If it's the latter, get permission first.

It's my own business and consequently my own PC.  I can see how someone would get a bit ticked if I were to start messing with their PC

---

### Post by Paqman on 2010-01-25
> **Marc St Louis said:**
> It's my own business and consequently my own PC.  I can see how someone would get a bit ticked if I were to start messing with their PC

Fair enough. We do sometimes get requests on here from people who want help circumventing restrictions imposed by their employer/school/etc.

---

### Post by Marc St Louis on 2010-01-25
> **Paqman said:**
> Fair enough. We do sometimes get requests on here from people who want help circumventing restrictions imposed by their employer/school/etc.

Doesn't seem to be a very intelligent thing to

---

### Post by llawwehttam on 2010-01-25
> **Miljet said:**
> Do you know what type drives you are dealing with? Older computer used IDE drives that are connected with thin flat cables. Newer computers use SATA drives that use thinner round cables. They are not compatible.

You can sometimes install an IDE drive in a newer computer by conecting it to the same cable your DVD drive is on, if you only have one optical drive. But I have read numerous threads in this forum concerning boot problems caused by mixing drive types. Just understand what you are doing before diving in.

I use a mix up of drives and as long as the slower IDE drives have time to be detected before your OS boots up it should be fine.

There are also converters available.

---

