---
title: "Please help fix windows xp through ubuntu"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by lanceA on 2010-11-27
I can boot ubuntu live from a usb drive.  When I try to boot XP in my "normal" mode it gives blank screen and then biosinfo.inf error.  Any suggestions for fixing this through Ubuntu

---

### Post by lanceA on 2010-11-27
I can't boot windows but I can run ubuntu live and see all my files .

Please help

---

### Post by Monotoko on 2010-11-27
Why can you not boot Windows? What is the error?

This should probably be in a Windows support forum rather than here, as they may have more knowledge on the subject.

Daniel

---

### Post by tad1073 on 2010-11-27
what error messages do you get when you try to boot xp?
did you have ubuntu previously installed?

---

### Post by lanceA on 2010-11-27
> **Monotoko said:**
> Why can you not boot Windows? What is the error?

This should probably be in a Windows support forum rather than here, as they may have more knowledge on the subject.

Daniel
I get the Dell splash screen then black screen then cannot find biosinfo.inf

---

### Post by lanceA on 2010-11-27
I get dell splash screen then black screen then cannot find biosinfo.inf

---

### Post by Monotoko on 2010-11-27
Something like the following?
```
Windows could not start because the following file is missing or corrupt C:\Windows\inf\Biosinfo.inf
```

If so Microsoft has a support page based around the issue: [http://support.microsoft.com/kb/829784](http://support.microsoft.com/kb/829784)

---

### Post by lanceA on 2010-11-27
> **Monotoko said:**
> Something like the following?
```
Windows could not start because the following file is missing or corrupt C:\Windows\inf\Biosinfo.inf
```

If so Microsoft has a support page based around the issue: [http://support.microsoft.com/kb/829784](http://support.microsoft.com/kb/829784)
Thanks I have found that link but I need to be able to do F8 for that and I can't.

This is what I can do.  Go into ubuntu, do these commands :
sudo apt-get install mbr
sudo install-mbr -i n -p D -t 0 /dev/sda

(i have no clue as to what this says.  But after that I can reboot into windows with no problem - except if i restart i'm back at the missing biosinfo.inf message

---

### Post by Monotoko on 2010-11-27
I personally haven't used install-mbr before, but it seems like one of two things are happening here. The mbr fix is temporary, or Windows is doing something when you boot into it.

You could check the manual for the install-mbr command to see what exactly it does with those switches. 

On the other hand, if Windows is doing something when you have rewrote the mbr, you may need to go to a Windows forum or chat room (irc.freenode.net channel: ##windows is quite a busy room)

---

### Post by lanceA on 2010-11-27
Sorry to sound so lame, but how do i get to that chatroom

---

### Post by Monotoko on 2010-11-27
No worries, the only dumb questions are the ones not asked! To get to an IRC chat room you can download xchat from the Ubuntu repositries and type "/server irc.freenode.net" then "/join ##windows"

Or you can use the web-based client: [http://webchat.freenode.net/](http://webchat.freenode.net/)

---

### Post by lanceA on 2010-11-27
many thanks

---

### Post by Hakunka-Matata on 2010-11-27
> **lanceA said:**
> Thanks I have found that link but I need to be able to do F8 for that and I can't.

This is what I can do.  Go into ubuntu, do these commands :
sudo apt-get install mbr
sudo install-mbr -i n -p D -t 0 /dev/sda

(i have no clue as to what this says.  But after that I can reboot into windows with no problem - except if i restart i'm back at the missing biosinfo.inf message

This [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/") URL describes how to fix your mbr while running an instance of Ubuntu Live CD.

---

### Post by Hakunka-Matata on 2010-11-27
fixmbr is likely not what you need to do to resolve your problem however.  

Monotoko said it best, [http://support.microsoft.com/kb/829784]("http://support.microsoft.com/kb/829784")

---

