---
title: "Organising ur computer with Ubuntu."
date: 2010-03-22
forum: New to Ubuntu
---

### Post by sinhanikhil.5 on 2010-03-22
***Hi all Ubuntu users,***

***Now i have already started with Ubuntu, need few more ideas to make it better.***
***As I am a very long term Windows user I am bound to compare between two.***
***For example i had a very organised computer in windows, a drive for software, a drive for movies and songs and 1 for general stuff. How can i make same in Ubantu.***
***I still have windows in my system and all my songs and movies and also ebooks within it which i can't access using Ubuntu, so how can i do?***
***My ipod was recognised by Ubuntu player and also updated some package to access, which was excellent till the Ubuntu player rejected to play.***

***Also I also want to learn few cmd lines just to get started, where can i get free materials to do so?***
***I am also reading ubuntupocketguide by Keir Thomas.***


***Feedback welcomed.:)***

---

### Post by ndefontenay on 2010-03-22
Hi.

There's no more drives on linux. All you got is a home folder. That home folder is where everything personal for you is stored.

What you could do is create a folder for each and then put them as a shortcut in your places menu.

If that seems still too messy for you, you could go one step forward and use gpart to partition your hard disk and create specific partition for specific needs. I'm not sure this is really useful though.

It is quite useful to put your /home folder on a different partition but one partition per usage is a bit over the top.

Since you're totally new to ubuntu, it's good to know that the file system on Linux use EXT4 instead of NTFS. EXT4 does not create fragmentation. When you work on a file, it will work only inside your RAM until the point where you save your file. EXT4 will estime the disk space for the file and save it all as one long contiguous file. 

No fragmentation limits the need for partition really.

---

### Post by ndefontenay on 2010-03-22
For greater help, you can open a different thread for different problem.

For exemple you can open a new thread for your ipod and mplayer problem.

Give more detail. Explain what symptom you got. We can then help you more.

Nico

---

### Post by sinhanikhil.5 on 2010-03-22
Thx making a folder option is cool. U mean to say is only 1 drive and under that sub-folders for ur respective needs. Do u know how to use Empathy option and gnome?
I have assigned my gmail for empathy, it looks like MS Outlook.

---

### Post by Bradtek on 2010-03-22
I know this is Absoloute beginner Talk, but beginners PLEASE don't give false info.

> There's no more drives on linux. All you got is a home folder. That home folder is where everything personal for you is stored.

You CAN have different drives only Linux does not call them C: D: etc
Partition your hard drive/s how you like .. to make it easier to recognise give the partitions Labels like Music or Movies or Stuff.

You CAN access Windows NTFS Drives / Partitions

If you can't then either something is wrong or you are doing something wrong.
Quite probably you just haven't mounted the drives.

> 
Do u know how to use Empathy option and gnome?
I have assigned my gmail for empathy, it looks like MS Outlook. 

Huh ?

Empathy is a multi protocol Instant Messaging client, 
like Windows live messenger or Yahoo messenger

Gnome is the Desktop Environment and associated apps that comes with it.

Are you sure you don't mean Evolution looks like MS Outlook ?

---

### Post by Elfy on 2010-03-22
You can use pysdm to connect your windows drives 

[http://ubuntuforums.org/showpost.php?p=5470813&postcount=1](http://ubuntuforums.org/showpost.php?p=5470813&postcount=1)
[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

It is available in the repos - so search for it in Ubuntu Software Centre or install it from the command line with

```
sudo apt-get install pysdm
```

I have 12 or so different drives/folders connecting at boot.

---

### Post by 3rdalbum on 2010-03-22
You can't have programs on a seperate drive on Ubuntu, due to the way that software generally works. Different parts of your programs are installed to different parts of the filesystem so they can be easily found by different programs that need to access this information. This is a strength of Linux - programs share code resources so they take up less space and are easier to manage.

As for your different drives for movies and music and stuff, that's well and truly easy to accomplish.

In order to play MP3 files you need to install an MP3 codec. You should be given the option to do this when you first try playing an MP3.

---

### Post by Gregorybekkers on 2010-03-22
It's not needed to store progs on a diffrent partition anyways cause Linux doesn't work like windows..
so it doesn't make your computer much slower..

you can just access your drives in ubuntu.

---

### Post by Paqman on 2010-03-22
+1 for pysdm. You should have no trouble accessing your Windows partitions and all your data using it.

---

### Post by sinhanikhil.5 on 2010-03-25
Thank you so much to all for the reply.

---

