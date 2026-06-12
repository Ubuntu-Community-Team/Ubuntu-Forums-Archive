---
title: "Accidentally Deleted All Files!!!"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by Skitsnygg on 2010-06-08
Hi,

I'm hoping someone will be able to help me here as I seem to have made a slight error!

First of all, I should say that I'm new to the forum and would greatly appreciate any help. I've also had a quick search before writing this but could not find and exact matches to my problem; if that is not the case, please point me in the right direction and accept my apologies :)

So here goes....

I would say I'm a complete beginner when it comes to computers but about a year ago, I built my own PC. Everything went fine until it came to the bios so I had it professionally set up here, with an evaluation version of Windows 7 installed.

This was due to expire a few days ago so, grudging paying for an OS, decided to take the plunge and go for Ubuntu.

This seemed to go OK as well, and after a while I was relatively comfortable with the basics and trasferred over a significant amount of music, videos, and documents. I then began to install software.

I installed iTunes, not realising the problems with this. Once I became aware of these I noticed it was quite tricky to uninstall and so sought help online. I entered the terminal command described, which did not seem to work, which was when I entered 'sudo' alone.

This seems to have completely wiped the media and documents that I had transferred (and stupidly not kept the backup!) and I can't seem to figure out how to reverse this.

I am really hoping that someone here can help me! As I said, I am not the most competent in this field and I'm kinna praying there's a simple way to do this.

After I did this I've barely touched the PC so shouldn't have written over anything.

Again, thanks in advance for any help.

Craig :)

---

### Post by jerome1232 on 2010-06-08
What was the command you ran? You never mentioned it in your post other than saying you ran sudo alone.

---

### Post by pizza-is-good on 2010-06-08
How did you install iTunes. Was it via the file that you downloaded from the iTunes site? do you know if you used wine?

Yes, the best thing would be to not touch your computer at all. That will give you better chances of having more files recovered.

I think that [parted magic]("http://partedmagic.com/") has some data recovery tools. You might want to look into it. Whatever the case, I wouldn't do anything until you double check the procedure with someone here.

---

### Post by Skitsnygg on 2010-06-08
I'm sure I followed these intructions:

[I]" What you can do to completely remove them (along with everything else  installed in wine) is:
-Open a terminal
-type:
rm -rf ~/.wine
(this command remove the wine c drive)

-then type:
wineprefixcreate

(This regenerates a wine c drive)


To remove the start menu entries, run:
sudo updatedb
(updates database)

locate 'nameofentry'

sudo rm /path/to/entry[/I] "

And then when this didn't work I got a bit annoyed and tried one or two variations (don't ask why!). Not sure why, but just got a feeling deleting everything had something to do with typing sudo and then hitting return.

---

### Post by Skitsnygg on 2010-06-08
Pizza: Ye it was using wine. 

Cheers for that link, just having a look now. Feel a bit out my depth tho! :???:

---

### Post by Backharlow on 2010-06-08
I was told but a data recovery guy, "If you erase something you shouldn't have, immediately reach other pull the plug from the wall."
So, shut down the computer now. The more time it stays up the more chance that your no longer tracked data will get overwritten.

---

### Post by jerome1232 on 2010-06-08
Depends on what variations you tried, I'm trying to figure out what exactly did you delete.

What is the output of the history command? (maybe it will have the exact commands you ran)

```
history
```

edit: You can look at testdisk / photorec, very good file recovery programs imo.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Skitsnygg on 2010-06-08
When I type history this is what I get:

1 rm -rf ~/ wine.
2 rm -rf ~/.wine
3 wineprefixcreate
4 sude updatedb
5 sudo
6 sudo add-apt-repository ppa:kubuntu-ppa/backports
7 history

:confused:

---

### Post by pizza-is-good on 2010-06-08
> **Skitsnygg said:**
> I'm sure I followed these intructions:

[I]" What you can do to completely remove them (along with everything else  installed in wine) is:
-Open a terminal
-type:
rm -rf ~/.wine
(this command remove the wine c drive)

-then type:
wineprefixcreate

(This regenerates a wine c drive)


To remove the start menu entries, run:
sudo updatedb
(updates database)

locate 'nameofentry'

sudo rm /path/to/entry[/I] "

And then when this didn't work I got a bit annoyed and tried one or two variations (don't ask why!). Not sure why, but just got a feeling deleting everything had something to do with typing sudo and then hitting return.

OK, I think this might be bad.

rm -rf ~/.wine would remove wine. OK. What you should have done is ```
sudo apt-get remove wine
```now, if when you were trying around, you accidentally did
```
rm -rf ~/ .wine
```with the space, then you removed your entire home directory and wine.....

