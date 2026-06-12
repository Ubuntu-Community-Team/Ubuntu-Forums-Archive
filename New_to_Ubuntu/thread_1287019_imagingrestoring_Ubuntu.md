---
title: "imaging/restoring Ubuntu"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by Don Bowen on 2009-10-09
I'm enjoying Ubuntu very much.  One of the first things I wanted to learn to do was how to image the Ubuntu partition on my laptop so that I could restore it if I had to.
On Windows that's done with software like Norton Ghost.  

So far, this is the best method I've found:

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

I read one article about using TAR (which behaves a lot like pkzip) to simply zip the entire hard drive.  It's a nice idea, and it produces a compressed file, but what do you do with that?  If I wipe out all the partitions on my HD, how would i use that compressed file to restore Ubuntu?  I suppose I could boot from the live CD, do a minimal install, then uncompress the backup file to the new partition?  That would work, probably.
(Here's the zipping approach article:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087))

the article above seems a more elegant approach, and I wanted to share it here!
What is your preferred method for imaging/restoring Ubuntu?

---

### Post by Sarmacid on 2009-10-09
It's very easy to create an image of your drives, just look up which one is it that you want and try ```
dd if=/dev/sda of=myfile.img
```

Personally I prefer the tar method, because the image of the hard drive will be the same size, and the tar will occupy much less. I've used it and to restore only needed to boot up with a live CD.

---

### Post by Zoot7 on 2009-10-09
Another great thing to do is use a seperate partition for home, so re-installing isn't nearly as time consuming having to tweak settings etc.
**[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")**

:)

---

### Post by LewRockwell on 2009-10-09
We make clones with Clonezilla

Even with catastrophic hard drive failure/theft/destruction we can be back up and running with the clone in minutes

.

---

### Post by Don Bowen on 2009-10-09
> **Sarmacid said:**
> It's very easy to create an image of your drives, just look up which one is it that you want and try ```
dd if=/dev/sda of=myfile.img
```

Personally I prefer the tar method, because the image of the hard drive will be the same size, and the tar will occupy much less. I've used it and to restore only needed to boot up with a live CD.
Yes, but how did you restore it using tar?  Wipe out both Ubuntu partitions and then??? what?

---

### Post by Don Bowen on 2009-10-09
> **Zoot7 said:**
> Another great thing to do is use a seperate partition for home, so re-installing isn't nearly as time consuming having to tweak settings etc.
**[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")**

:)
Wow!  I'm sure there are people who do wonderous things with CloneZilla....but I'm not one of them!
Inscrutable and very hard to use! (and I've done a lot of this kind of thing.)  After the third attempt to image a HD partition to a portable USB hard drive, just gave up.
Maybe the program will be better...when it's finished?  It's a little rough cut right now.

---

### Post by Don Bowen on 2009-10-09
> **Don Bowen said:**
> Wow!  I'm sure there are people who do wonderous things with CloneZilla....but I'm not one of them!
Inscrutable and very hard to use! (and I've done a lot of this kind of thing.)  After the third attempt to image a HD partition to a portable USB hard drive, just gave up.
Maybe the program will be better...when it's finished?  It's a little rough cut right now.
Using a separate partiton for "home" sounds interesting.  I do that all the time with windows by mapping "My Documents" to a separate data partition so that personal stuff doesn't get wiped out during a re-image.
Is it possible to locate "home" on another partition?  If so, how is that done?

---

### Post by MegaJim on 2009-10-09
Create new partition, make a copy of your /home directory into that parition, then setup a mount point for that partition in the /home directory (have a look at `man fstab` or read a guide somewhere on mount points)

Probably easiest from a live CD but recovery mode would work if you're familiar with the terminal.

---

### Post by Don Bowen on 2009-10-09
> **MegaJim said:**
> Create new partition, make a copy of your /home directory into that parition, then setup a mount point for that partition in the /home directory (have a look at `man fstab` or read a guide somewhere on mount points)

Probably easiest from a live CD but recovery mode would work if you're familiar with the terminal.
does the new "home" have to be a partition?  can it be a folder on another HD?

---

### Post by ramjet_1953 on 2009-10-09
I agree 100% with what LewRockwell had to say.

CloneZilla is a great piece of software that has the ability to make an exact clone of a hard drive, including GRUB.

Something really nice with CloneZilla is that it only copies sectors with data in them.

This speeds up the copy process dramatically.

I have always done this and had reason to be grateful late last year, when I had a catastrophic mechanical failure of my hard drive. 

I just opened the trapdoor of my laptop and replaced the failed HDD with the clone and was away again in just a few minutes.

Nothing beats a full-blown clone of your hard drive.

Regards,
Roger :)

---

### Post by MegaJim on 2009-10-10
It doesn't have to be a partition, you can create a symbolic link to your home on another drive using

```

cd /
sudo ln -s /mnt/other-drive/home

```

---

### Post by Don Bowen on 2009-10-12
> **ramjet_1953 said:**
> I agree 100% with what LewRockwell had to say.

CloneZilla is a great piece of software that has the ability to make an exact clone of a hard drive, including GRUB.

Something really nice with CloneZilla is that it only copies sectors with data in them.

This speeds up the copy process dramatically.

I have always done this and had reason to be grateful late last year, when I had a catastrophic mechanical failure of my hard drive. 

I just opened the trapdoor of my laptop and replaced the failed HDD with the clone and was away again in just a few minutes.

Nothing beats a full-blown clone of your hard drive.

Regards,
Roger :)
I disagree... CloneZilla isn't ready for prime time yet.  The best tools in the world are useless if you can't get people to use them.  CloneZilla's interface is non-existent, so even though it may be capable of doing great things, it's just too hard to use to be practical.

---

### Post by Don Bowen on 2009-10-12
> **MegaJim said:**
> It doesn't have to be a partition, you can create a symbolic link to your home on another drive using

```

cd /
sudo ln -s /mnt/other-drive/home

```
interesting... I executed that code with the folder I wanted to be the new "home"
and it had no effect on anything.
Home is still on the Ubuntu partition, and the 2ndHome folder I wanted doesn't show up anywhere?
What, exactly, does this code do?

OK...maybe "LN" stood for "Link Name" in your example?
Still, if I'm creating a link name... a) what is a link name, and b)what good does that do?

now, how do I get rid of Link names like "ln" in your example once I've created them?

---

### Post by Don Bowen on 2009-10-12
> **Don Bowen said:**
> interesting... I executed that code with the folder I wanted to be the new "home"
and it had no effect on anything.
Home is still on the Ubuntu partition, and the 2ndHome folder I wanted doesn't show up anywhere?
What, exactly, does this code do?

OK...maybe "LN" stood for "Link Name" in your example?
Still, if I'm creating a link name... a) what is a link name, and b)what good does that do?

now, how do I get rid of Link names like "ln" in your example once I've created them?
I suppose I should state the goal here more clearly.
I want to be able to remap the "home" folder sot that when I click on "Places" and "Home Folder" it goes to a folder on a different hard drive than Ubuntu lives on.
I could hope that programs would then save data automatically to this relocated home, rather than the home folder on the hard drive where I've installed Ubuntu.  
Thus, if I have to re-image the Ubuntu drive, I don't lose all the contents of the "home" folder.

---

### Post by crispy_420 on 2009-10-13
Did anyone mention dd to copy disc over?

---

### Post by MegaJim on 2009-10-13
That just creates a symbolic link with the name of the directory it is passed

In linux, the /home directory is where all of the users files and settings are stored, by name, so if i have two users called james and john on the system, their respective home directories will be at

/home/james
/home/john

you can use a symbolic link to remap these locations, however you should run in maintenance mode or be logged in as another user first so you don't break stuff.

e.g. for me i could create a symbolic link in /home

cd /home
sudo ln -s /mnt/other-drive/home-folder

so now when i list the contents of home with 

ls

i can see

/home/james
/home/john
/home/other-home

now i just have to move everything from /home/james to /home/other-home

shopt -s dotglob
sudo mv james/* other-home/

now i can remove the old home, and rename it so it matches my user name

sudo rmdir james
sudo mv other-home james

now you'll just want to make sure you own your own home directory

sudo chown james james

Any probs just ask.

---

### Post by HybridZero on 2009-10-13
I'll throw in another vote for Clonezilla. It beautifully handles reimaging for my ubuntu install and is a breeze to use.

---

### Post by Mark Phelps on 2009-10-13
If you just want a simple no-frills partition image backup/recovery app, check out P.I.N.G (Partimage Is No Ghost) at windowsdream.com.  It's a front-end to Partimage that allows for quick and easy backup/restore.  It's highly customizable through the use of a config file -- but I don't believe that it can do folder redirection as part of a restore.  It simply restores an entire partition.

---

### Post by tea for one on 2009-10-13
[QUOTE=Don Bowen;8079168]I'm enjoying Ubuntu very much.  One of the first things I wanted to learn to do was how to image the Ubuntu partition on my laptop so that I could restore it if I had to.
On Windows that's done with software like Norton Ghost.  

So far, this is the best method I've found:

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Good evening

I would suggest that Remastersys is a fine application to clone an image of your OS complete with any personal software choices.

Please take a look at this website for further info:-

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

The advantage of Remastersys is that the created image also automatically includes the Ubuntu installation software. 

i.e it is the same as using a live installation CD but including extra software that the user has added.

Secondly, I also agree that it is a good idea to create a separate partition for "Home" because you can the use Grsync (available via synaptic) to back up and restore your personal data.

---

### Post by CharlesA on 2009-10-13
> **LewRockwell said:**
> We make clones with Clonezilla

Even with catastrophic hard drive failure/theft/destruction we can be back up and running with the clone in minutes

.

I'll second/third Clonezilla. I used to use PING (see below), but it won't support EXT4.

> **Don Bowen said:**
> Wow!  I'm sure there are people who do wonderous things with CloneZilla....but I'm not one of them!
Inscrutable and very hard to use! (and I've done a lot of this kind of thing.)  After the third attempt to image a HD partition to a portable USB hard drive, just gave up.
Maybe the program will be better...when it's finished?  It's a little rough cut right now.

I've used the newest version of Clonezilla with no problems. The interface is GUI based (for the most part), and you just need to read the prompts and know what to do next.

> **Mark Phelps said:**
> If you just want a simple no-frills partition image backup/recovery app, check out P.I.N.G (Partimage Is No Ghost) at windowsdream.com.  It's a front-end to Partimage that allows for quick and easy backup/restore.  It's highly customizable through the use of a config file -- but I don't believe that it can do folder redirection as part of a restore.  It simply restores an entire partition.

Second this, I wasn't able to use it to backup LVM, but then again, I don't think I was supposed to be able to use it. :p

---

### Post by Don Bowen on 2009-10-15
> **tea for one said:**
> [QUOTE=Don Bowen;8079168]I'm enjoying Ubuntu very much.  One of the first things I wanted to learn to do was how to image the Ubuntu partition on my laptop so that I could restore it if I had to.
On Windows that's done with software like Norton Ghost.  

So far, this is the best method I've found:

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Good evening

I would suggest that Remastersys is a fine application to clone an image of your OS complete with any personal software choices.

Please take a look at this website for further info:-

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

The advantage of Remastersys is that the created image also automatically includes the Ubuntu installation software. 

i.e it is the same as using a live installation CD but including extra software that the user has added.

Secondly, I also agree that it is a good idea to create a separate partition for "Home" because you can the use Grsync (available via synaptic) to back up and restore your personal data.
Remastersys turns out to be the best of all the offerings.  Maybe I used the wrong version of CloneZilla, but it just looks terrible.

---

### Post by Don Bowen on 2009-10-15
> **MegaJim said:**
> That just creates a symbolic link with the name of the directory it is passed

In linux, the /home directory is where all of the users files and settings are stored, by name, so if i have two users called james and john on the system, their respective home directories will be at

/home/james
/home/john

you can use a symbolic link to remap these locations, however you should run in maintenance mode or be logged in as another user first so you don't break stuff.

e.g. for me i could create a symbolic link in /home

cd /home
sudo ln -s /mnt/other-drive/home-folder

so now when i list the contents of home with 

ls

i can see

/home/james
/home/john
/home/other-home

now i just have to move everything from /home/james to /home/other-home

shopt -s dotglob
sudo mv james/* other-home/

now i can remove the old home, and rename it so it matches my user name

sudo rmdir james
sudo mv other-home james

now you'll just want to make sure you own your own home directory

sudo chown james james

Any probs just ask.
Quote:  "Any probs just ask."

I've read through the post you made about sudo this and sudo that, and it just doesn't make any sense to me.  I'm sure it's good advice, but you're talking well above my level of sophistication.

---

### Post by MegaJim on 2009-10-15
on the terminal type `man command` to see its manual entry

e.g

```

man mv

```

---

### Post by Don Bowen on 2009-10-17
> **MegaJim said:**
> on the terminal type `man command` to see its manual entry

e.g

```

man mv

```
wow.. another terse entry.  Typing the code you gave returns...

NAME
       mv - move (rename) files

SYNOPSIS
       mv [OPTION]... [-T] SOURCE DEST
       mv [OPTION]... SOURCE... DIRECTORY
       mv [OPTION]... -t DIRECTORY SOURCE...

DESCRIPTION
       Rename SOURCE to DEST, or move SOURCE(s) to DIRECTORY.

       Mandatory  arguments  to  long  options are mandatory for short options
       too.

       --backup[=CONTROL]
              make a backup of each existing destination file

       -b     like --backup but does not accept an argument

       -f, --force
              do not prompt before overwriting

OK... nice... mv is for moving files.  Good.  Do you use it to move a few files? all of them?  to make a backup so that you can restore it later?  
If you're making a backup with MV, then how do you accomplish a restore if both Ubuntu partitions are wiped out?  I'm not quiet sure what you meant to convey with this post...
I'll read it again.

---

### Post by MegaJim on 2009-10-18
The idea of posting the man command is so you can help yourself a bit, my earlier post was describing one strategy to separate user files from the root partition, not for backing anything up.

Perhaps though, you need more direct help.  The ubuntu IRC channel is always full of people willing to talk you through things.

---

### Post by Don Bowen on 2009-10-20
> **Sarmacid said:**
> It's very easy to create an image of your drives, just look up which one is it that you want and try ```
dd if=/dev/sda of=myfile.img
```

Personally I prefer the tar method, because the image of the hard drive will be the same size, and the tar will occupy much less. I've used it and to restore only needed to boot up with a live CD.
how do you do a "restore" with the tar method?  boot off the Live CD?

---

### Post by Don Bowen on 2009-10-20
wow....I've been round and round with imaging Ubuntu.  Here's a brief review:

1. tar - compress all the files that are the partition into one file.  Seems to work, but how do you do a restore after wiping out the ubuntu partition?  boot Live CD?  Tar isn't a destructive backup/restore method, and that 's what I want.  I want to know that the partition is back to the way it was completely.

2. Remastersys - was the best of the methods.  It created a live cd you could re-install that was the image of your installation.  Sadly, it stopped working when Ubuntu went from 9.04 to 9.10.  It gives the appearance of working, but when you boot from the restore CD, you can't do the re-install.

3. CloneZilla - probably a good choice if you can get it to do anything.  The software is marred by it's lack of a user interface.  The most recent one gives me a never-ending keyboard error on my laptop.  I will look in on CloneZilla again...it might turn in to something useful someday.... if they ever finish it.

4. Partimage - again, the step by step I had quit working when going from 9.04 to 9.10. never actually got it to make an image, but it looks promising.

5. RescueCD - it's like live boot with partimage and some other tools.  Way too hard to use.  The step by step instructions for partimage didn't seem to apply for this OS.  More study needed.

6. Norton Ghost - 2003 doesn't think a linux partition is a usable one.  I haven't tried the latest version, though I expect it will work.  I don't like the idea that I have to install Norton 14 before I can image with it. It's only for windows anyway.

What have you used, successfully, to image Ubuntu? 
thanks in advance,
-D.B.

---

### Post by kaibob on 2009-10-20
I've used Acronis True Image for many years but finally had to look elsewhere because even the just-released version of True Image does not support ext4. I decided to first try Clonezilla because it supports ext4 and has been around for some time. I agree with an earlier post that Clonezilla can be more than a little confusing. However, I soon learned to accept most of the default options, changing only source, destination, and image-name options.

I have now successfully made and restored numerous drive images and have placed Clonezilla on a flash boot drive to speed up the process. The more I use the program, the more I have come to like its efficient and reliable, if cluttered, approach to disk imaging. 

One nice aspect of Clonezilla is that it comes as a live CD, which means that you can give it a try with a minimal investment of time. If it doesn't work well, you can move onto another program.

---

### Post by Don Bowen on 2009-10-20
> **kaibob said:**
> I've used Acronis True Image for many years but finally had to look elsewhere because even the just-released version of True Image does not support ext4. I decided to first try Clonezilla because it supports ext4 and has been around for some time. I agree with an earlier post that Clonezilla can be more than a little confusing. However, I soon learned to accept most of the default options, changing only source, destination, and image-name options.

I have now successfully made and restored numerous drive images and have placed Clonezilla on a flash boot drive to speed up the process. The more I use the program, the more I have come to like its efficient and reliable, if cluttered, approach to disk imaging. 

One nice aspect of Clonezilla is that it comes as a live CD, which means that you can give it a try with a minimal investment of time. If it doesn't work well, you can move onto another program.
unless you get that keyboard error I do...that keeps repeating on the screen and scrolls the program choices off the screen.  I really want to like CloneZilla, but for me, it remains unusable.

---

### Post by Don Bowen on 2009-10-20
> **kaibob said:**
> I've used Acronis True Image for many years but finally had to look elsewhere because even the just-released version of True Image does not support ext4. I decided to first try Clonezilla because it supports ext4 and has been around for some time. I agree with an earlier post that Clonezilla can be more than a little confusing. However, I soon learned to accept most of the default options, changing only source, destination, and image-name options.

I have now successfully made and restored numerous drive images and have placed Clonezilla on a flash boot drive to speed up the process. The more I use the program, the more I have come to like its efficient and reliable, if cluttered, approach to disk imaging. 

One nice aspect of Clonezilla is that it comes as a live CD, which means that you can give it a try with a minimal investment of time. If it doesn't work well, you can move onto another program.
Yeah!  CloneZilla finally worked!  I went back and found an older version that doesn't give me that constant "keyboard" error message... and then it was just a walk through the menus t get it working.
It imaged just fine, and it re-imaged (destructively) just fine.
Thank you all for suggesting it.

I notice that the "image" it created was a simple tar file. 
Doesn't that mean that one could duplicate what clonezilla does in the terminal?
TAR compress the entire partition to image, then
boot up on a CD, formate the target partition (to erase it),
then unzip the compressed tar file back to the target?
interesting...will have to try that.

---

### Post by Don Bowen on 2009-10-24
Final word... Norton Ghost 14.0 works every time.  Darn it.  I was really hoping to run an imaging program in Ubuntu to do the job....that would keep me from relying on Windows.  

There simply isn't a good imaging solution for Ubuntu, not yet.

---

### Post by Giradman on 2009-11-03
**Don** -I've been reading this interesting thread in hopes of finding an easy solution to image my Ubuntu installation - rather discouraged from the course of the thread.  I'd like an easy & intuitive program like those available in Windows - :(

I'm also a Windows user and after reading an article in *PC World* on preparing for a Windows 7 installation was made aware of an 'imaging program' (and free download) called [[COLOR="Blue"]Macrium Reflec[/COLOR]t]("http://www.macrium.com/") - just as a test I ran the download on my VISTA laptop and stored to an external hard drive (not tested a restore); but was quite easy to use - SO, why isn't there a similar option for Ubuntu? :(

---

### Post by Hazey on 2009-11-04
Hi guys,

I would prefer a mix of all these listed solutions. Because Linux (in gerneal) releases very fast, a static image is not the best solution. Every time you restore the Image updates will become due. Private Data will not be up to date also.

In my optinion the best solution is a daily tar backup on an external HDD. When a version update releases, you can create an image of the new version.

If you restore the image, you have your private data up to date. Just copy them from the tarball to the home folder.

Hazey

---

### Post by NickJones on 2009-11-04
I sugested something like this to the Ubuntu Brainstorm, you can see my post [http://brainstorm.ubuntu.com/idea/22212/](http://brainstorm.ubuntu.com/idea/22212/)
Please vote, add ideas etc, I think a easy image solution would improve Ubuntu, and give everyone that extra reason to make the move.

---

### Post by yeleek on 2009-11-04
> **LewRockwell said:**
> We make clones with Clonezilla

Even with catastrophic hard drive failure/theft/destruction we can be back up and running with the clone in minutes

.

+1 Clonezilla allows for baremetal restores too.  I image mine off to external usb every so often.

---

### Post by Don Bowen on 2009-12-10
> **Giradman said:**
> **Don** -I've been reading this interesting thread in hopes of finding an easy solution to image my Ubuntu installation - rather discouraged from the course of the thread.  I'd like an easy & intuitive program like those available in Windows - :(

I'm also a Windows user and after reading an article in *PC World* on preparing for a Windows 7 installation was made aware of an 'imaging program' (and free download) called [[COLOR="Blue"]Macrium Reflec[/COLOR]t]("http://www.macrium.com/") - just as a test I ran the download on my VISTA laptop and stored to an external hard drive (not tested a restore); but was quite easy to use - SO, why isn't there a similar option for Ubuntu? :(
the best thing I've found is called "PING" or Partimage Is No Ghost.  Stupid name, but the software works very well.  It's free, and if you download the ISO, you end up with a boot CD that can image and restore your computer.

I should note that Clonezilla uses the same Partimage core engine and is probably a better program... if it works on your computer.  On my laptop, it behaves like one key is stuck and is unusable.
I hope this message reaches you since I haven't been on for a while.
cheers.
-DB

---

### Post by alisonm70 on 2009-12-10
Hi
I'm new to the linux (4 months).
After reading this tread I decided to try Clonezilla. I found this tutorial on you tube

[http://www.youtube.com/watch?v=Zz8iUzV0oMk&feature=related](http://www.youtube.com/watch?v=Zz8iUzV0oMk&feature=related)

and bingo - I found Clonezilla is easy to use - I think is it great - and it cost nothing.

I also watched this you tube first - it is just a general talk about Clonezilla - gives you a little insight into it.

[http://www.youtube.com/watch?v=7WGSMHWV73s&feature=fvw](http://www.youtube.com/watch?v=7WGSMHWV73s&feature=fvw)

My recommendation to other newbie's - give it a try.

---

### Post by RonCam on 2010-02-17
> **Don Bowen said:**
> the best thing I've found is called "PING" or Partimage Is No Ghost.  Stupid name, but the software works very well.But ... when I went to their website, looking for documentation on file system compatibility ... I saw nothing ... but only came across lots of forum messages from users complaining they had to find another utility, as PING won't 'do' Ext4!

Is this out of date, and does it work with Ext4, now?

---

### Post by Don Bowen on 2010-03-02
More thoughts...
 
I use a Dell Inspiron 1501 (AMD x2).
I've tested a few different ways to backup and restore partitions.
I dual boot W7 and Ubuntu depending on mood.
 
I've tried, Norton, PING, and CloneZilla, and after working over time,
I have to admit that CloneZilla is the best so far.  for me, it's been the most
reliable solution...even if the program is UGLY!

---

### Post by LewRockwellFAN on 2010-03-03
> **Don Bowen said:**
> I disagree... CloneZilla isn't ready for prime time yet.  The best tools in the world are useless if you can't get people to use them.  CloneZilla's interface is non-existent, so even though it may be capable of doing great things, it's just too hard to use to be practical.
Might have been true in October, I dunno, I only discovered it around Thanksgiving. It works GREAT. All you have to do is read what it says on the screen. There are clear instructions every step of the way. And not that many steps. No harder than registering for this forum.
Remastersys is fine too. Not as versatile as a cloner but makes live cds just fine.

BTW, I'm not chiming in just to agree with the other poster of similar name. I use this nic at the emacs and sabayon fora as well.

---

### Post by shmk on 2010-03-09
Is it possible with software like Clonezilla or Remasterys do what software like Macrium Reflect or Acronys do?

1. create a image of the system to restore in a one click procedure on different machines

2. create a image "openable" to see what there's inside and retrieve only what you need (maybe a single folder)

---

### Post by faust99 on 2010-03-14
I've used Clonezilla in the past, and while creation of the image went ahead with no problems, restoration of the image failed. My point is not to denigrate Clonezilla, but to ask whether there is a way to test ext4 images created by Clonezilla?

---

### Post by SecretCode on 2010-03-14
I have tested clonezilla images by restoring into a virtual machine. It's time consuming, though.

---

### Post by faust99 on 2010-03-14
> **SecretCode said:**
> I have tested clonezilla images by restoring into a virtual machine. It's time consuming, though.

Thanks for the idea :D

I thought of trying to restore to an external hard disk and booting from that, but I haven't worked out how to do that yet (i.e. booting from an external hd). 

I actually took the plunge and restored the partitions I cloned. Since it was a fresh install I didn't have that much too loose had it failed, but it worked out.

---

### Post by CharlesA on 2010-03-14
> **faust99 said:**
> I've used Clonezilla in the past, and while creation of the image went ahead with no problems, restoration of the image failed. My point is not to denigrate Clonezilla, but to ask whether there is a way to test ext4 images created by Clonezilla?

Only way I know to test them would be to restore them to the machine that you imaged. That's what I do.

> **faust99 said:**
> Thanks for the idea :D

I thought of trying to restore to an external hard disk and booting from that, but I haven't worked out how to do that yet (i.e. booting from an external hd). 

I actually took the plunge and restored the partitions I cloned. Since it was a fresh install I didn't have that much too loose had it failed, but it worked out.

You would probably have to install grub on the external drive so that it would be bootable.

---

### Post by faust99 on 2010-03-14
> **CharlesA said:**
> Only way I know to test them would be to restore them to the machine that you imaged. That's what I do.

Yes, I ended up doing that and it was cool. :cool:



> **CharlesA said:**
>  You would probably have to install grub on the external drive so that it would be bootable.

Of course ](*,)-pretty obvious really. Thanks.):P

---

### Post by BugBuster on 2010-03-14
+1 for CloneZilla..I have used it several times on Windows/NTFS partitions as well as Linux ext3/4 partitions. So far the success rate has been 100%:). Kudos to the CloneZilla team!!

Another tool that I can suggest is PING ([http://www.windowsdream.com](http://www.windowsdream.com)). Its another free tool and is works equally well. Also its ISO is just 20~MB, great for people with slow/limited internet.

I used PING before I came across CloneZilla and gave up PING as it did not have the ability to restore an image of say partition A to partition B like clonezilla. Also clonezilla allows you to work directly  with partitions (copy partition A to partition B without creating an image).

---

