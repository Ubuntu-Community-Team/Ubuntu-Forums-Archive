---
title: "Home folder wiped. Help!"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by zosolm on 2010-09-27
I started to run out of space on my hard drive and then my ubuntu started to play up. The log in screen would appear but when I logged I, it would look as if it were loading, but then bring up the log in screen again. I figured I need to free up some space, so I pressed control, alt +F2 to get a terminal and was able to log in there. I then did ```
sudo apt-get clean
```, restarted and my home folder (all of my music, pictures, documents) was empty. How do I get it back?? :(
Thanks

---

### Post by q1_dab on 2010-09-27
> **zosolm said:**
> I started to run out of space on my hard drive and then my ubuntu started to play up. The log in screen would appear but when I logged I, it would look as if it were loading, but then bring up the log in screen again. I figured I need to free up some space, so I pressed control, alt +F2 to get a terminal and was able to log in there. I then did ```
sudo apt-get clean
```, restarted and my home folder (all of my music, pictures, documents) was empty. How do I get it back?? :(
Thanks

Do you mean you ran 'sudo apt-get **install** clean' ?

As far as I am aware apt-get needs an instruction, such as 'install'. If you mean you ran the 'clean' application and it deleted your ~/ then I would suggest reading the manpage first, then looking into some file-recovery programs to possibly retrieve your files. 

(Let this be a reminder, always RTFM to stop silly things like this happening.)

---

### Post by zosolm on 2010-09-29
are there an you can recommend? simple to use, preferably as i'm not too experienced

---

### Post by chaanakya_chiraag on 2010-09-29
> **q1_dab said:**
> Do you mean you ran 'sudo apt-get **install** clean' ?

As far as I am aware apt-get needs an instruction, such as 'install'. If you mean you ran the 'clean' application and it deleted your ~/ then I would suggest reading the manpage first, then looking into some file-recovery programs to possibly retrieve your files. 

(Let this be a reminder, always RTFM to stop silly things like this happening.)
No no no...  ```
sudo apt-get clean
``` removes all the packages downloaded by apt during program installation...this shouldn't have affected the files in the home directory at all...

---

### Post by theozzlives on 2010-09-29
> **chaanakya_chiraag said:**
> No no no...  ```
sudo apt-get clean
``` removes all the packages downloaded by apt during program installation...this shouldn't have affected the files in the home directory at all...

Correct! That command wouldn't hurt /home. I use it all the time. You had to have use some other command in addition to. Drop to the terminal and report what exactly whats in /home NOT /home/<username>.

To Q1_dab, clean is an instruction for apt.

---

### Post by coffeecat on 2010-09-29
> **q1_dab said:**
> Do you mean you ran 'sudo apt-get **install** clean' ?

As far as I am aware apt-get needs an instruction, such as 'install'.

No the OP means they ran 'sudo apt-get clean' which is perfectly good syntax. 'sudo apt-get install clean' would merely result in the error message: "E: Unable to locate package clean".

---

### Post by coffeecat on 2010-09-29
@zosolm, we seem to have been sidetracked by apt-get syntax.

As someone else has said, apt-get clean will not empty your home folder, but the fact that you ran out of space and Ubuntu started to 'play up' means that possibly there has been filesystem corruption. Your possible options for what to do now need a bit of experience. First - do you have any backups of your personal files?

Next - if there is filesystem corruption or your home has somehow been wiped accidentally and you do not have backups of you personal files, do not boot into the system. That will merely cause overwrites of deleted files and will make them completely impossible to rescue.

There are two courses of action.

With the possibility of a filesystem corruption, you could boot into a live CD and run fsck. Do you need help?

If you need to recover deleted files you need photorec from the testdisk package which you would run from the live CD. This is not for the fainthearted and difficult if you are inexperienced.

---

### Post by theozzlives on 2010-09-29
> **theozzlives said:**
> You had to have use some other command in addition to.

I can't post the command I think you ran, but if your stuff & settings are gone you shouldn't be using your computer. If you have been, your stuff is probably gone... Time to restore from backups. If you don't have any, I feel for you.

---

### Post by Old *ix Geek on 2010-09-29
> **zosolm said:**
> I started to run out of space on my hard driveReally? How do you know? What did you do to check your remaining disk space?
> and then my ubuntu started to play upMay be entirely unrelated to running out of space, if that's what occurred.
> I then did
```
sudo apt-get clean
```, restarted and my home folder (all of my music, pictures, documents) was empty. How do I get it back?? :(Again, really? What have you done to look into your home folder? As others have said, the command you ran--by itself--could not have deleted your home folder and/or its contents. Either you ran something else, too, or your files really aren't missing.

From a command line type:
```
cd /home
ls -l

```
Is your directory there? If so, what are its permissions?

---