rm -rf is something that is very dangerous and should be used with care. It could be used as a malicious command. Read this [Forum Announcement]("http://ubuntuforums.org/announcement.php?f=326")

I suspect those instructions, because the last step had rm, which removes files, and that is something you don't do to get a program running.

Now, definitely don't touch that computer, and lets wait for someone that has data recovery experience to help us out.

---

### Post by sandyd on 2010-06-08
> **Skitsnygg said:**
> When I type history this is what I get:

1 **rm -rf ~/ wine.**
2 rm -rf ~/.wine
3 wineprefixcreate
4 sude updatedb
5 sudo
6 sudo add-apt-repository ppa:kubuntu-ppa/backports
7 history

:confused:
Ive bolded your mistake.

you did a space between the wine and the slash. This has erased your whole home folder and all your files as a result.

-------------------
wrong thread

---

### Post by pizza-is-good on 2010-06-08
> **Skitsnygg said:**
> When I type history this is what I get:

1 [COLOR=Red]**rm -rf ~/ wine.**[/COLOR]
2 rm -rf ~/.wine
3 wineprefixcreate
4 sude updatedb
5 sudo
6 sudo add-apt-repository ppa:kubuntu-ppa/backports
7 history

:confused:


OK, that confirms my previous post. you did rm -rf ~/ [space] wine
BAD BAD

Please stop using the computer now. You will loose more data. Get a live CD and boot from that and get back here from there, but don't touch anything else....

EDIT: Correction, you wouldn't need to sudo to delete your own files, only the system files, so the terminal was OK with your authority to do that.

---

### Post by jerome1232 on 2010-06-08
> **Skitsnygg said:**
> When I type history this is what I get:
[COLOR="Red"]
1 rm -rf ~/ wine.[/COLOR]
2 rm -rf ~/.wine
3 wineprefixcreate
4 sude updatedb
5 sudo
6 sudo add-apt-repository ppa:kubuntu-ppa/backports
7 history

:confused:

That one highlighted in red, removed all files in your home directory, recursively. (meaning it nuked your /home/<username> and everything under it)

Unfortunatly the only way to get those files back is to use a utility such as photorec

