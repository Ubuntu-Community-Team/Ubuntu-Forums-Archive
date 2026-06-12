---
title: "Antivirus for Linux?"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by Call My Function on 2010-03-10
I already asked a friend this, but I'd like a second opinion.

He's a regular computer geek, and he claims that I don't need antivirus programs for Linux, since most viruses are designed to infect Windows. Is this true? Can I surf the net and whatnot without fear of infection?

If not, could you recommend a free, decent antivirus program for Ubuntu (Karmic)?

---

### Post by Brandel Valico on 2010-03-10
For the most part it is true. Been using Linux for years and I have been to sites I know infect Windows PC's simply by going there. Without fear of my computer being infected. 

Now that doesn't mean you can't catch anything. If you are allowing things to install and granting Admin privilege to packets or running commands from non-trusted sites you may run into issues. But the odds of such are far far lower then on Windows. So my answer would be that roughly 97% percent of the time you never need Anti-Virus on Linux. But if your sharing files with others on Windows it's not a bad idea to have one simply to ensure any files your sharing aren't infected when you give them to the Windows user. If you open up Software Center and do a search for Clam. You will find a Virus scanner easily available for install. (Unlike Windows you simply download it from the Center and it installs and sets up for you. No need to do web searches and download from non-trusted sources. You also have a vast amount of other programs in the same center)

---

### Post by Arand on 2010-03-10
I commented something similar not too long ago: [http://ubuntuforums.org/showpost.php?p=8875017&postcount=13](http://ubuntuforums.org/showpost.php?p=8875017&postcount=13)
(might want to read the thread as well, since it's relevant: [http://ubuntuforums.org/showthread.php?p=8875017](http://ubuntuforums.org/showthread.php?p=8875017) )

 - Arand

---

### Post by ubudog on 2010-03-10
He is right.  You don't need to worry about viruses/spyware in Ubuntu.  The only way to install a virus in Ubuntu is if you actually want one.  But if you don't, then you are ok. ;)

---

### Post by zeroseven0183 on 2010-03-10
I agree that for the most part you don't need an antivirus but if you're sharing files with Windows users, chances are that the files transferred could be malware/virus. I recommend the simple virus scanner mentioned above, ClamTk, it's the GUI of ClamAV. Download it and make sure you update it often. I also recommend BitDefender for Linux. I have both of these on my machine, sitting here waiting to kill a Windows virus.

If you need more information about virus/virus scanners in Linux, read Tuxradar's review at [http://www.tuxradar.com/content/get-best-virus-scanner-linux](http://www.tuxradar.com/content/get-best-virus-scanner-linux)

And if you happen to choose to install BitDefender, the instructions are here: [http://ubuntuforums.org/showpost.php?p=8888554&postcount=12](http://ubuntuforums.org/showpost.php?p=8888554&postcount=12)

Hope that helps

---

### Post by Dude-PWB- on 2010-03-10
For the most part, no need to worry about virus or spyware in linux. However, as mentioned above, if you are using e-mail and sharing files with windows users, it might not be a bad idea to have something around to scan anything suspicious. Not so much for your protection, but for theirs. Someone sends you a virus, that doesn't affect you, but you could pass it on to someone else that it will.

ClamTK is a simple av client and will do everything you need with a nice little GUI.

Klamav has a little more flash to the gui, and a few more options, but they use the same virus database from what I understand.

Both are in the repositories.

---

### Post by zeroseven0183 on 2010-03-10
> **ubudog said:**
> He is right.  You don't need to worry about viruses/spyware in Ubuntu.  The only way to install a virus in Ubuntu is if you actually want one.  But if you don't, then you are ok. ;)

Very true. It's one thing I'm no longer *very* concerned about since switching to Linux/Ubuntu. I don't use virus scanners for my machine's protection, I use it for my friend's security.

I feel a lot safer now.

---

### Post by ubudog on 2010-03-10
> **zeroseven0183 said:**
> Very true. It's one thing I'm no longer *very* concerned about since switching to Linux/Ubuntu. I don't use virus scanners for my machine's protection, I use it for my friend's security.

I feel a lot safer now.

Me too.  In Windows, I used to get all paranoid when it started getting slow (which happened all the time).  Now, with Ubuntu, I am no longer paranoid, except for the encrypted hard drive, etc.

---

### Post by Call My Function on 2010-03-10
Thanks guys. :) I haven't had any trouble so far (as far as I can tell), and although I'm not intimately familiar with Ubuntu, I'm selective about what I install and I always try to understand what commands or programs are meant to do before I run them. I'll take a look at those antivirus programs and whatnot.

---

### Post by ubudog on 2010-03-10
Well, hope you enjoy Ubuntu.  :p

---

### Post by undecim on 2010-03-10
Just make sure that you know what commands and programs do before you install them.

Not long ago, there was a .deb package (analogous to a setup file in Windows) the Gnome/Ubuntu customization site gnome-look.org, which the author claimed was a screen saver. In reality it was a virus.

If you just go installing things from random people, you are going to get viruses no matter what OS you have.

However, a lot of the worms (what most people think of as a virus) that affect Windows exploit flaws in Windows that Ubuntu is designed to prevent.

In other words, the only way to get a virus in Linux is to install it directly.

---

### Post by diablo75 on 2010-03-10
ClamAV is available in the Applications>Software Center I believe...  But your friend is right.  You don't need AntiVirus for Linux.  Others in here will do a better job at explaining why this is, but in short, the OS has a big advantage here due to it being open source.  The operating system is a product of crowd-sourcing, much in the same way as Wikipedia has been since it first showed up several years ago.  And much like the highly-moderated articles of Wikipedia that require membership and has an approval process for changes made to locked articles, so to is a strict moderation that goes on with the source code for Linux before it's allowed to become part of the official distribution.  Everybody is out to identify possible flaws or weaknesses or bugs in the source code and it's much easier for any single person to make a contribution because the OS and much of the software that runs on it is open-source.

