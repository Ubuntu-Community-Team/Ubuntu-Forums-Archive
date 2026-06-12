---
title: "IDE vs AHCI ?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by sturdy on 2008-12-17
Hi all,

I'm a real nooby so be gentle...
I have a ASUS P5Q-E mobo (P45/ICH10R chipset) and had a hard time finding a linux distro that would recognize both SATA and PATA drives. Ubuntu 8.1 does that so I am trying to wean myself from XP Pro. Both OS are currently installed on separate HD in IDE mode. Apparently there is no significant benefit to non-RAID AHCI Windows so I am wondering if there is any benefit to moving my ubuntu to AHCI? If yes, is a re-install required?

Much thanks,
Sturdy

---

### Post by surj08 on 2008-12-17
Hm wierd im pretty sure all current linux distros support IDE(Pata) and SATA.


Also AHCI only works for SATA drives which are a different type of drive
 
[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface#Common_problems_switching_to_AHCI_under_Linux](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface#Common_problems_switching_to_AHCI_under_Linux)

---

### Post by cariboo on 2008-12-17
If your windows installation is fully up to date, changing to achi should be no problem. You can do this in the bios, and there is no need  to reinstall.

Linux natively uses achi, it is ancient OSs like Windows XP that have a hard time with current hardware.

Jim

---

### Post by sturdy on 2008-12-17
> **surj08 said:**
> Hm wierd im pretty sure all current linux distros support IDE(Pata) and SATA.


Also AHCI only works for SATA drives which are a different type of drive
 
[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface#Common_problems_switching_to_AHCI_under_Linux](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface#Common_problems_switching_to_AHCI_under_Linux)

Thanks for the response and the link. And of course you are right. I thought it was weird too. Here is the rest of the story: 

The linux distros all saw my SATA drive but failed to see the PATA drives on IDE controllers whether the BIOS was IDE or AHCI mode. The problem seems to have been the implementation of the ICH10R on the P5Q-E mobo. The BIOS was also updated several times so that may have been the issue. Anyway, the latest ubuntu 8.1 is the only distro I found (8.04 did not) that would recognize my old IDE drives on either the onboard IDE controller or on a PCIe-IDE controller.

Since linux was a nogo at the time, I installed XP Pro as IDE and when ubuntu 8.1 became available it auto installed as IDE. Now I see there is a way to retrofit XP for AHCI. A reinstall of ubuntu is easy but if there is no practical improvement in ubuntu AHCI performance on a desktop pc, I don't think it is worth the effort to muck with XP. I really don't care about the AHCI bells and whistles like sequential spinup, etc.

So if there is a practical benefit, I'll do the retrofit, otherwise: KISS... and, if it ain't broke, don't fix it.

Thanks again,
Sturdy

---

