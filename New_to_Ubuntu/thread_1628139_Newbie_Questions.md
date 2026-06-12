---
title: "Newbie Questions"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by wickeddd on 2010-11-22
Hi all,

Im fairly new to the whole linux scene after being a big windows user I wanted to try something else. Im having some trouble adjusting but im liking it :)
Few questions that may seem stupid.
1. I have realized now that I partitioned my hard drives ridiculously high and wanting to make it smaller. I have installed G-Parted & when I try to "Move or Resize" the option is unavailable. I have also tried partitioning it from windows and that doesn't work either. What have I done wrong?

2. I am unfamiliar with where things are stored in ubuntu, I know that my documents and such are stored in my home folder but when I install programs and such, where are they installed into?

3. When I look in "Computer" I see 2 unfamiliar hard drives. 'SYSTEM RESERVED' and 'File System' What are they??

4. My 3D cube isn't a cube, its a cylinder. Why is that?

I have a decent knowledge of the terminal thanks to reading many guides from this forum.

Cheers, wick.

---

### Post by guildofghostwriters on 2010-11-22
I can't answer all your questions. However...

1. are you logging your installed Ubuntu to use gparted? You need to boot into the live cd and use gparted there - you can't change a partition if the hard drive is mounted and you can't boot into your installed ubuntu without mounting hence the need to do it from the live cd.

2. sorry

3. file system is the mounted hard drive that ubuntu is using - click into it & you'll be in / (root). I'm guessing but the other one might be something to do with a windows installation, perhaps some kind of system restore thingy, but I'm guessing.

4. mine is too. I keep meaning to explore compiz config settings manager to see if I can work out why - just looked and there's nowt obvious.

---

### Post by nm_geo on 2010-11-22
How did you install Ubuntu?  Flash Drive?  I believe and have used my Ubuntu flash drive to change the partition sizes on my hard drive after the installation using my flash drive.  You need to be very careful if you have a Windoz partition and if you resize it .. Reboot the windoz program before you do anything else.  The chkdisk will run and reset the size of the windoz partition.  If all you do is change the Linux partitions you probably will not have to do that but I still reboot my windoz before proceeding.

---

### Post by QLee on 2010-11-22
[QUOTE=wickeddd]...
1. I have realized now that I partitioned my hard drives ridiculously high and wanting to make it smaller. I have installed G-Parted & when I try to "Move or Resize" the option is unavailable. I have also tried partitioning it from windows and that doesn't work either. What have I done wrong?[/QUOTE]
I'd guess that you're trying to do it on mounted volumes (partitions), which, if you think about it, wouldn't be a good idea. Try from the Live CD gparted. But be careful and backup first.

[QUOTE=wickeddd]2. I am unfamiliar with where things are stored in ubuntu, I know that my documents and such are stored in my home folder but when I install programs and such, where are they installed into?[/QUOTE]
Have a look at this:
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html)
or, enter the command, man hier, in a terminal window.


[QUOTE=wickeddd]3. When I look in "Computer" I see 2 unfamiliar hard drives. 'SYSTEM RESERVED' and 'File System' What are they??[/QUOTE]
Presumably, a windows volume (partition). 

Second (third, and fourth) Edit: I should have added this with the last edit because it won't be clear for a new user. Stuff is often installed when OEMs install Windows to a brand new drive. Not strictly needed but don't delete  without doing a forum search using those terms as keywords and following the advice of knowledgeable users. File system is going to be Ubuntu. I should learn to read more carefully, I have a valid excuse but it isn't important to you. If you have looked at the hierarchy you'll understand File System. Sorry, I'm recovering from surgery last Monday, my thoughts are scattered and slow, you deserve better answers than I am giving.

[QUOTE=wickeddd]4. My 3D cube isn't a cube, its a cylinder. Why is that?[/QUOTE]
Don't know, I don't use it, but you might want to mention how many desktops you are using. Some user will come along to help you with this question.


Edit: I forgot to state welcome to the forum, but I often forget to write that.

Fifth edit: I suggest you post the 4th question just as it stands, as a new thread, it might get lost in this thread, I expected someone to answer before now. As a new question, it will attract attention from those who can help more easily than bumping this thread.

