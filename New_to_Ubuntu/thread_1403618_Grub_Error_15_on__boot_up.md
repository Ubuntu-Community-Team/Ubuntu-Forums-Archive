---
title: "Grub Error 15 on  boot up"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by dojerp on 2010-02-10
I accidentially modified my root desktop file in my Ubuntu BT4 and need to repair it but am a total newbie. I have downloaded the ISO onto a CD and have rebooted up to the CD image but am having problems doing anything else due to lack of experience. And YES! I have serached and run through the other postings similar but if I could understand it I would have fixed it by now. HELP!!! How do I fix the right boot device.
Would there be someone available to assist me immediately! Thank you.
 
I have /dev/hda1; /dev/hda2; /dev/hda5

---

### Post by rcayea on 2010-02-10
If you are using Ubuntu 9.10 I would do this:

Boot from live cd and then, 

In a terminal, type:

"sudo fdisk -l" This will tell you the drive letter and number. 

then:

"sudo mount /dev/sdAB /mnt" the AB is A for the drive to boot and the number is the linux partition.

then type:

"sudo grub-install --root-directoyry=/mnt /dev/sdA"

A would be the drive again. 

then type:

"sudo umont /mnt"


after all this, I like to go into synaptic and reinstall "grub-pc".

Of course all of the above commands you would type without quotes. 


good luck

---

### Post by lyall on 2010-02-14
see the following link
[https://wiki.ubuntu.com/Grub2#Err15]("https://wiki.ubuntu.com/Grub2#Err15")

answer from SoFl W

I had the same problem with the error 15

I have two hard drive a SCSI 37GB Ubuntu installed on it
and a IDE 20Gb for backups
the SCSI is sdb and the IDE is sda

I had to remove the IDE drive, then the SCSI become sda
then the above link info worked for me

hope this helps

good luck and have fun learning

---