In Windows, the users don't have the luxury of being able to dig through the source code to look for flaws.  All they can do is report symptoms of problems to Microsoft, and the limited number of paid programmers that do have access to the source code then have to decide what flaws are the most important and which ones don't merit their attention.  So with Windows, a bug that affects only 500 people won't be as important as a bug that affects 500,000 and probably won't be fixed at all.  But if it were Linux and if just one or two of those 500 people were a programmer who had access to the source code and figured out how to fix the problem on their own, the other 498 would actually stand to benefit from a patch that ends up being released thanks to the work of that one developer who had some spare time on his hands and decided to do something about a bug simply because he could.

So throughout the long life of Linux there has been this much more diversified, seasoned, multi-cultured source for development feedback that has helped to make it a much stronger, more "mature" operating system, especially in terms of the way security was designed.  If there was ever a person out there who found a way to circumvent that security, there is at least another who knows exactly how to repair the flaw.  The reason viruses are able to best Windows is because their developers can only patch so many holes, and the ones they don't have time to get around to end up being exploited the most.  Third-party software developers that make Anti-Virus software make a killing because Microsoft is unable to handle this responsibility all by themselves, and even still, the best anti-virus software isn't perfect.

The reason anti-virus software isn't necessary in Linux is simply because the OS and its updates that patch  vulnerabilities do the exact job anti-virus software in Windows is meant for:  Prevent unwanted, malicious software or network activity from compromising the system.  If there were a flaw in Linux found that allowed something like that, it wouldn't be the job of some third-party software to safeguard the user against but the job of the OS itself.  The reason anti-virus software even exists is simply because Microsoft is unable to handle the immense work load of patching their own source code as well as a crowd of Linux geeks can.

Am I saying Linux is perfect and invincible to viruses?  Might it become more susceptible to viruses in the future if it were to ever become as popular as Windows is today?  I would think that with an increase in the number of users would also come a complimentary increase in the number of clever developers that would only help to increase the number of eyes available to find flaws and fix them.  Saying that Linux would get a lot of viruses down the road because more people are going to use it is like saying Wikipedia will become rife with widespread, uncontrollable vandalism because more people visit it.  It hasn't happened yet, and very likely never will happen because of the way it is designed, moderated and improved upon by the hive mind.

Sorry... I got carried away and made this post kinda long.  :p

---

### Post by ubudog on 2010-03-10
> **diablo75 said:**
> ClamAV is available in the Applications>Software Center I believe...  But your friend is right.  You don't need AntiVirus for Linux.  Others in here will do a better job at explaining why this is, but in short, the OS has a big advantage here due to it being open source.  The operating system is a product of crowd-sourcing, much in the same way as Wikipedia has been since it first showed up several years ago.  And much like the highly-moderated articles of Wikipedia that require membership and has an approval process for changes made to locked articles, so to is a strict moderation that goes on with the source code for Linux before it's allowed to become part of the official distribution.  Everybody is out to identify possible flaws or weaknesses or bugs in the source code and it's much easier for any single person to make a contribution because the OS and much of the software that runs on it is open-source.

In Windows, the users don't have the luxury of being able to dig through the source code to look for flaws.  All they can do is report symptoms of problems to Microsoft, and the limited number of paid programmers that do have access to the source code then have to decide what flaws are the most important and which ones don't merit their attention.  So with Windows, a bug that affects only 500 people won't be as important as a bug that affects 500,000 and probably won't be fixed at all.  But if it were Linux and if just one or two of those 500 people were a programmer who had access to the source code and figured out how to fix the problem on their own, the other 498 would actually stand to benefit from a patch that ends up being released thanks to the work of that one developer who had some spare time on his hands and decided to do something about a bug simply because he could.

So throughout the long life of Linux there has been this much more diversified, seasoned, multi-cultured source for development feedback that has helped to make it a much stronger, more "mature" operating system, especially in terms of the way security was designed.  If there was ever a person out there who found a way to circumvent that security, there is at least another who knows exactly how to repair the flaw.  The reason viruses are able to best Windows is because their developers can only patch so many holes, and the ones they don't have time to get around to end up being exploited the most.  Third-party software developers that make Anti-Virus software make a killing because Microsoft is unable to handle this responsibility all by themselves, and even still, the best anti-virus software isn't perfect.

The reason anti-virus software isn't necessary in Linux is simply because the OS and its updates that patch  vulnerabilities do the exact job anti-virus software in Windows is meant for:  Prevent unwanted, malicious software or network activity from compromising the system.  If there were a flaw in Linux found that allowed something like that, it wouldn't be the job of some third-party software to safeguard the user against but the job of the OS itself.  The reason anti-virus software even exists is simply because Microsoft is unable to handle the immense work load of patching their own source code as well as a crowd of Linux geeks can.

Am I saying Linux is perfect and invincible to viruses?  Might it become more susceptible to viruses in the future if it were to ever become as popular as Windows is today?  I would think that with an increase in the number of users would also come a complimentary increase in the number of clever developers that would only help to increase the number of eyes available to find flaws and fix them.  Saying that Linux would get a lot of viruses down the road because more people are going to use it is like saying Wikipedia will become rife with widespread, uncontrollable vandalism because more people visit it.  It hasn't happened yet, and very likely never will happen because of the way it is designed, moderated and improved upon by the hive mind.

Sorry... I got carried away and made this post kinda long.  :p

:lolflag: but true.

---

