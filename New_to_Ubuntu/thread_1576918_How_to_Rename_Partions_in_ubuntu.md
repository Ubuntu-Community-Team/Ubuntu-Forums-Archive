---
title: "How to Rename Partions in ubuntu?"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by tajiknomi on 2010-09-18
[SIZE=2][COLOR=Black][I]I had currently Installed Ubuntu and i forgot to Rename my part-ions during Setup,now i want to **rename my partions**,how can i do it??

whenever i tried to remain part-ions,it shows me the message "**Couldn't be renamed,Operation not supported by Backned..**

Help me.
[/I][/COLOR][/SIZE]

---

### Post by wilee-nilee on 2010-09-18
> **tajiknomi said:**
> [SIZE=2][COLOR=Black][I]I had currently Installed Ubuntu and i forgot to Rename my part-ions during Setup,now i want to **rename my partions**,how can i do it??

whenever i tried to remain part-ions,it shows me the message "**Couldn't be renamed,Operation not supported by Backned..**

Help me.
[/I][/COLOR][/SIZE]

Install gparted; run in the terminal
```
sudo apt-get install gparted
```

Then open gparted right click on the partition, then label, name it, hit close, and then hit the check icon in the top panel to initiate it's running.

---

### Post by tajiknomi on 2010-09-18
[SIZE=2][I]I have tried to label one of my Partion,but it create another exact partion and harm my current partion...now when i want to enter that partion,it shows me the message :Unable to mount location: Internal Error,no mount object 4 mounted volume"

is their any way to Undo it..???
[/I][/SIZE]

---

### Post by wilee-nilee on 2010-09-18
> **tajiknomi said:**
> [SIZE=2][I]I have tried to label one of my Partion,but it create another exact partion and harm my current partion...now when i want to enter that partion,it shows me the message :Unable to mount location: Internal Error,no mount object 4 mounted volume"

is their any way to Undo it..???
[/I][/SIZE]

Can you post a screen shot of gparted.

---

### Post by tajiknomi on 2010-09-18
[SIZE=2]*print screen is attached here with...*[/SIZE]

---

### Post by tajiknomi on 2010-09-18
[SIZE=2]*Gparted...*[/SIZE]

---

### Post by wilee-nilee on 2010-09-18
> **tajiknomi said:**
> [SIZE=2]*print screen is attached here with...*[/SIZE]

I need to see gparted.
[ATTACH]169819[/ATTACH]

This is what I want to see, was this what you used as I suggested.

---

### Post by tajiknomi on 2010-09-18
[SIZE=2][I]but i can do now to undo my current operation??


[/I][/SIZE]

---

### Post by tajiknomi on 2010-09-18
[SIZE=2][I]but what can i do now to undo my current operation??


[/I][/SIZE]

---

### Post by wilee-nilee on 2010-09-18
> **tajiknomi said:**
> [SIZE=2]*Gparted...*[/SIZE]

What I see are flags on all the ntfs partitions, if you right click on each one, then information and see what they say, and post that information. 

The problem here is that the instructions I gave you should not have caused any problems it is just adding a name. So your going to have to be a little more specific; which partition and what exactly you did.

---

### Post by tajiknomi on 2010-09-18
*information is attached...*

---

### Post by wilee-nilee on 2010-09-18
> **tajiknomi said:**
> *information is attached...*

Were any of those flags there when you first opened gparted and did nothing.

---

### Post by tajiknomi on 2010-09-18
*information about partion...*

---

### Post by wilee-nilee on 2010-09-18
So I have asked a couple of questions that are important.

#1 were the flags already on the ntfs partitions before you did anything to change the name? 

#2 So your going to have to be a little more specific; what in your words did you actually do?

I can't really help if I don't have some real specific details.

---

### Post by jtarin on 2010-09-18
_Keep in mind you can only modify unmounted partitions_.
**From the Gparted manual**
> Partition operations such as delete, resize, move, copy, format, check, and label require the partition to be unmounted.> To have all partitions unmounted and available for partition editing actions, boot from a Live CD and use gparted

---

### Post by wilee-nilee on 2010-09-18
> **jtarin said:**
> _Keep in mind you can only modify unmounted partitions_.
**From the Gparted manual**

Thanks man I appreciate the post.;) The names couldn't be changed on a mounted partition anyway the label is off when mounted, so this is a well; not sure what happened here.

---

### Post by DeadlyWolf on 2010-09-18
I use Disk Utility Edit Filesystem Label.

---

### Post by candtalan on 2010-09-18
Question:
when a Label is changed, does the content of the partition get changed, corrupted deleted or whatever, or is a change of label independednt of the data?

tia

---

### Post by jtarin on 2010-09-18
> **candtalan said:**
> Question:
when a Label is changed, does the content of the partition get changed, corrupted deleted or whatever, or is a change of label independednt of the data?

tiaIndependent.

---

### Post by jtarin on 2010-09-18
> **wilee-nilee said:**
> Thanks man I appreciate the post.;) The names couldn't be changed on a mounted partition anyway the label is off when mounted, so this is a well; not sure what happened here.The post was directed at the OP, but since you like to chime in on my efforts....your incorrect when you state.."the label is off when mounted".

---

### Post by srs5694 on 2010-09-18
The "Unable to read the contents of this file system" message is consistent with the idea that the disk was improperly unmounted (say, because of a power failure or system crash). If this is the case, you won't be able to do much with the partition from Linux until it's fixed using CHKDSK *in Windows.* I therefore recommend rebooting into Windows and using it to fix the disks. It's also pretty easy to relabel the disks in Windows, as I recall.

As to how relabeling a partition could result in it splitting in to, I can't say, except that it was almost certainly user error -- selecting the wrong option from a menu. Without the specifics that wilee-nilee is asking for, though, nobody can do much but speculate on this score.

---

### Post by wilee-nilee on 2010-09-18
> **jtarin said:**
> The post was directed at the OP, but since you like to chime in on my efforts....your incorrect when you state.."the label is off when mounted".

Funny label is off on my mounted partitions. I have to say though dealing with you is like looking in a mirror.;)

---

### Post by bodhi.zazen on 2010-09-18
This is , IMHO, much easier to do on the command line.

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Although that link is named "USB Drive" , the command line options work for any partition.

See also :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by jtarin on 2010-09-18
> **wilee-nilee said:**
> Funny label is off on my mounted partitions. I have to say though dealing with you is like looking in a mirror.;)
On your best day.

---

