---
title: "Adding an additional hard drive"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by dagarshali on 2011-06-27
Hi,
I have installed both windows 7 and ubuntu on my machine and use the grub to choose between the two. Currently, my desktop has only one hard disk on which both of these OS' are installed.

I have another internal hard disk that I bought exclusively for storing data both from windows and from ubuntu. Is there a specific way to install this ? I am kinda a new to this. So, any help would be greatly appreciated.

Regards,
Vishwa

---

### Post by wolfen69 on 2011-06-27
Just install gparted (in ubuntu) and format it to whatever file system you like. If you want both OS's to be able to read it, you'll have to format it to NTFS. Simple.

---

### Post by _0R10N on 2011-06-27
Since your second drive is not going to contain any OS, no specific action is required. Just plug it to your PC and boot your system.

As wolfen says, you need to format that drive so you can start storing information in it. You can do it through gparted or fdisk. But that's not all. After formating the disk, you'll need to tell ubuntu where and how to mount it so it can be accessible. To do that take a look at the /etc/fstab file and add an extra entry for your drive.

If you need further guidance no hesitate and let us know.

---

### Post by wolfen69 on 2011-06-28
> **_0R10N said:**
> After formating the disk, you'll need to tell ubuntu where and how to mount it so it can be accessible. To do that take a look at the /etc/fstab file and add an extra entry for your drive.


Actually, it will mount automatically when clicked on in your file browser. I've never had to add it to fstab.

---

### Post by Jagoly on 2011-06-28
Were you talking about setting up the storage, or actually opening up your case and plugging in the drive?

---

### Post by amjjawad on 2011-06-29
You need to worry about The Hardware Installation before The Software Installation :)

Your current HDD (HDD1) must be Master so the second one should be Slave or Secondary Master (it depends on where you connected to which Data Slot - there are IDE and SATA ) so a basic knowledge is required here.

Assuming you know the above step already, the next step will be your BIOS.
Enter BIOS and make sure your 2nd HDD (which you just installed) is detected.

After that, if GParted is not installed already, open the Terminal and:

```
sudo apt-get update
sudo apt-get install gparted -y

```

You'll find it under:

System > Administration > GParted.

MAKE SURE YOU SELECT THE RIGHT HDD.
**It should be sdb.**

Assuming it's a used HDD, you just need to format it and it should be NTFS so that both Ubuntu and Windows can access it. 
If it's NEW then you need to create a Partition Table - GParted will let you know in case this step is required.

With GParted, you can create, remove, format, resize partitions so you don't need another tool.

I suggest to give each partition a LABEL. That will help you to find your new partitions easily.

I guess you know how to access the new partitions :)

Good luck!

---

