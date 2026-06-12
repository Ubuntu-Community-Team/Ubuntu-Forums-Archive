---
title: "question: how to install windows onto a different hdd after installing ubuntu..."
date: 2010-12-22
forum: New to Ubuntu
---

### Post by TuLesto on 2010-12-22
Greetings to you all, 

I cannot seem to find an answer tailored to my question. 

I would like to install Windows after installing Ubuntu 10.10... not only do I want to install it, I want to install it onto another hard drive separate to the one Ubuntu is currently running on. I do still want to have the choice of choosing which OS to run. How can I make this possible.

I have three hard drives. All of them are of the same brand and are the same model number. The third will become my internal backup drive if I may call it that. 

Thank you for your time.

---

### Post by TuLesto on 2010-12-22
Is no body willing to answer? did I say something I shouldn't have?

---

### Post by oldfred on 2010-12-22
We all are volunteers here and different people have different interests. Some are on line more than others and from many parts of the world. Some posts may not get reponses for a day, and then you can bump it to get back to the top of the list.

Should not be an issue. I have windows XP on my sda, and Ubuntu installed on both sdb & sdc. I set up windows to have its boot loader on that drive so it boots even if the other drives do not. Same for sdb, it is set up with grub2 to primarily boot the install in sdb. Likewise sdc. Grub2 is very good at finding other systems and will let you boot just about anything.

I find it better if windows is installed to the first drive. If drives are identical that can be somewhat of an issue. I have two 160GB drives and cannot tell them apart in BIOS, but have learned the one on top, first is sda and my windows install. Originally I had to experiment with booting each drive to see which drive was windows and which Ubuntu.

