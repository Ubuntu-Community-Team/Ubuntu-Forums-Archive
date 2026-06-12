---
title: "Run fsck manually"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by Ludwig9 on 2009-04-16
I get this message when I start up. Can this problem be eliminated simply by reinstalling 8.10 or by installing 9.04? As it is, I can't get into TERMINAL (or anything else). I am running a dual install with Windows XP, and have no problem in windows. Therefore I don't think the harddrive is bad. I have read another thread started by Trinian, who had the same problem 3 weeks ago (I don't have the link at the moment). I am not worried about losing data. 
How does one get into maintenance mode?

[QUOTE]/dev/sda7: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(that is, without –a or –p options
fsck died with exit status 4
An automatic file system check (fsck) of the root file system failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root file system mounted in read-only mode. 
The root file system is currently mounted in read-only mode. A maintenance shell will now be started. After performing system maintenance , press CONTROL-D to terminate the maintenance shell and restart the system.
Bash: no control in this shell
/QUOTE]

---

### Post by Ludwig9 on 2009-04-16
Here is Trinian's thread.
[http://ubuntuforums.org/showthread.php?t=1101526&highlight=maintenance+mode](http://ubuntuforums.org/showthread.php?t=1101526&highlight=maintenance+mode)

---

### Post by billgoldberg on 2009-04-16
> **Ludwig9 said:**
> I get this message when I start up. Can this problem be eliminated simply by reinstalling 8.10 or by installing 9.04? As it is, I can't get into TERMINAL (or anything else). I am running a dual install with Windows XP, and have no problem in windows. Therefore I don't think the harddrive is bad. I have read another thread started by Trinian, who had the same problem 3 weeks ago (I don't have the link at the moment). I am not worried about losing data. 
How does one get into maintenance mode?

[QUOTE]/dev/sda7: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(that is, without &#8211;a or &#8211;p options
fsck died with exit status 4
An automatic file system check (fsck) of the root file system failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root file system mounted in read-only mode. 
The root file system is currently mounted in read-only mode. A maintenance shell will now be started. After performing system maintenance , press CONTROL-D to terminate the maintenance shell and restart the system.
Bash: no control in this shell
/QUOTE]

Well the errors says a maintance shell will be opened. 

And it should (I have seen lots of those when my netbook was running ext2).

just run

```
sudo fsck
```

when you get into the shell.

I'm guessing you could do the same from a live cd should by some reason you don't get the shell.

Start the Ubuntu live cd.

Mount your internal hard drive (using the file manager for instance).

Open up a terminal and do

```
sudo fdisk -l
```

then check to see which is the linux one 

Lets says it's /dev/hda1

You would then run 

```
sudo fsck /dev/hda1
```

I haven't actually done this, but I don't see a reason why it shouldn't work.

---

### Post by Herman on 2009-04-16
My ideas are, if your computer can boot a Ubuntu live CD or a Ubuntu USB, the easiest way for beginners is to open 'System'-->'Administration'-->'Partition Editor', take a look around and see which file system you want checked. Right-click on it and click 'check' from the right-click menu.
Here's a link I made which explains that more, [Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_")**.**

Slightly more advanced users may want to see what file systems they have, (if they don't remember), and run the appropriate file system check manually from a terminal.
```
sudo blkid
``````
sudo e2fsck -C0 -p -f -v /dev/sda2
```Where: '/dev/sda2' is the correct partition number for the file system you want to have checked. Please look at the blkid output and replace '/dev/sda2' with whatever partition number is appropriate.

The command 'e2fsck' is the specific file system check for the ext series of file systems and it can fix more errors when run manually than it can when it's run though fsck. At least that's how things seem to me. Most of the time, that will actually fix all your file system errors.

If that doesn't fix it, it will tell you and it will give you advice about what to do next.
Here's a link in case you need more info, [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem")

Here's a link about how to run a manual file system check on a reiser file system, [Running a filesystem check on a reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_on_a_reiserfs")

Regards, Herman :)

---

### Post by Ludwig9 on 2009-04-17
Thanks to both of you, BillGoldberg and Herman.
My problem seems to be solved, although I haven't done exactly what either of you recommended. It's a long story but basically this is what I did. 
I tried running from a live CD but the menu under Applications did not contain Accessories/Terminal. It contained only:
Help
Edit Menus
- remove panel
Move
[] Lock to Panel

So I could not run: sudo fsck -1

I installed jaunty in the hope that that would fix the problem (I was previously using Ibex). But that did not work. Even after the installation, while keeping the previous partitions as they were, it would not boot up. I had tried to change the size of the partitions since I previously had only 8 MB for swap, but it kept telling me when I tried to change the size of the partitions, that I would have to go back and change this and that. In any case I ended up keeping all the partitions as before, but without success. I then reinstalled Ibex, but this time managed to change the size of the partitions: in brief, I discovered that the only way to change the size of old partitions is to delete them and then re-create them. I did this and managed to give about 2000 MB to the swap partition. In any case all seems to be fine now. 
I did however go into Terminal and run: sudo fdisk -1
I took a screenshot of it but have forgotten how to add it here. 
Remind me how to do that and I will post it here. Thanks.

---

### Post by Herman on 2009-04-17
:) You are doing well, Ludwig9, but I'm guessing there might be something a little different about your computer that may be making things seem a little more difficult for you than they normally should be. I'm not sure what it is.

If you click on 'System', and you got 
> Help
Edit Menus
- remove panel
Move
[] Lock to Panelyou could have some kind of a problem with your mouse being recognized and set up correctly in hardware. I'm just guessing that because that's the menu I get when I right-click on any of the menus in my top panel, so it seems as if your computer is interpreting your right-click as a left-click. Maybe I'm wrong, I'm not sure.

Another thing I remember happening to me not long ago after showing a movie with my little EeePC through a video projector. The EeePC has only a very small screen, and normally runs at only 800 x 480 resolution.
It changed its resolution or I changed it when configuring it for dual screens to get the best movie picture, which was perfect at the time for seeing the movie.
After that though, I had everything all mixed up for a while and when I clicked on a menu, (or thought I was clicking on a menu), I would get some different menu or no menu at all. I fixed that by going 'System'-->'Preferences'-->'Screen Resolution', and playing around in there for a bit. There are all kinds of magical settings in there, it's great! Anyway, all I needed to do was set a lower resolution. There are wonderful settings in there for doing all kinds of tricks with our displays. I'm not sure, but if you're having problems getting the menu you want when you click on in, it could have something to do with the way your display is set up, (screen resolution), maybe?

Anyway, to answer your question, an easy way to post us information is to copy the terminal output with your mouse and just paste it into your reply (post). If you want, you can highlight it afterwards and click on the little # symbol and that will 'wrap code tags around the selected text', meaning it will appear in a special rectangle when you hit the 'Preview Post' button, below where you're typing, or after you click 'Submit Reply'. 
That's a lot easier and better than posting a screenshot. Screenshots are good sometimes but text is better. With text, I can easily copy your fdisk output into my own computer and paste it into a text file and play with it and re-arrange it as I please and add my own comments to it to help me make sense out of it, (analyse it) for you.
Another tip is, you can copy commands you see in Ubuntu Web Forums and other how-tos and paste them into your terminal to save typing them by hand. You should think about what each command will do first, but generally most people will only post safe commands, or if they might do anything bad, they'll come with a warning or explanation.
The command 'fdisk -l' is to list some information about your hard disk (partitions), so it's '-l' for 'list, and not a number 1.
The 'fsck' command is to run a file system check, but the 'fdisk' command is for starting a partition editor. billgoldberg gave you the right commands, so you can just copy those if you like and you'll be fine.
You are doing very well though, and the best thing to do is to be persistent and in a while it'll all make sense and seem easy after a bit of practice. The main thing is to keep on trying. 

Regards, Herman :)

---

### Post by Ludwig9 on 2009-04-17
Thanks, Herman.
I appreciate your confidence in me, but the problem with the mouse was undoubtedly my fault: I usually use the mouse left-handed (though I switch back and forth often) and after the new installation, Ubuntu was probably set up for a right-handed user. I should have known.

---

### Post by Herman on 2009-04-17
:) Oh, alright, that's okay. 
I hope you'll have good luck with having your file system checked and fixed.

Most things are easy in Ubuntu nowadays, the developers have been putting a lot of work into Ubuntu and all the software associated with it too. Some of those old error messages could be getting a little dated.
> fsck should be performed in maintenance mode with the root file system mounted in read-only modeProbably that old advice comes from way back before there was any such thing as a Ubuntu 'Desktop' Live CD, and user freindly apps like Gnome Partition Editor. :)

---

### Post by tokico on 2009-04-17
Just use

--
sudo fsck /dev/sda7
--

As simple as that.

---

