---
title: "Error: &quot;The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed&quot;"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by xGutsAndGloryx on 2009-05-18
Hello Everyone,

I am trying to load linux on my new computer. i keep getting the following errors message.

Error: "The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed"



what should i do?

---

### Post by taurus on 2009-05-18
Is that a brand new harddrive or is there already something on it?

From Ubuntu LiveCD, open a terminal and post the output of this command.

```
sudo fdisk -l
```

---

### Post by xGutsAndGloryx on 2009-05-18
> **taurus said:**
> Is that a brand new harddrive or is there already something on it?

From Ubuntu LiveCD, open a terminal and post the output of this command.

```
sudo fdisk -l
```


brand new hard drive....i just built the system... i have tried installing ubuntu a few times.

---

### Post by xGutsAndGloryx on 2009-05-18
i can't get it to give any output

---

### Post by taurus on 2009-05-18
Go into the BIOS and make sure it is detecting your harddrive (drive headers and sectors).  Also, make want to turn on the AHCI for your harddrive.

---

### Post by xGutsAndGloryx on 2009-05-18
> **taurus said:**
> Go into the BIOS and make sure it is detecting your harddrive (drive headers and sectors).  Also, make want to turn on the AHCI for your harddrive.


i can go into the bios and check to verify it's detecting the hard drive. how do i turn on the AHCI?

---

### Post by xGutsAndGloryx on 2009-05-18
> **xGutsAndGloryx said:**
> i can go into the bios and check to verify it's detecting the hard drive. how do i turn on the AHCI?

.

---

### Post by xGutsAndGloryx on 2009-05-22
.

---

### Post by Didius Falco on 2009-05-22
Hi,

AHCI should be an option in your BIOS. Not knowing what BIOS you are using, I can't say exactly where it would be, but look for a place to set it to use IDE/AHCI/RAID and that will be it.

Regards,

Didius

---

### Post by xGutsAndGloryx on 2009-05-26
i checked it the bios.

its said the bios version is

NL94510J.86A.0025.2008.0107.1543

---