[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

You need an extra disc or partition to recover the files to (obviously if you are writing to the drive you are recovering from you can be overwriting deleted data as you are recovering it) You can run it from a live cd (that's what I would do, to prevent system log files and etc from possibly overwriting your deleted data)

---

### Post by Skitsnygg on 2010-06-08
Ouch!

Cheers for your help folks. Is generally something that can be fixed on ubuntu?

To be honest, this isn't 'end of the world' stuff for me. A lot of films/TV programs and if I could do with saving the doc's!

If had been my main music collection tho......

---

### Post by pizza-is-good on 2010-06-08
> **Skitsnygg said:**
> Ouch!

Cheers for your help folks. Is generally something that can be fixed on ubuntu?

To be honest, this isn't 'end of the world' stuff for me. A lot of films/TV programs and if I could do with saving the doc's!

If had been my main music collection tho......

> **carlee said:**
> Ive bolded your mistake.

you did a space between the wine and the slash. This has erased your whole home folder and all your files as a result.

a good thing to do right now is to shut down IMMEDIATELY, and boot up from a livecd.
then run
```

sudo apt-get install testdisk
sudo testdisk
```gl...

If you shutdown now, and do as carlee said, you'll get a significant amount of it back.

---

### Post by Skitsnygg on 2010-06-08
Best bet to follow these ubuntucat instuctions word for word?

---

### Post by jerome1232 on 2010-06-08
No, you need to adjust them for your situation. You will be selecting different partitions than selected in that tutorial.

You can also make photorec only search for specific file types (text files, music, video, documents etc..)

Just make sure you are recovering the files to a different partition or disk than where you home folder was, you can always start the program up and post back with a screen shot and questions on how to go on before you commit to it doing the recovery.

---

### Post by Skitsnygg on 2010-06-08
Cool, sounds like a plan.

And, probably a daft question here but I'm assuming the boot CD is exactly the same as the one I used for the initial install?

---

### Post by KdotJ on 2010-06-08
Ouch, that it one painful command

Worth a read, for future reference, the following link is to a thread here on this forum outlining dangerous commands

[CLICK HERE]("http://ubuntuforums.org/announcement.php?f=326")

you will see that the command you used (rm -fr ...) is one of the very first ones stated.

Good luck with the recovery!!!

---

### Post by KdotJ on 2010-06-08
> **Skitsnygg said:**
> Cool, sounds like a plan.

And, probably a daft question here but I'm assuming the boot CD is exactly the same as the one I used for the initial install?

Yes indeed, just choose the "Try Ubuntu" option when offered

---

### Post by jerome1232 on 2010-06-08
> **carlee said:**
> Ive bolded your mistake.

you did a space between the wine and the slash. This has erased your whole home folder and all your files as a result.

a good thing to do right now is to shut down IMMEDIATELY, and boot up from a livecd.
then run
```

sudo apt-get install testdisk
sudo testdisk
```

gl...

Correct me if I'm wrong here carlee but I thought testdisk just recovered partition table data and mbr data. Photorec (which comes with testdisk) can recover deleted data. We don't have any partition table trouble here just deleted files. So I'm not understanding why you are recomending testdisk.

@Skitsnygg, yes the live cd should be the one you used to install with, you will want to select "Try Ubuntu" from the boot menu which will get you into a live cd environment. Live cd's are nifty things, always good to keep a few laying around.

---

### Post by Skitsnygg on 2010-06-08
Haha, cheers KdotJ.

First time I've ever opened the terminal n managed to fire that one in!

---

### Post by irv on 2010-06-08
Just by chance did you look in the trash to see if the files were in there?
I don't think there are, but it is worth a look.

---

### Post by pizza-is-good on 2010-06-08
> **irv said:**
> Just by chance did you look in the trash to see if the files were in there?
I don't think there are, but it is worth a look.

As far as I know, nothing that you delete in the terminal will get put in the trash.

---

### Post by jerome1232 on 2010-06-08
> **pizza-is-good said:**
> As far as I know, nothing that you delete in the terminal will get put in the trash.

Not when using rm, it actually deletes stuff. There are ways though, if I recall correctly you can install trash, and use it in place of rm, it will move files to trash instead of deleting them.

---

### Post by irv on 2010-06-08
> **jerome1232 said:**
> Not when using rm, it actually deletes stuff. There are ways though, if I recall correctly you can install trash, and use it in place of rm, it will move files to trash instead of deleting them.

Thanks, this is good to know. In fact Ubuntu should use as default and recommend using it.

---

### Post by pizza-is-good on 2010-06-08
> **jerome1232 said:**
> Not when using rm, it actually deletes stuff. There are ways though, if I recall correctly you can install trash, and use it in place of rm, it will move files to trash instead of deleting them.

Well, yes, I meant to using rm. It didn't occur to me that something else would be used to delete things, even if I use shred all the time for clearing old HDDs. :lolflag:
I hadn't heard of trash.

---

### Post by Skitsnygg on 2010-06-09
Here goes...

Wish me luck folks, n cheers for the advice again.

Will post screenshots if I get stuck!

---

### Post by Skitsnygg on 2010-06-09
So..........first question!

What version of PhotoRec am I downloading?

***EDIT***

Scrap that, just noticed the download links underneath :)

---

### Post by jerome1232 on 2010-06-09
It's in the repositories, just install testdisk it comes with photorec

```
sudo apt-get install testdisk
```

---

### Post by crispy_420 on 2010-06-09
[ext3grep]("http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html")

Does not look that simple but how much is your data worth? Also I would maybe consider running from the LiveCD if possible and writing data to a different drive. The more you use the drive, the more that may be lost. 

Also look into file carving on google based on your file system type (eg. ext3/4).

---

### Post by KdotJ on 2010-06-09
> **Skitsnygg said:**
> Here goes...

Wish me luck folks, n cheers for the advice again.

Will post screenshots if I get stuck!

Good luck!
Keep us updated and if you succeed, as I'm certain other people will be in the same situation in the future

---

### Post by Skitsnygg on 2010-06-09
> **KdotJ said:**
> Good luck!
Keep us updated and if you succeed, as I'm certain other people will be in the same situation in the future

Afraid I'm just going to put mark down as a 'learning curve'!

I actually managed to find the documents I deleted (on my laptop) and so all I've really lost is about 60GB of films and TV programs.

Had a look through how to fix this and really appreciate the help from all of you, but think I'm just a bit of out of my depth.

Definately learned a lesson tho! :razz:

Now I just need to remember what videos I lost......

---

### Post by Skitsnygg on 2010-06-09
.

---

### Post by QIII on 2010-06-09
Glad you got most of it back!

One thing to take from this, aside from the dangers of rm, is to do frequent backups.

I know.  Everyone says it.  We all know it.  Sort of like flossing our teeth.  We know we should, but do we really?

We all screw up sometimes.  Even those of us who have been at it a while.

---

