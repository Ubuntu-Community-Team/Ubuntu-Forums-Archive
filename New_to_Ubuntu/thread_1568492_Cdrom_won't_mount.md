---
title: "Cdrom won't mount"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by LG83 on 2010-09-05
Hi,

I'm using ubuntu 10.04 as a guest on winxp.

I tried the following to get my cdrom mounted:

sudo mkdir /media/cdrom; 
sudo mount /dev/cdrom/media/cdrom/

In response I got: 
mount: can't find /dev/cdrom/media/cdrom/ in /etc/fstab or /etc/mtab

I would like to know how to fix it and also make ubuntu mount cdrom automatically at startup.

P.S: why should something as basic as cdrom detection be such a big deal in linux?

Thanks.

---

### Post by jtarin on 2010-09-05
Have you tried mounting without sudo?
run the command ```
ls -al /dev/cd*
```
Watch your spacing between your mount device and /media you have it as one long path.

---

### Post by LG83 on 2010-09-05
> **jtarin said:**
> Have you tried mounting without sudo?
run the command ```
ls -al /dev/cd*
```Watch your spacing between your mount device and /media you have it as one long path.


When typing:

ls -al /dev/cd*
I get:

ls: cannot access /dev/cd*: No such file or directory

---

### Post by jtarin on 2010-09-05
Run it```
ls -al /dev/cd*
```Post it

---

### Post by LG83 on 2010-09-05
And also - without sudo the result is the same as with.

---

### Post by jtarin on 2010-09-05
Try this one ```
cdrecord -scanbus
```You do have a cdrom in the drive....oh yeah!

---

### Post by LG83 on 2010-09-05
ls: cannot access /dev/cd*: No such file or directory

---

### Post by LG83 on 2010-09-05
I believe I do have a cdrom drive :D

But here's what I get for cdrecord -scanbus:

wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

---

### Post by jtarin on 2010-09-05
> **LG83 said:**
> I believe I do have a cdrom drive :D

The question was...do you have CD disc in the drive at the present time?

---

### Post by jtarin on 2010-09-05
Is this a Wubi install?

I think the link for your device to "cdrom" could be broken or non-existing.

So we need to find out the device name for your cdrom and make the link like this.
```
username@hostname# ln -sf /dev/hdX /dev/cdrom
```
where X stands for a letter a...d that is the block device for your CD-ROM. 
This is how your drives are labeled:
/dev/hda - primary master
/dev/hdb - primary slave
/dev/hdc - secondary master
/dev/hdd - secondary slave
During start up if you check dmesg you should see which is your CD-ROM.Maybe look in the bios...some tell.

---

### Post by LG83 on 2010-09-05
Oh silly me:oops:

No, my cdrom is empty at the moment.

---

### Post by LG83 on 2010-09-05
Maybe the problem has to do with the fact I'm running ubuntu as a guest through virtualbox?

---

### Post by jtarin on 2010-09-05
```
username@hostname# dmesg | less
```
and look for lines that begin with hda, hdb, hdc, hdd like these

---

### Post by jtarin on 2010-09-05
> **LG83 said:**
> Maybe the problem has to do with the fact I'm running ubuntu as a guest through virtualbox?
Could be. I don't do virtual boxes. Have always been a dual booter, but now have got the wife trained on Linux and we rarely boot into Win7 anymore. In fact just today I grew Ubuntu's partition and shrunk Wins.

---

### Post by jtarin on 2010-09-05
What Virtual box are you running? You'll have to make the link in its configuration file(s). [Here's one way.]("http://wiki.archlinux.org/index.php/VirtualBox#Setting_up_CD-ROM_for_the_Virtual_PC")

---

