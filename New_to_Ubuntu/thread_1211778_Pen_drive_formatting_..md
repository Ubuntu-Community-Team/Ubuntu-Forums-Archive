---
title: "Pen drive formatting ."
date: 2009-07-13
forum: New to Ubuntu
---

### Post by rsiddharth on 2009-07-13
I want to format my pen drive ( USB stick ) , how will I do it in ubuntu ? . 

Thank you for any help .

---

### Post by hkvn on 2009-07-13
Use **gparted**

---

### Post by mano cazalet on 2009-07-13
for ext3 you can do it from terminal with
```
sudo mkfs.ext3 /dev/sdaX
```

just be careful to format the correct drive

for ntfs i don't know how it works in terminal, just in gparted

---

### Post by ddrichardson on 2009-07-13
gparted is not installed by default so you could just open a terminal and use the mkfs.vfat command. Make sure you know the partition name (as in /dev/sdb) and remember that you need to use sudo so **make sure you have the correct device**.

You can find the device using:
```
dmesg|grep usb
```With the device plugged in.

To format:
```
sudo mkfs.vfat DEVICE_NAME
```

---

### Post by dharanitharan on 2009-07-31
wat i ve to do to format the pen drive with ntfs file system:)

---

### Post by kpkeerthi on 2009-07-31
> **dharanitharan said:**
> wat i ve to do to format the pen drive with ntfs file system:)

Install gparted using synaptic. Its interface is graphical and intuitive.

---

### Post by vinutux on 2009-07-31
> **kpkeerthi said:**
> Install gparted using synaptic. Its interface is graphical and intuitive.

Install gparted```
sudo apt-get install gparted
```

---

### Post by Humanum on 2009-07-31
> **dharanitharan said:**
> wat i ve to do to format the pen drive with ntfs file system:)

Once you've installed Gparted, launch it and then select the drive you want to format.

Then, click on it (might be with the right button) and you'll have a list of options... from there it's kind of easy peasy... You read and apply

Haven't got my laptop near to tell the whole process :popcorn:

---

### Post by dharanitharan on 2009-07-31
is there any other way s available to format via terminal commands:confused:

---

### Post by Grenage on 2009-07-31
Totally,

For example, I want a basic format for use on linux and windows:

**If you need to partition it:**
fdisk /dev/sdc (pen drive)
make a type-c partition

**Just to format the partition:**
mkdosfs /dev/sdc1 (pick the right drive and partition)

Edit: **ddrichardson** has already covered this for you, scroll up.

---

### Post by dharanitharan on 2009-07-31
thanks a lot:)

---

### Post by rsiddharth on 2009-07-31
I apologize for being 2 weeks to respond  . I Thank you ddrichardson , mano cazalet and others for your help .

---

