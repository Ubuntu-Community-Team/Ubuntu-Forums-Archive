---
title: "Grub"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by bj218 on 2010-03-14
How can I move grub to another partition on the same hard drive?

---

### Post by J V on 2010-03-14
Good question... uhh...

Why would you want to do that?

IMO the only seperate partition worth a * is /home...

---

### Post by Paqman on 2010-03-14
Broadly speaking, Grub comes in two parts. The first part is located on the master boot record of your drive The second (larger) part is located on the partition your OS is on and contains all the actual nuts and bolts of Grub. All the first part does is locate the second part, so that it can do all the work.

What are you actually trying to move, and what are you trying to achieve?

---

### Post by oldfred on 2010-03-14
If you really want a grub partition:

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

grub2:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

### Post by bj218 on 2010-03-15
> **Paqman said:**
> Broadly speaking, Grub comes in two parts. The first part is located on the master boot record of your drive The second (larger) part is located on the partition your OS is on and contains all the actual nuts and bolts of Grub. All the first part does is locate the second part, so that it can do all the work.

What are you actually trying to move, and what are you trying to achieve?
I want to but grub on a separate partition so I wont loose it if I have 
a problem. I am running 3 operating Ubuntu/WinXP/Mint.

---

### Post by sandyd on 2010-03-15
> **bj218 said:**
> I want to but grub on a separate partition so I wont loose it if I have 
a problem. I am running 3 operating Ubuntu/WinXP/Mint.
You will have to replace "/dev/sdaxx" with the partition that you have created for grub. (I suggest it to be formated as ext3. The below examples is based on the thought that you have formated it as ext3....)


```

sudo mount -t ext3 /dev/sdaxx /mnt
gksudo cp /boot/* /mnt
sudo umount /mnt
sudo mv /boot /boot.bak
gksudo gedit /etc/fstab
gksudo mkdir /boot
sudo mount -t ext3 /dev/sdaxx /boot

```in a blank new line at the bottom, add this
```

/dev/sdaxx /boot ext3 relatime,errors=remount-ro 0 1

``````

grub-install /dev/sdaxx
```And I hope I didnt make any typos.

oh, and I almost forgot.
you will have do to the step
```

/dev/sdaxx /boot ext3 relatime,errors=remount-ro 0 1

```
on mint too (assuming youve set up grub using ubuntu)

---

### Post by bj218 on 2010-03-21
I am using ext4 will this change any thing?

---

### Post by bumanie on 2010-03-21
The commands should work the same as long as you substitute ext4 where the ext3 presently is. Those instructions will give you a separate boot partition. Another thing you could look at is [GAG bootloader]("http://gag.sourceforge.net/"), it can handle up to 9 different operating systems and does not need to have a boot partition. Read the link.

---

