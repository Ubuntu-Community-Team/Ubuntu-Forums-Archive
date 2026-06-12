---
title: "Can't run AVG? Tried WINE..."
date: 2009-05-09
forum: New to Ubuntu
---

### Post by newbpanda on 2009-05-09
Trying to use AVG to get rid of my viruses. It won't even load with WINE. I'm losing my mind here. :D

---

### Post by Wa1k3rTXRang3r on 2009-05-09
dont bother. most viruses dont even affect linux so you dont need an antivirus

---

### Post by anjilslaire on 2009-05-09
Correct. What makes you think your linux system is infected? A virus omly works on the OS it's designed for. Windows viruses cannot affect a linux system.

---

### Post by newbpanda on 2009-05-09
Yes, but my Windows bootable portion of the computer is what has the virus...

---

### Post by leomelo on 2009-05-09
Try Avast.There is a version for Linux.

---

### Post by Wa1k3rTXRang3r on 2009-05-09
why not install it on your windows partition then?

---

### Post by Shawn K on 2009-05-09
(Disregard.  My earlier response no longer applies.)

---

### Post by anjilslaire on 2009-05-09
Or try ClamAV, available in the repositories.
However, you should get AVG installed in Windows itself, and then run the AV scan while booted into Windows in Safe Mode.

That being said, and its going to be unpopular news, but once a system is compromised with a system-level infection, cleaning with antivirus software is not truly sufficient, as you can never truly confirm that the infection has been mitigated. 
To ensure the integrity of your data, the only way to be sure all malware is removed is to format & reinstall Windows, and change all passwords *after* the format.

The reason for this is, even if your AV software finds and removes the intial infection, there are likely unknown other malware that have piggybacked in on the initial infection that is not being detected. Without knowing what you really have on the system compromising your data, there's no way to verify it's 100% clean again without a format.

---

### Post by newbpanda on 2009-05-10
I have Avast working now. Got it earlier... I'm supposed to move infected files to the "chest"? Once this is done, I'll perform backup operations...

EDIT: Windows XP refuses to login on my computer. I mentioned that in an earlier post... *sighs*

EDIT AGAIN: What if I format the hard drive & partition everything for Ubuntu THEN install the virtual machine "Win4Linux" onto Ubuntu to run my Windows APPs? Would this still be affected by old viruses? I'm sick and tired of the limitations of a dual-booting system.

---

### Post by SunnyRabbiera on 2009-05-10
Yeh your XP might be fried, but maybe linux can help recover it somehow.

---

### Post by newbpanda on 2009-05-10
Haha! I love the avatar, SunnyRabbiera! Tugboat doing that stupid promo! :D

---

### Post by MontelEdwards on 2009-05-10
lol. 
this made me laugh.  You really dont need virus protection in Linux.
because for a virus to do any major damage, they have to have your root password.
Unlike Windows where any program can shut down the computer by its self.
But i think there is ClamAV or something like that. I have had Linux since I was 11 and nothing really hurt me bad.

---

### Post by newbpanda on 2009-05-10
New question: Know a good utility for partitioning an **external** hard drive? 

I have a Seagate "SN Max" Serial ATA external hard drive of unknown capacity (probably about 250GB) and I would like to use it to back up my hard drive with. 

I currently have Western Digital's "Data Lifeguard" for XP but it only works with WD hard drives... which is strange because when I originally formatted the external I used this very same program... it refuses to format the or repartition my Seagate eternal HD. :(

---

### Post by anjilslaire on 2009-05-11
gparted should be able to partition any drive properly detected by the system, external or internal.

---

### Post by newbpanda on 2009-05-11
Okay, thanks for advice, folks. My computer now has Ubuntu as the one & only bootable partition with XP running via a virtual machine within Ubuntu. :D

EDIT: Uh, I forget how to "mark as solved." :D

---

