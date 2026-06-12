---
title: "load kernel first"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by delparral on 2011-07-03
Ubuntu 9.1 is installed in sda1, however, while creating a separate boot partition an error occurred and now I can not boot sda1.  I get the message ¨load kernel first¨.

I have tried without success to learn to load a kernel.

Can you help?

---

### Post by wildmanne39 on 2011-07-04
> **delparral said:**
> Ubuntu 9.1 is installed in sda1, however, while creating a separate boot partition an error occurred and now I can not boot sda1.  I get the message ¨load kernel first¨.

I have tried without success to learn to load a kernel.

Can you help?
Hi, we can probably figure it out, but 9.10 is an old version of ubuntu it is not supported anymore, you will not have any kind of updates, not even security, you would be better off going with 10.04 it has long term support,but if you want to trouble shoot 9.10, post back here and we will give it a try.

---

### Post by amjjawad on 2011-07-04
> **wildmanne39 said:**
> Hi, we can probably figure it out, but 9.10 is an old version of ubuntu it is not supported anymore, you will not have any kind of updates, not even security, you would be better off going with 10.04 it has long term support,but if you want to trouble shoot 9.10, post back here and we will give it a try.

9.04 is not supported. 9.10 is until 11.10 ;)

---

### Post by mcduck on 2011-07-04
> **amjjawad said:**
> 9.04 is not supported. 9.10 is until 11.10 ;)

No, it's not. The support for 9.10 ended April 30, 2011.

Versions currently supported are 8.04 LTS (for servers only, until 2013), 10.04 LTS (until 2013 on desktops and 2015 on servers), 10.10 (until April 2012) and 11.04 (until October 2012).

[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

What comes to the threads actual problem, is there any specific reason why you are trying to create a separate boot partition? It's very rarely useful any more these days, and more often just causes troubles. Anyway, the booting problems are quite likely result from editing your partition layout, as that will change the UUIDs of the partitions. Reinstalling Grub and editing /etc/fstab to use corect UUIDs shoukld help.

---

### Post by delparral on 2011-07-04
Thank you all.

I am already using 10.04.  I only want to get into sda1 to get some personal information and photos there.

 However I can not access it.  When I select it on Grub booting I get the message ¨load the kernel first¨.

When I boot with Supergrub, I get the same message.  

I tried booting with Rescatux but it can not fix sda1.

I have tried to find out how to load the kernel without success.

This is my first time in the forums.  Ubuntu is trouble free all this started when I tried to install PC Linux in a separate partition.

If you tell me what to do I will try it.

Cheers

---

### Post by amjjawad on 2011-07-04
> **mcduck said:**
> No, it's not. The support for 9.10 ended April 30, 2011.

Versions currently supported are 8.04 LTS (for servers only, until 2013), 10.04 LTS (until 2013 on desktops and 2015 on servers), 10.10 (until April 2012) and 11.04 (until October 2012).

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)


Thanks :)
And sorry everyone for the wrong info!

---

### Post by mcduck on 2011-07-04
> **delparral said:**
> Thank you all.

I am already using 10.04.  I only want to get into sda1 to get some personal information and photos there.

 However I can not access it.  When I select it on Grub booting I get the message ¨load the kernel first¨.

When I boot with Supergrub, I get the same message.  

I tried booting with Rescatux but it can not fix sda1.

I have tried to find out how to load the kernel without success.

This is my first time in the forums.  Ubuntu is trouble free all this started when I tried to install PC Linux in a separate partition.

If you tell me what to do I will try it.

Cheers

If you just want to get your files from there, you don't need to boot it, just mount the partition from your current 10.04 install instead.

It should appear in the file manager's "places"-menu, most likely labeled by the size of the drive/partition.

---

### Post by delparral on 2011-07-04
I have tried accessing sda1 from Ubuntu 10.04 in sda3 but I can not find my notes nor I know how to access my Tomboy notes in sda1.

---

### Post by mcduck on 2011-07-04
> **delparral said:**
> I have tried accessing sda1 from Ubuntu 10.04 in sda3 but I can not find my notes nor I know how to access my Tomboy notes in sda1.

The notes are stored in your home directory, so once you mount the sda1 partition browse to /home/*yourusername*/.tomboy/ and copy the .notes files into ~/.tomboy on sda3.

(files & directories with a dot in front of the name are hidden, so you'll need to press Ctrl-h in the file manager to see them)

---

### Post by delparral on 2011-07-04
Thank you.  I was able to see many files but not the Tomboy files.  Am I supposed to use a terminal?  What commands should I type?

Another file that I found was the kernel.  I tried to extract it into the root directory, but I was not able because I do not know how to do this as root.  Can you help?

How can I be root? no one else uses the computer.

---

