---
title: "Live cd installation Ubuntu 10.04 does not support  Chipset Intel G41."
date: 2010-07-27
forum: New to Ubuntu
---

### Post by newbieususbuntu on 2010-07-27
After get live cd installation Ubuntu 10.04 64bit and 32bit. I tried run live cd installation with Ubuntu 10.04 64bit and 32bit. But i get both failure. My question is:

Will Ubuntu 10.04 support intel chipset G41? If can how to run live CD intallation on my comp.

There are my spec comp:
1. Processor : Intel Core 2 Duo E7400 2.8GHz.
2. Mainboard : Gigabyte GA-G41M-ES2H (Intel G41 chipset)
3. Monitor : LCD Samsung 21
4. Memory : Kingston 4Gb.
5. HDD : Seagate 320Gb.

Please someone can help me?

---

### Post by grief -l on 2010-07-27
What makes you think that the chipset doesn't support it?  It's more likely something wrong with the way it's burned onto the CD.   Don't use a CD-RW - just a simple CD-R. I must have burned 5 or 6 CD-RW before I found out they don't work. If that doesn't solve the problem use the md5Checksum utility and instructions on the download page to check the integrity of the download.  Gabe

---

### Post by clhsharky on 2010-07-28
newbieususbuntu

> After get live cd installation Ubuntu 10.04 64bit and 32bit. I tried run live cd installation with Ubuntu 10.04 64bit and 32bit. But i get both failure.
When is the failure - live sesion,instalation,boot?

> Will Ubuntu 10.04 support intel chipset G41?
Chipset drivers are in the Linux kernel, and Ubuntu 10.04 provides a Kernel that support your G41 chip.

> If can how to run live CD intallation on my comp.
You might not be able to, but first make sure you have a good live install CD as grief -l recommended. Try a live session in another computer.

I've read Intel will solve this soon with switching UMS/KMS drivers depending on chip.

Installation can be accomplished with alternate install CD.
Edit grub at boot with nomodeset selection, works with slightly older Intel chipsets.

Sharky

---

### Post by newbieususbuntu on 2010-08-01
> **grief -l said:**
> What makes you think that the chipset doesn't support it?  It's more likely something wrong with the way it's burned onto the CD.   Don't use a CD-RW - just a simple CD-R. I must have burned 5 or 6 CD-RW before I found out they don't work. If that doesn't solve the problem use the md5Checksum utility and instructions on the download page to check the integrity of the download.  Gabe

I burned ubuntu 10.04 to cd-r before that. But failure too. can i md5Checksum my cd ubuntu 10.04?

tq

---

### Post by newbieususbuntu on 2010-08-01
> **clhsharky said:**
> newbieususbuntu


When is the failure - live sesion,instalation,boot?


Chipset drivers are in the Linux kernel, and Ubuntu 10.04 provides a Kernel that support your G41 chip.


You might not be able to, but first make sure you have a good live install CD as grief -l recommended. Try a live session in another computer.

I've read Intel will solve this soon with switching UMS/KMS drivers depending on chip.

Installation can be accomplished with alternate install CD.
Edit grub at boot with nomodeset selection, works with slightly older Intel chipsets.

Sharky


Failure in live session

---

### Post by grief -l on 2010-08-01
> can i md5Checksum my cd ubuntu 10.04?

Yes, [bottom of this page]("https://help.ubuntu.com/community/HowToMD5SUM")

Gabe

---

### Post by newbieususbuntu on 2010-08-20
I really tried anyway for live run CD Ubuntu 10.04 at my PC(burn to CD-R) or other ways. But until now always failure.

Please anyone can help. That impposible just want to learning ubuntu i must change my pc. 

Before i jointed to this forum. i get information about linux we can get information/help from internet with quickly. But after i only just to try first time(that's only my first problem at linux always ca't to solve). This make me a little dissapointed for linux (ubuntu)....

Sorry this just my mind. So i hope not offened everyone.

tq

---

### Post by grief -l on 2010-08-20
As I have said, I went through the same problem you are having - I burned CD after CD and none of them worked until I found out not to use a CD-RW and to burn it as slow as possible (4X). Then my hardware didn't support Wifi so I couldn't get online to ask questions, the OS forgot my password after a hard shutdown and had to reinstall, I didn't understand about root and made more mistakes than the file system would allow and it shut me out of my own computer!  But that's how we learn!
 
Ubuntu (and Linux) doesn't have a Customer Support Desk so ranting and complaining is useless - either YOU want to get inside linux or you don't. If you do there are people here who will put out to help where they can, but they're all just people like you and me. None of them really care whether you give up or not (hope that doesn't offend you). 

OK, back to the problem. I would suggest you go to [shipit]("https://shipit.ubuntu.com/") and order a CD. In the meantuiime you can download[[URL="http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm"] Puppy Linux]("https://shipit.ubuntu.com/") [/URL]or[[URL="http://www.slitaz.org/en/"] Slitaz]("https://shipit.ubuntu.com/")[/URL] to play with while you wait for the ubuntu CD to arrive.[URL="https://shipit.ubuntu.com/"]
[/URL]

---

### Post by oldfred on 2010-08-20
On initial screen have you tried f4 safe boot or f6 to add parameters for different hardware?

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa

---

### Post by newbieususbuntu on 2010-08-27
For grief -l:
Thanks for your reply. I had success try live DVD ubuntu 10.04. But this just information only. I used DVD-RW for try live ubuntu 10.04 64bit. So do not burn to DVD-R.

For olfred:
Thanks for your reply. iI dnon't use any option at DVD ubuntu 10.04 64bit. But until now i don't know why can try live ubuntu from CD-RW or CD-R ubuntu 10.04.

---