Some suggest unplugging the other drives. Windows will install its boot loader and probably install it to the 'first' drive, if not the one you install to. (Ubuntu's grub does the same thing, if you do not specify, windows does not give you a choice).  

With multiple installs & multiple drives I find this tool very useful. It shows what boot loader is in which MBR, but grub sometimes lies and the drive # shown is not correct. I run this both before & after any repartitioning or system change.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by TuLesto on 2010-12-22
Wow oldfred, thank you. My apologies for being impatient, the Ubuntu community has been nothing but kind to me. 

Thank you for your input.


> **oldfred said:**
> We all are volunteers here and different people have different interests. Some are on line more than others and from many parts of the world. Some posts may not get reponses for a day, and then you can bump it to get back to the top of the list.

Should not be an issue. I have windows XP on my sda, and Ubuntu installed on both sdb & sdc. I set up windows to have its boot loader on that drive so it boots even if the other drives do not. Same for sdb, it is set up with grub2 to primarily boot the install in sdb. Likewise sdc. Grub2 is very good at finding other systems and will let you boot just about anything.

I find it better if windows is installed to the first drive. If drives are identical that can be somewhat of an issue. I have two 160GB drives and cannot tell them apart in BIOS, but have learned the one on top, first is sda and my windows install. Originally I had to experiment with booting each drive to see which drive was windows and which Ubuntu.

Some suggest unplugging the other drives. Windows will install its boot loader and probably install it to the 'first' drive, if not the one you install to. (Ubuntu's grub does the same thing, if you do not specify, windows does not give you a choice).  

With multiple installs & multiple drives I find this tool very useful. It shows what boot loader is in which MBR, but grub sometimes lies and the drive # shown is not correct. I run this both before & after any repartitioning or system change.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by TuLesto on 2010-12-22
Wow oldfred, thank you. My apologies for being impatient, the Ubuntu community has been nothing but kind to me. 

Thank you for your input.


> **oldfred said:**
> We all are volunteers here and different people have different interests. Some are on line more than others and from many parts of the world. Some posts may not get reponses for a day, and then you can bump it to get back to the top of the list.

Should not be an issue. I have windows XP on my sda, and Ubuntu installed on both sdb & sdc. I set up windows to have its boot loader on that drive so it boots even if the other drives do not. Same for sdb, it is set up with grub2 to primarily boot the install in sdb. Likewise sdc. Grub2 is very good at finding other systems and will let you boot just about anything.

I find it better if windows is installed to the first drive. If drives are identical that can be somewhat of an issue. I have two 160GB drives and cannot tell them apart in BIOS, but have learned the one on top, first is sda and my windows install. Originally I had to experiment with booting each drive to see which drive was windows and which Ubuntu.

Some suggest unplugging the other drives. Windows will install its boot loader and probably install it to the 'first' drive, if not the one you install to. (Ubuntu's grub does the same thing, if you do not specify, windows does not give you a choice).  

With multiple installs & multiple drives I find this tool very useful. It shows what boot loader is in which MBR, but grub sometimes lies and the drive # shown is not correct. I run this both before & after any repartitioning or system change.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by oldfred on 2010-12-22
Herman has a complete page on installing to a second drive:

Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

Once you have windows installed all you have to do in Ubuntu is this and it should find your windows install and let you boot it. I like to make the Ubuntu drive second and change BIOS to boot the Ubuntu drive.

sudo update-grub

---

### Post by amjjawad on 2010-12-23
> **TuLesto said:**
> Is no body willing to answer? did I say something I shouldn't have?

You're very luck that oldfred was the first to answer your questions. It's so hard to add more info whenever oldfred is there :)
Yes, he's one of the best who could help you!

Good luck :)

---

### Post by theasprint on 2010-12-23
Hi,

I am not sure if others had this experience.

Last time i tried installing Ubuntu and then installing Windows, but ended up my PC boots straight to Windows, just as if Windows "ate up" my Ubuntu installation
To be more specific, Ubuntu and Windows are in the same hard drive but in 2 different partitions. 

So from that condition, I assume I should have reinstalled grub? (Because that was what I didn't do last time)

---

### Post by amjjawad on 2010-12-23
> **theasprint said:**
> Hi,

I am not sure if others had this experience.

Last time i tried installing Ubuntu and then installing Windows, but ended up my PC boots straight to Windows, just as if Windows "ate up" my Ubuntu installation
To be more specific, Ubuntu and Windows are in the same hard drive but in 2 different partitions. 

So from that condition, I assume I should have reinstalled grub? (Because that was what I didn't do last time)

You need to start your own thread as this will cause some confusion.

On my signature, there's a guide for Dual-Booting. Check the steps in Scenario 1. You'll come to know what's wrong.

_**Edit: **_Ops, I'm so sorry :( I didn't start writing about that case yet.
So YES, you need to re-install GRUB2. [This is how]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

---

### Post by TuLesto on 2010-12-23
thanks for the luck I am figuring this out It is nice working with ubuntu again. oldfred definitely seems wise. I do though appreciate all the replies, since I need all the help I can get.

I'm halfway there now. I was battling it out using disk utility all by myself. took me till now (with the exception of lunch supper and everything in between) to get the right configuration for another master drive. It has been a long time since the last time I played around with a computer indeed.

> **amjjawad said:**
> You're very luck that oldfred was the first to answer your questions. It's so hard to add more info whenever oldfred is there :)
Yes, he's one of the best who could help you!

Good luck :)

---

### Post by amjjawad on 2010-12-23
> **TuLesto said:**
> thanks for the luck I am figuring this out It is nice working with ubuntu again. oldfred definitely seems wise. I do though appreciate all the replies, since I need all the help I can get.

I'm halfway there now. I was battling it out using disk utility all by myself. took me till now (with the exception of lunch supper and everything in between) to get the right configuration for another master drive. It has been a long time since the last time I played around with a computer indeed.

You welcome :)
I was about to reply because I have done that before, I mean, I installed Windows while Ubuntu was installed but my case was a bit different and when I saw oldfred's posts, I didn't want to jump in :)
He's very professional in this field.

---

### Post by TuLesto on 2010-12-23
I really thought I had gotten it right. The windows install disc isn't recognising the HDD. It seems as though I will have to throw in the towel and go to bed. Tomorrow I will read this and consider it a early Christmas gift from oldfred. 

> **oldfred said:**
> Herman has a complete page on installing to a second drive:

Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

Once you have windows installed all you have to do in Ubuntu is this and it should find your windows install and let you boot it. I like to make the Ubuntu drive second and change BIOS to boot the Ubuntu drive.

sudo update-grub

---

### Post by Verbeck on 2010-12-23
well.... here's what i do
edit : its just a reapeat
1. unplug the ubuntu hard disk 
2. install windows on the other
3. connect the first one 
4. change the boot order, so ubuntu loads first 
5. run sudo update-grub

edit : didn't read the whole thread first; looks like its already posted

---

### Post by oldfred on 2010-12-23
If windows is not seeing the drive, you may have other formated partiitons? Windows will install to a empty drive or to NTFS primary partition with the boot flag.  If you have other partitions already on drive you should remove or modify to make room for windows.

To see your partitions, from Ubuntu or Linux liveCD.

```
sudo fdisk -l
```

---

