---
title: "Partition Hard Drive Help"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by stktek on 2010-12-29
Need some help. I want to partition my HD and move my home folder to the new partition and them update to 10.10 Not to sure how to do this as I am not very computer smart. I have installed GParted but am lost at how to do this with out loosing all my stuff.

---

### Post by SuaSwe on 2010-12-29
[color="RED"]Before playing with GParted, all data should be backed up - please beware of the risks involved![/color]

If I were in your position and did not have a removable HDD (in which case you could just back up your stuff and reinstall afresh!), I would shrink the current HDD to, say, 300GB (e.g. enough to fit all current data), then once you have a bunch of lovely unallocated space... Actually, just found a lovely article that explains it beautifully:

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

Just beware as mentioned above though that data loss is always possible when manipulationg partitions, so at the very least you should back up anything irreplaceable.

---

### Post by frustratednerd on 2010-12-30
> **stktek said:**
> Need some help. I want to partition my HD and move my home folder to the new partition and them update to 10.10 Not to sure how to do this as I am not very computer smart. I have installed GParted but am lost at how to do this with out loosing all my stuff.
Not sure how to partition with GParted (but I'm gonna try and figure out), but once you finally get to partition your drive...to move /home/ to one of the new partitions, go to terminal and type out:

```
sudo cp /home/ /dev/sda[number]
```

where [number] is the number of the new partition.

---

### Post by SuaSwe on 2010-12-30
> **frustratednerd said:**
> 
```
sudo cp /home/ /dev/sda[number]
```
where [number] is the number of the new partition.

I would bet against this - the new partition needs to be mounted first, but cannot be called /home as there is already one, then the old one needs to be removed... I'd follow the advice in the article I linked above, it's nice and concise. :)

---

### Post by frustratednerd on 2010-12-30
> **SuaSwe said:**
> I would bet against this - the new partition needs to be mounted first, but cannot be called /home as there is already one, then the old one needs to be removed... I'd follow the advice in the article I linked above, it's nice and concise. :)
Right. It didn't hit me that he/she was trying to make a separate partition for /home, even though it was in plain sight. Thanks for reminding me.

---

### Post by Bucky Ball on 2010-12-30
You will need to do this from a LiveCD as the partition you want to shrink is running your OS, therefore cannot be unmounted, and if you can't unmount it, you can't shrink it.

As mentioned, BACK UP anything irreplaceable.

I would also kill the extended partition while you are at it. It only contains /swap. This will kill /swap as well but just make another.

---

### Post by Idefix82 on 2010-12-30
> **SuaSwe said:**
> the new partition needs to be mounted first, but cannot be called /home as there is already one, then the old one needs to be removed...

This shouldn't be an issue since the OP wants to install a new version of Ubuntu afterwards anyway. But the command will not work for another reason: you need to preserve all the file attributes, otherwise you will become the owner of the copy, which is not what you want.

So the easiest thing to do would be: create a new partition with gparted, mount it as anything you like (say /temp), move the entire /home folder to that partition with
```
sudo cp -rp /home /temp
```
then do a fresh install of 10.10, choose "manual partitioning" during the install, tell the installer to use the newly created partition for /home but **do not check the "format" box.** Also give the installer a partition for / (root) and one for swap. Feel free to report back on your progress.

And I second SuaSwe's warning: backup before you create the new partition.

---

### Post by SuaSwe on 2010-12-30
Further to Bucky Ball's message, if your PC doesn't have a CD/DVD drive, you can also use a LiveUSB (creatable using System > Administration > Startup Disk Creator). :)

---

### Post by Bucky Ball on 2010-12-30
> **suaswe said:**
> further to bucky ball's message, if your pc doesn't have a cd/dvd drive, you can also use a liveusb (creatable using system > administration > startup disk creator). :)

+1

---

### Post by hello2012 on 2010-12-30
[FONT=Times New Roman][SIZE=3]I wonder to know if your OS is Windows. If so, I suggest you use Partition Assistant to partition hard drive, if your OS is 32 bit, you can use its [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3][COLOR=#800080]free partition manager[/COLOR][/SIZE][/FONT]]("http://www.extend-partition.com/free-partition-manager.html")[FONT=Times New Roman][SIZE=3] too. No matter this can help you or not, at least you can think this tool to help you finish the further operations if necessary.[/SIZE][/FONT]

---

### Post by SuaSwe on 2010-12-30
Look everyone, it's a Windows user! GET HIM!!! 

(Joke. ;) )

---

