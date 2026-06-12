---
title: "COMPLETE newb here"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by mr. bigsby on 2009-10-22
Before I dig into the stickies and archives and everything, I would like to ask a very basic question- is Ubuntu what I need?
 
I have a 7 year old PC which recently collapsed under it's own weight, I'm afraid. I pulled the data files off the hard drive, and formatted it. But sadly, the XP disc has been lost in the sands of time...
 
What I'd like to do is install a [free] OS, and convert the computer into a recording platform... as I dabble in musical endeavors. 
 
Is Ubuntu what I need?
 
Thanks!

---

### Post by sgosnell on 2009-10-22
Maybe UbuntuStudio.

---

### Post by mr. bigsby on 2009-10-22
> **sgosnell said:**
> Maybe UbuntuStudio.
 
Is that an operating system. or just the recording software?

---

### Post by jrrader on 2009-10-22
[http://ubuntustudio.org/](http://ubuntustudio.org/)

It's Ubuntu's OS specialized for the arts.

---

### Post by skompier on 2009-10-22
> **mr. bigsby said:**
> Is that an operating system. or just the recording software?

UbuntuStudio is Ubuntu with specific software pre-installed that caters to media production.

---

### Post by dwasifar on 2009-10-22
> **mr. bigsby said:**
> Is that an operating system. or just the recording software?
It's a version of the OS optimized for multimedia creation and editing.

[Here's the homepage.]("http://ubuntustudio.org/")

---

### Post by dwasifar on 2009-10-22
Now a longer answer.

First, welcome!  As you can already tell by how many people responded to your question, we're glad you're considering Ubuntu.

You may want to look at [this thread]("http://ubuntuforums.org/showthread.php?t=801404") for some beginner information.

Probably the most important thing you need to keep in mind, if you're coming in cold from Windows, is: *Linux is not Windows.*  That's not meant to scare you off; on the contrary.  We want you to become a happy Linux user.  But it usually needs to be stressed at the outset, because lots of times people don't realize how accustomed to Windows they are until they try something else.  There will be a learning curve; there will be Windows stuff you'll have to unlearn.  It'll probably take some time and patience.  But it's worth the effort.  Once you get used to the differences, you'll start to appreciate the technical advantages of Linux.

Anyway.  Don't want to go off on a long sermon about it.  Just check out the beginner guides, and allow yourself time to get acclimated to avoid frustration, and you'll do fine.  You've already figured out how to look for answers, so you're already on the right road.

Again, welcome.  :)  And good luck to you.

---

### Post by mr. bigsby on 2009-10-23
> **dwasifar said:**
> Again, welcome. :) And good luck to you.
 
Thanks. I think I'll give it a shot.
 
:guitar:

---

### Post by dwasifar on 2009-10-23
Let us know how it goes.

BTW: Would "Mr. Bigsby" be a friend of Mr. Kahler and Mr. Floyd Rose?

---

### Post by Merk42 on 2009-10-23
7 Years old?
What are the specs of the machine?

---

### Post by ikt on 2009-10-23
> **mr. bigsby said:**
> Thanks. I think I'll give it a shot.
 
:guitar:

If you have any troubles we're still here ^_^ and after you get it all up and running lets all have a newb party later on :)

---

### Post by mr. bigsby on 2009-10-25
> **dwasifar said:**
> Let us know how it goes.
 
BTW: Would "Mr. Bigsby" be a friend of Mr. Kahler and Mr. Floyd Rose?
 
Could very well be...
 
:)
 
Hey, so I downloaded Ubuntu, fired up the computer, and started the install process. I got hung up on Step 4- it says "No root file is defined, correct using partition menu". But the partition menu wasn't active.
 
Any ideas?
 
Oh yeah, keep in mind- I'm not only a newb, I'm also not a techie. So please be gentle...

---

### Post by sgosnell on 2009-10-25
You have to tell Ubuntu where to put /, the root directory, if you're selecting manual partitioning.  I have no way of knowing how you've set up the install/partitioning.

---

### Post by mr. bigsby on 2009-10-25
> **sgosnell said:**
> You have to tell Ubuntu where to put /, the root directory, if you're selecting manual partitioning. I have no way of knowing how you've set up the install/partitioning.
 
Oh hell man, I just put the disc in and started following directions. I didn't set up much of anything...

---

### Post by sgosnell on 2009-10-25
You had to make choices along the line.  The screen before that gave you at least 3, IIRC.

---

### Post by mr. bigsby on 2009-10-25
> **sgosnell said:**
> You had to make choices along the line. The screen before that gave you at least 3, IIRC.
 
Not sure about that... I'll go try it again, see what the options are.

---

### Post by mr. bigsby on 2009-10-25
Okay, here's how it goes:
 
Screen 1- Select language
 
Screen 2- Select time zone
 
Screen 3- Select keyboard layout
 
Then, when I hit the "next" button, a dialog box opens (for about 2 seconds), says "Starting Partitioner", and a progress bay zips across...
 
Screen 4- Pretty much blank, there are some buttons on the bottom that refer to partitioning, but they're not active. When I push the "next" button, I get the error message.
 
:confused:

---

### Post by Major Squirrel on 2009-10-25
Hey!

I had the same problem as you and I figured it out!

What you have to do is if you're manually selecting your partitions, that is the last choice on the partition selection menu: option 1 is install side by side, option 2 is use entire disk and option 3 is specify partitions manually, pretty much if you want to dual boot with windows, pick option 1 and then move the slider on the colored bar until it has allocated as much space for ubuntu as you want. Option 2 is if you want to go cold turkey and completely ditch windows and have a ubuntu only machine, and the last one seems like the one you are using wher you can make a partition for ubuntu and what not. If you decide to do that you have to format a partition to either ext3 or ext4 and thenin the drop down menu that discusses booting or something you have to select the / option. You should be good to go after that!

---

### Post by mr. bigsby on 2009-10-25
It's almost sounding like I'm doing the wrong thing by running "install"... is there a setup function that I need to run first?

---

### Post by Major Squirrel on 2009-10-25
Well do you mean once you've put in the live cd? installing is definitely what you need to choose, how are you planning on installing ubuntu? Do you want to create a manual partition, or completely use the disk?

---

### Post by Vaphell on 2009-10-25
lol, no :-) this is the setup
there are few steps about language, keyboard and stuff. One of them is to assign disk space for ubuntu installation. You need to pick one of 3 options (side by side, whole hdd, manual tweaking). You said you don't have XP disk anymore so go with full hdd install if you don't feel like manually creating partitions. Mark it and click next.

---

### Post by mr. bigsby on 2009-10-25
I don't know what I was doing wrong, but this time it worked...  so at least I have that going for me.
 
I had to format the hard drive, so I'm going all in with Ubuntu. I'll let you know how it works out!
 
:cool:

---

### Post by Major Squirrel on 2009-10-25
That's the spirit!!! Enjoy it!

---

### Post by sgosnell on 2009-10-25
You'll learn more from making mistakes and recovering from them than you ever will by getting it right the first time.  That's the way life is.

---

