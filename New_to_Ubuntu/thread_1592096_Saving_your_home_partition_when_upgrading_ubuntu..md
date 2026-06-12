---
title: "Saving your home partition when upgrading ubuntu."
date: 2010-10-10
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-10-10
I was shown how to do this before but i can't remember how, when im on the installer i look for my home folder and label it /home . and do a /boot and a switch. Do i need to use Gparted first to set them up for this?

---

### Post by TeoBigusGeekus on 2010-10-10
Just look for your home partition in the installer, mount it as /home and remember **NOT** to format it.

---

### Post by bprins on 2010-10-10
sorry for not understanding what u mean, but you already have a separate partition for your home folder?

---

### Post by Rave Gloves on 2010-10-10
ive got my home and the swap, it will not let me install without a root partition, do i need to make one in Gparted?

---

### Post by beew on 2010-10-10
This is my understanding, though I haven't tested it and I hope that someone may confirm it if I am correct or point out where it is wrong. 

In the old system there is a root partition (/), a home partition (/home) and a swap partition. I think in order to keep the /home partition in a reinstallation (or upgrade?) all I need to do is to choose "manual" in step 4 during installation (Lucid, I think the step sequence in Maverick is a bit different)and only reformat the / partition and then proceed as usual.

---

### Post by beew on 2010-10-10
> **Rave Gloves said:**
> ive got my home and the swap, it will not let me install without a root partition, do i need to make one in Gparted?

Then how do you boot in the old system? It is news to me that you can boot at all without a root partition, I learn something new everyday.:P

---

### Post by Rave Gloves on 2010-10-10
This is my partitions, what should i do?

---

### Post by beew on 2010-10-10
So apparantly you don't have a /home partition after all. I could be wrong but I think in that case you won't be able to keep your personal settings and you can keep your data only by manually saving them somewhere.

P.S. Maybe you can save some folders with your settings in the /home folder (not the /home partition, it looks like you don't have one) and then replace the new ones with them once you finish (re) installation? A bit tedious but it should work based on theory (:))

---

### Post by amjjawad on 2010-10-10
> **Rave Gloves said:**
> This is my partitions, what should i do?

You need minimum:

1- / partition (root)
2- swap partition

Some may go for 3 partitions 

1- / (root) partition 
2- swap partition
3- /home partition

My suggestion is:
Create 4 partitions

1- root (/)
2- /home
3- /data
4- swap

OR
Split your HDD to two main partitions. One for Ubuntu and the other keep it as it's just in case you want to install Windows later on or any other Linux Distro. For the first partition, you can go for the 4 partitions scheme.

Also, /data could be formated as FAT32 so that it could be accessible by both Ubuntu and Windows just in case you'll install Windows in the future.

---

### Post by amjjawad on 2010-10-10
> **Rave Gloves said:**
> I was shown how to do this before but i can't remember how, when im on the installer i look for my home folder and label it /home . and do a /boot and a switch. Do i need to use Gparted first to set them up for this?

[https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)

---

### Post by bprins on 2010-10-10
what I would do in your situation is the following.

pack your home folder and store it on a cd-rom

get a copy of ubuntu on a CD.

throw away all your partitions.

make 3 new partitions (swap mount point, / mount point, /home mount point) (or optionally a fourth as previous poster proposed for data, but I don't use that, I store my data in /home).

then, install ubuntu, assign your swap, home and root partition.

after installing, unpack your home tarball from CD back in your /home partition.

and you're done.

---

### Post by beew on 2010-10-10
> **amjjawad said:**
> You need minimum:

Also, /data could be formated as FAT32 so that it could be accessible by both Ubuntu and Windows just in case you'll install Windows in the future.

Not necessary, Windows can read Ext3 with the help of this utility.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It is called Ext2IFS but if you read the documentations it works for Ext3 as well (guess the old name stuck)

---

### Post by amjjawad on 2010-10-10
> **beew said:**
> Not necessary, Windows can read Ext3 with the help of this utility.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It is called Ext2IFS but if you read the documentations it works for Ext3 as well (guess the old name stuck)

You could save time to download, install and reboot Windows just to use that ;)
If I were you, I would just save my time and format it as FAT32 :)

---

### Post by TeoBigusGeekus on 2010-10-10
> **beew said:**
> Not necessary, Windows can read Ext3 with the help of this utility.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It is called Ext2IFS but if you read the documentations it works for Ext3 as well (guess the old name stuck)
I wouldn't let windows anywhere near my linux files.
Create a separate NTFS partition (data, backup, downloads or whatever) if you like for linux/windows access, but don't let windows have access to your linux system files.

---

### Post by amjjawad on 2010-10-10
> **TeoBigusGeekus said:**
> I wouldn't let windows anywhere near my linux files.
Create a separate NTFS partition (data, backup, downloads or whatever) if you like for linux/windows access, but don't let windows have access to your linux system files.

I can tell you had a very bad experience :)
Without reading this, I won't let Windows access Linux's files :D hehe.

---