---

### Post by lobralleo on 2010-11-22
I am only addressing you question n. 4, since the other three have been covered already.

You can control your desktop effects by installing simple-ccsm or compizconfig-settings-manager, which will give you direct control over composite effects with a graphical interface.

The first package is a somewhat stripped down control center, while the second is a more complete interface to the configuration and will really allow you to control every element of the animations.

Hope this helps!

---

### Post by BobSongs on 2010-11-22
For Question 3:

**File System** is the display of your entire file system. 

Ubuntu (and many other distributions of Linux) realizes you really want to manage the files under your **home folder**:  /home/[current user]. So displaying everything isn't necessary most of the time.

Under Windows XP, the root drive is broken up into 3 folders:

[LIST]
[*]Windows
[*]Program Files
[*]Documents and Settings
[/LIST]
Neat and tidy.

However, Linux tends to have a few more basic root folders, such as

[LIST]
[*]bin
[*]boot
[*]cdrom
[*]dev
[*]etc
[/LIST]
and so on. Other than **/home**, you are not allowed to manage many of these folders and files (unless you give yourself the rights of the administrator), so why display them by default? Therefore they're kept out of the way for your convenience.

---

### Post by BobSongs on 2010-11-22
Answer to Question 4:

In the Compiz configuration, once the 3D box setting is selected, there's a further subsetting allowed elsewhere that enhances the box by letting it become a cylinder. This can be unchecked.

For a fuller answer, see my second answer to Question 4

---

### Post by BobSongs on 2010-11-22
Answer to Question 2:

Just as in Windows, files and settings are distributed throughout the file system, depending on the software.

In Windows, the typical application setup will have files put in **/Program Files**. A new folder created along with many sub folders. Add to that some **.dll** files tossed in **/WINDOWS/System32** and fonts in **/WINDOWS/fonts**... on and on. The installation ends with numerous settings added to the Windows Registry. Fine.

In Linux, files are placed in various system folders too. There's no *one folder*. The key thing to note here is the following:

Since Linux has no registry, this to your advantage. Information that would be added to the Windows Registry are added to your** /home **folder. These entries are created and placed in hidden files/folders. They're hidden from view by giving each file or folder a leading dot (**.groumet**, **.inkscape**, etc.). Why is this an advantage?

If you create a set of partitions along the following lines, re-installing Linux becomes a breeze:

[LIST]
[*][Windows NTFS Partition for your current version of Windows]
[*][Linux system partition, usually known as / or 'root']
[*][Linux Swap]
[*][Linux /home]
[/LIST]
Others may argue vehemently for a "better" distribution of partitions... but for the beginner turning intermediate, this isn't a bad choice. Here's why.

Should your Linux system fail you due to excessive tinkering or something gone horribly wrong (power failure stops the O/S from booting -- happened to me), a simple re-install with the same partition structure selected will let you have your familiar work station back in just a few minutes. Do not choose to format **/home** when designating that last partition. Just tell the Ubuntu installer what file system you chose (Ext2, Ext3, Ext4, etc) and tell it that it should be known the overall file system as **/home**.

You're good to go. Since **/home** contains your preferences, this results in things like:

[LIST]
[*] Firefox has all it's bookmarks and browsing history intact
[*] Recipe software has all it's recipes
[*] Application settings are all preserved
[*] Desktop has all its files and folders intact, right down to the background you chose
[/LIST]
 **Note:** Your Linux partition shouldn't be any bigger than 30GB (if you have a large hard drive) and your Linux Swap shouldn't exceed 1GB. But feel free to research the Linux Swap and what a good ratio is for the size of memory your system possesses.

---

### Post by wickeddd on 2010-11-22
Thank you, all of you.
You have really helped me understand linux better :)

---

### Post by BobSongs on 2010-11-23
Answer to Question 4:

Compiz has grown along with its many plug-ins. The installed set must've been growing too big for the "average user" so the number was pared down to a more manageable size. 

However, you can manage all the old familiar eye-candy, along with a few new toys, after installing

**compiz-fusion-plugins-extra**

That can be done by opening a Terminal, and pasting the following text:

```
sudo aptitude install compiz-fusion-plugins-extra
```

Have fun.

---

