---
title: "Removing hard drive from system"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by Crusty Juggler on 2009-09-18
I have replaced my Mythbuntu hard drive and want to take it out, but when I disconnected the HDD, booting crashed after the BIOS screen.  I even tried disconnecting the 1st HDD, which was plugged into SATA-0 and plugged the second HDD into SATA-0, but no go.

Do I need to go in and edit the grub menu.lst and change the second harddrive from (1,0) to (0,0)?

---

### Post by bruno9779 on 2009-09-18
I think that there is more than that.

Probably grub or the MBR (master boot record) needed for the booting process are on the hdd that you are removing.

at what point does the booting stop?

have you tried to boot with a live CD and mount the HDD? does it work?

---

### Post by Crusty Juggler on 2009-09-18
Boot stops immediately after the BIOS screen.

I haven't tried mounting under a live cd, but if I think it would work fine.  When I plug both HDDs back into the original sata ports, it loads up fine and the grub menu offers up both HDDs as choices.

---

### Post by bruno9779 on 2009-09-18
probably you will have to set your bios to recognize the HDD (can't help you here)

you will have to reinstall grub from the live CD

```
sudo grub-install /dev/hda
```

and reconfigure it

---

### Post by mapes12 on 2009-09-18
> **Crusty Juggler said:**
> I have replaced my Mythbuntu hard drive and want to take it out, but when I disconnected the HDD, booting crashed after the BIOS screen.  I even tried disconnecting the 1st HDD, which was plugged into SATA-0 and plugged the second HDD into SATA-0, but no go.

Do I need to go in and edit the grub menu.lst and change the second harddrive from (1,0) to (0,0)?Have you installed an OS on the second HDD or are you just trying to copy your old drive to your new drive??

---

### Post by Crusty Juggler on 2009-09-18
I've installed an OS (Mythbuntu 9.04) on the second HDD.  Mythbuntu 8.04 is on the first HDD.

---

### Post by falconindy on 2009-09-18
Yup, you're removing Grub when you disconnect that first hard drive. Leave hdd1 disconnected and re-install grub from the live CD as per above.

---

### Post by mapes12 on 2009-09-19
> **Crusty Juggler said:**
> I've installed an OS (Mythbuntu 9.04) on the second HDD.  Mythbuntu 8.04 is on the first HDD.In that case why not just remove the old HDD, install the new HDD into the same HDD SATA interface then do a fresh install. GRUB will then configure itself to the new HDD and not be confused with the what's on the old HDD.

---

