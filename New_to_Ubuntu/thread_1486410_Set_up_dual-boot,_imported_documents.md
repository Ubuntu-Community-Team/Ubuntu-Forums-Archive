---
title: "Set up dual-boot, imported documents"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Newbie2910 on 2010-05-17
When I did this, did the setup make duplicate copies of all of my documents or just set the Linux filesystem so it can see them on my Windows Vista partition? 

I hope to slowly migrate all of my stuff to Ubuntu and eventually remove the Windows partition.

---

### Post by ubunterooster on 2010-05-17
It should have copied them from vista to Ubuntu

---

### Post by Newbie2910 on 2010-05-17
I thought so, but wanted to be sure.

They are in my /home folder (wow... look at that I typed that in Linux-ese not with a "\"... so cool :P).

I will do some more checking and make a few backups when in Vista before removing them from that partition.

I  did some reading that I will be able to delete the NTFS partition and expand the EXT4 partition so that Ubuntu can use all of it?  Sound right?

---

### Post by mike555 on 2010-05-17
might I suggest backing up doc's etc. to an external hard drive of USB thumbdrive ...... I learned the hard way when my hard drive failed , thankfully most of mine were backed up using "dropbox" ..

 you could use "Ubuntuone" also ..

---

### Post by ubunterooster on 2010-05-17
> **Newbie2910 said:**
> I thought so, but wanted to be sure.

They are in my /home folder (wow... look at that I typed that in Linux-ese not with a "\"... so cool :P).

I will do some more checking and make a few backups when in Vista before removing them from that partition.

I  did some reading that I will be able to delete the NTFS partition and expand the EXT4 partition so that Ubuntu can use all of it?  Sound right?
Sounds right.

---

### Post by Newbie2910 on 2010-05-17
What is "Ubuntuone"?  I've seen it but what is it?

Yes I use USB drives and CDs for backups profusely

---

### Post by ubunterooster on 2010-05-17
A Linux Version of Dropbox; it is a cloud backup medium.             [[IMG]https://www.dropbox.com/static/images/dropbox_logo_home.png[/IMG]]("https://www.dropbox.com/")




[https://one.ubuntu.com/](https://one.ubuntu.com/)

---

### Post by ranch hand on 2010-05-17
If you are going to drop MS (good idea) I would seriously consider reinstalling your Ubuntu first.

That is because I am sure you are installed on one partition.  If you were to delete your current ext4 partition and reinstall on a / (root) and /home partition you will insure the safety of your data a little bit more.  This is because the data will all be in the /home partition and if you really screw you OS you can just reinstall the / partition and not format the /home partition in the installer.

I would also put the / partition on a primary partition and the /home and swap partitions in as logical partitions within an extended partition.  This gives you much greater flexibility for the future.

---