### Post by Bucky Ball on 2010-12-30
> **hello2012 said:**
> [FONT=Times New Roman][SIZE=3]I wonder to know if your OS is Windows. If so, I suggest you use Partition Assistant to partition hard drive, if your OS is 32 bit, you can use its [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3][COLOR=#800080]free partition manager[/COLOR][/SIZE][/FONT]]("http://www.extend-partition.com/free-partition-manager.html")[FONT=Times New Roman][SIZE=3] too. No matter this can help you or not, at least you can think this tool to help you finish the further operations if necessary.[/SIZE][/FONT]

My friend, take a closer look at the screen shot. They are EXT4 partitions; clearly Linux partitions. Not an NTFS or FAT partition to be found ...

---

### Post by stktek on 2010-12-30
Only Ubuntu on my HD do not like windows as it always crashed on me. Although I am very nervous about doing the upgrade to 10.10 and still trying to understand what is going on. I do not have another drive to back up on and my home folder has 100gig of stuff. This is why I want to partition so that for future upgrades things might go simpler for me.
I am reading all the links sent and trying to understand it all;:confused:

---

### Post by SuaSwe on 2010-12-30
Before you do anything else, just for your own peace of mind, do you have any CD's/DVD's you can burn with all your most important data? The vast majority of the time your data will survive completely intact, but just in case it's best to have those irreplaceable files backed up!

Once you have done, start with first shrinking your current partition to make room for the new stuff. There are plenty of step-by-step instructions available, and if you don't understand anything I'm sure lots of people here will be happy to explain it all. :)

---

### Post by Idefix82 on 2010-12-30
To add to what SuaSwe said, once you have shrunk your partition successfully, almost nothing can go wrong for you. Shrinking the partition is the part that sometimes (very rarely) causes loss of data. After that, just don't misclick and check back here before doing things you don't understand and you will be fine.

---

### Post by Bucky Ball on 2010-12-30
Bit late in the thread but just wondering: Why do you want to upgrade to 10.10??? 10.04 LTS is a long term support release; extra year of support on 10.10 and more stable.

You may ask, "Well, Bucky's running 10.10!" My reply: it is the only kernel that runs on my new Toshiba Satellite Pro. I would be using 10.04 if I could. There are three other computers in the house and two are 10.04, the other still on 8.04. All LTS releases.

---

### Post by Sky Aisling on 2010-12-30
Thanks everyone for this helpful discussion thread.


@SuaSwe,
Thank you for the reference: [http://embraceubuntu.com/2006/01/29/...own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")

@stktek,
Did we mention, [SIZE=4]b a c k  u p[/SIZE]  your stuff?  ;)

---

### Post by stktek on 2010-12-30
Thanks for all the info. 
I will be buying a external HD and back everything up first before trying to partition.

---

### Post by Sky Aisling on 2010-12-30
@stktek

PS -  an aside
This comment is not related to partitioning but to backing up your stuff.

If you are using Firefox browser, and, you are wondering how to save your bookmarks here's a discussion that may be helpful:

[http://ubuntuforums.org/showthread.php?t=1193567&page=69](http://ubuntuforums.org/showthread.php?t=1193567&page=69)

---

### Post by hello2012 on 2011-01-04
> **Bucky Ball said:**
> My friend, take a closer look at the screen shot. They are EXT4 partitions; clearly Linux partitions. Not an NTFS or FAT partition to be found ...
 yeah, sorry about the mistake i made.

---

### Post by Bucky Ball on 2011-01-04
> **hello2012 said:**
> yeah, sorry about the mistake i made.

;) I've made plenty. No worry. ....

Can't learn much if we don't make mistakes, ay? 

As for backing up Firefox bookmarks:

Bookmarks->Organise Bookmarks->Import and Backup

---

### Post by li7anyushen on 2011-10-02
> ** said:**
> 
&#12288;&#34915;&#21407;&#20307;&#23545;&#28909;&#25935;&#24863;&#65292;[&#39282;&#26009;](http://shop34896557.taobao.com)&#65292;&#22312;60&#8451;&#20165;&#33021;&#23384;&#27963;5&#65374;10&#20998;&#38047;&#12290;&#34915;&#21407;&#20307;&#32784;&#20919;&#65292;[&#23456;&#29289;&#40479;--petbird](http://shop34896557.taobao.com)&#65292;&#22312;-70&#8451;&#21487;&#20445;&#23384;&#25968;&#24180;&#65292;[&#40550;&#40521;](http://shop34896557.taobao.com)&#65292;&#20919;&#20923;&#24178;&#29157;&#21487;&#20445;&#23384;30&#24180;&#20197;&#19978;&#12290;&#24120;&#29992;&#28040;&#27602;&#21058;&#20063;&#33021;&#36805;&#36895;&#26432;&#28781;&#34915;&#21407;&#20307;&#65292;&#22914;75%&#20057;&#37255;0.5&#20998;&#38047;&#25110;2%&#26469;&#33487;&#28082;5&#20998;&#38047;&#22343;&#21487;&#23558;&#20854;&#26432;&#27515;&#12290;&#32418;&#38665;&#32032;&#12289;&#24378;&#21147;&#38665;&#32032;&#21644;&#22235;&#29615;&#32032;&#31561;&#26377;&#25233;&#21046;&#34915;&#21407;&#20307;&#32321;&#27542;&#30340;&#20316;&#29992;&#12290;&#30456;&#20851;&#30340;&#20027;&#39064;&#25991;&#31456;&#65306;      [&#25991;&#40479;&#32321;&#27542;&#26102;&#38388;&#21021;&#25506;](http://blog.cersp.com/index/2249551.jspx?articleId=21784755)

---

