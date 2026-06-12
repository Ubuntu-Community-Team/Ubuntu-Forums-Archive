---
title: "Problem mounting ISO file in Ubuntu 10.04"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by Dactula on 2011-06-01
Hi All,

My PC is dual boot with Windows XP and Ubuntu 10.04. I am new to the world of linux. 

I had an ISO image file of a  DVD copy protected with SafeDisc which I mounted as a virtual drive in Windows using Daemon Tools. I tried to do the same in Ubuntu with softwares like gISOmount, kISO, Gmount-iso and Acetone ISO. The first three gave various error messages. Acetone ISO was able to read the contents of the ISO file in a new folder on the desktop and I ran its setup program which installed the program under Wine and also created a desktop icon. However when I try to run the program it gives the message "Cannot locate CD ROM , insert correct CD ROM select OK and restart application". 

Is there a way out ?

---

### Post by Dactula on 2011-06-01
I ought to add that the Setup file of the ISO image displays a warning regarding certain dll files which "failed to self register" whatever that is supposed to mean.

---

### Post by MartyBuntu on 2011-06-01
> **Dactula said:**
> Hi All,

My PC is dual boot with Windows XP and Ubuntu 10.04. I am new to the world of linux. 

I had an ISO image file of a  DVD copy protected with SafeDisc which I mounted as a virtual drive in Windows using Daemon Tools. I tried to do the same in Ubuntu with softwares like gISOmount, kISO, Gmount-iso and Acetone ISO. The first three gave various error messages. Acetone ISO was able to read the contents of the ISO file in a new folder on the desktop and I ran its setup program which installed the program under Wine and also created a desktop icon. However when I try to run the program it gives the message "Cannot locate CD ROM , insert correct CD ROM select OK and restart application". 

Is there a way out ?

Did you configure WINE to see the mounted image as your disk drive?

---

### Post by Dactula on 2011-06-02
Please instruct me regarding how to configure Wine appropriately. Thanks.

---

### Post by jaacko on 2011-06-02
> **Dactula said:**
> Please instruct me regarding how to configure Wine appropriately. Thanks.

Open winecfg, by pressing ALT+F2 and typing
```
winecfg
```

On Drives tab click Add. This adds a new drive letter for wine. Then point the newly created drive letter to point to the folder where your ISO-file is mounted. Hope this works.

---

### Post by Anuovis on 2011-06-02
It would be a good idea to also click *Show advanced *after adding that drive and then pick CD-ROM in the *Type *menu.

If that doesn't work, you might need to reinstall the software by mounting the iso to the location you specified. Sometimes the software gets confused if you use a different virtual CD drive to run it.

---

