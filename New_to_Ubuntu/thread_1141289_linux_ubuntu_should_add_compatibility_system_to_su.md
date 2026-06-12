---
title: "linux ubuntu should add compatibility system to support good window software"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by kai3393 on 2009-04-28
some software like microsoft office,winrar,some good utilities tool such as ccleaner and online games.With that compatibility system some window users to use linux ubuntu.I hope this system will add in linux to give more benefit to users.

---

### Post by Kosimo on 2009-04-28
That's exactly what Wine does 

[http://www.winehq.com](http://www.winehq.com)

But, just keep in mind that there are very good alternatives (free and open source) to many windows programs, OpenOffice, Firefox, Gimp, Pidgin, etc..

---

### Post by 3rdalbum on 2009-04-28
Er... ccleaner is a program that removes cruft from a Windows filesystem; it would do nothing useful on Linux. I also don't know why you'd need Winrar when Ubuntu is perfectly capable of unarchiving RAR files.

Haven't you heard of the Wine project? That allows some Windows software to be run. Writing a compatibility layer isn't easy; not by any means. It's not a project that would be reasonably complete in a year. Wine has been working towards the goal since 1993.

I personally would rather see more work being done toward improving Linux applications and infrastructure, rather than trying to run non-native apps.

---

### Post by kai3393 on 2009-04-28
but still no enough,linux cant support many platform games

---

### Post by the8thstar on 2009-04-28
No, it's the other way around : not enough game developers make games that run on Linux natively.

---

### Post by kai3393 on 2009-04-28
my good education software such as microsoft encarta 2009 is also cant support by wine,that mean wine still got problem to support microsft software that needed Microsoft .NET Framework

---

### Post by scheuri on 2009-04-28
Microsoft Windows is not Linux (or Ubuntu)
Linux(or Ubuntu) is not Microsoft Windows

Things are different, will be different and you MUST accept that.
You can do nearly everything (IMHO) with Linux, depending on your needs and your will to adapt to other software (or your will to check that software out at least).

Gaming, that is a different story...Linux is not a gaming platform (in comparison with MS Windows), or at least not yet. Period. No discussion there.

If you are not willing to accept that, you will have a hard time to find out about linux and you will eventually go back to windows, very likely flaming about linux.

Sorry to be so harsh, but...that is my experience.

good luck
scheuri

---

### Post by Spiritous on 2009-04-28
I think if you'd make a big brand name (WoW, CoD4... Etc) For Ubuntu, there would be a huge demand = Max profits... Wake up game developers!

---

### Post by kai3393 on 2009-04-28
I also want to help but i dont know how to start and i needed to wait after my big!!! final exam(the exam that will affect my future life)..........but i still can give some good suggestion.

---

### Post by lovinglinux on 2009-04-28
CCleaner? It is great and essential for Windows users because the registry becomes a mess pretty fast due to left overs from uninstalled software, crashes and malware, thus affecting the performance of the entire system.

Linux does not work this way. Settings are stored in text files, mainly on a per application basis. Thank God!

Check this out:
[http://en.wikipedia.org/wiki/Windows](http://en.wikipedia.org/wiki/Windows)
[http://en.wikipedia.org/wiki/Windows_registry#Equivalents_in_other_operating_systems](http://en.wikipedia.org/wiki/Windows_registry#Equivalents_in_other_operating_systems)

Additionally, Linux performance is not affected the way Windows is. There is no need for defrag tools and configuration files left over from uninstalled software are harmless.

---

### Post by Tibuda on 2009-04-28
> **kai3393 said:**
> my good education software such as microsoft encarta 2009 is also cant support by wine,that mean wine still got problem to support microsft software that needed Microsoft .NET Framework
have you tried [wikipedia]("http://www.wikipedia.org/")?
See also [http://mashable.com/2009/03/30/microsoft-encarta-to-close/](http://mashable.com/2009/03/30/microsoft-encarta-to-close/)

---

### Post by Mauler5858 on 2009-04-28
Kai,

It seems like you want to learn linux, but are still attached to some Microsoft things and gaming that cant come with you very well. One perfectly logical solution is to dual boot both XP(or vista) and Ubuntu.  Heck you could even use Wubi to try out Ubuntu while keeping what you need.

On the other hand per what you said earlier.  While the wine project and compatibility for Microsoft programs are a luxury and nice to have, its not Linux's fault for not providing that.  The blame lies in the developers hands that are not embracing Linux(and Mac as well in a lot of cases).  The true future of commercial software is hopefully moving in the direction of cross-platform development.  I personally go for open-source every chance i can, but i know that that cannot take care of all my needs....especially gaming.

---

### Post by moster on 2009-04-30
Uff, most of stuff on internet are in rar files. Is there a decent unrar prog? Xarchive, ark, file-roller cannot open some rar files. I cannot even extract subtitles for movie without winrar and wine.

---

### Post by oldos2er on 2009-04-30
> **moster said:**
> Uff, most of stuff on internet are in rar files. Is there a decent unrar prog? Xarchive, ark, file-roller cannot open some rar files. I cannot even extract subtitles for movie without winrar and wine.

 Run this in a terminal:
```
sudo apt-get update && sudo apt-get install rar unrar

```
 Now file-roller will be able to handle rar archives.

---

### Post by Tibuda on 2009-04-30
> **moster said:**
> Uff, most of stuff on internet are in rar files. Is there a decent unrar prog? Xarchive, ark, file-roller cannot open some rar files. I cannot even extract subtitles for movie without winrar and wine.

All those applications only use the tools available in your system. Like multimedia codecs. If you [install rar and unrar]("apt:rar,unrar"), then all these applications you listed will be able to open rar files.


About the thread topic (Wine), I agree very much with what Mark Shuttleworth said in the [Open Week]("https://wiki.ubuntu.com/MeetingLogs/openweekJaunty/AskMark"):
> (12:24:03 PM) jcastro: <rabbit251> jcastro: QUESTION: Do you see Wine (and Windows-compatibilty in general) or native Linux ports as the more important ingredient in the success of Ubuntu, or do they each play an important role?
(12:24:18 PM) sabdfl: they both play an important role
(12:24:30 PM) sabdfl: but fundamentally, the free software ecosystem needs to thrive on its own rules
(12:24:41 PM) sabdfl: it is *different* to the proprietary software universe
(12:24:54 PM) sabdfl: we need to make a success of our own platform on our own terms
**(12:25:08 PM) sabdfl: if Linux is just another way to run Windows apps, we can't win**
(12:25:13 PM) sabdfl: OS/2 tried that
(12:25:15 PM) sabdfl: next?


---

### Post by moster on 2009-05-01
> **oldos2er said:**
> Run this in a terminal:
```
sudo apt-get update && sudo apt-get install rar unrar

```
 Now file-roller will be able to handle rar archives.

Thank you and daniel for your posts but I was not clear enough. I have those already installed. It seems that these linux archivers cannot opet all rar archives. Try this for example. Winrar will open this for sure.

[http://www.prijevodi-online.org/prijevodi/supernatural/sezona_1/Supernatural%20-%2001x06%20-%20Skin.rar]("http://www.prijevodi-online.org/prijevodi/supernatural/sezona_1/Supernatural%20-%2001x06%20-%20Skin.rar")

---

### Post by anewguy on 2009-05-01
> **moster said:**
> Thank you and daniel for your posts but I was not clear enough. I have those already installed. It seems that these linux archivers cannot opet all rar archives. Try this for example. Winrar will open this for sure.

[http://www.prijevodi-online.org/prijevodi/supernatural/sezona_1/Supernatural%20-%2001x06%20-%20Skin.rar]("http://www.prijevodi-online.org/prijevodi/supernatural/sezona_1/Supernatural%20-%2001x06%20-%20Skin.rar")

The fault here is not do to handling of rar files - I just used package manager to open the rar file.  It shows a single .srt file inside the rar, and it doesn't know what a file type of .srt is - the rar itself is processed correctly, it's the .srt file inside it that it doesn't know what to do with.

What is this supposed to be for?  Is it supposed to be for a Windows platform, a Linux platform, a MAC or what?


EDIT:  Just did a little research to find out what a .srt file was.  The package manager extracts it fine to my home folder. and if you search the net for linux .srt file I think it is the very first entry that shows you how to use these with vlc.  If you don't have vlc installed, just go to synaptic package manager and install it, then just follow the instructions in one of the many posts that show in that search.

So:  there is NO problem with Ubuntu handling the rar file, and it extracts the .srt file fine.  The problem would appear to be you needing to install an application to USE the .srt file.

END OF EDIT


Dave :)

---

### Post by moster on 2009-05-01
> **anewguy said:**
> The fault here is not do to handling of rar files - I just used package manager to open the rar file.  It shows a single .srt file inside the rar, and it doesn't know what a file type of .srt is - the rar itself is processed correctly, it's the .srt file inside it that it doesn't know what to do with.

What is this supposed to be for?  Is it supposed to be for a Windows platform, a Linux platform, a MAC or what?


Dave :)

Very strange. I cannot see what is inside of that rar with Xarchive, ark or file-roller. And I have installed rar and unrar... I am in updated ubuntu 8.10 hmmm

That is plain text file with subtitles in it.. nothing special..

---

### Post by anewguy on 2009-05-01
> **moster said:**
> Very strange. I cannot see what is inside of that rar with Xarchive, ark or file-roller. And I have installed rar and unrar... I am in updated ubuntu 8.10 hmmm

That is plain text file with subtitles in it.. nothing special..

I just click on the link you provided, it asks what I want to do by default - I choose the default of opening with Archive Manager (which as far as I know IS file-roller).  I'm just using a default installation of Ubuntu 8.10.  I know I have some extra packages installed, but I don't see how they would affect file-roller.  Perhaps you might want to try removing it (complete removal) with synaptic package manager, then completely reinstalling it as maybe a lib or something got stepped on.  Don't know what else to tell you.  

Good luck!!

Dave :)

---

### Post by moster on 2009-05-01
> **anewguy said:**
> I just click on the link you provided, it asks what I want to do by default - I choose the default of opening with Archive Manager (which as far as I know IS file-roller).  I'm just using a default installation of Ubuntu 8.10.  I know I have some extra packages installed, but I don't see how they would affect file-roller.  Perhaps you might want to try removing it (complete removal) with synaptic package manager, then completely reinstalling it as maybe a lib or something got stepped on.  Don't know what else to tell you.  

Good luck!!

Dave :)

I have solved the mistery. That file have extension ".rar" but actually it was zip archive. I rename it to .zip and everything is OK now. I am only not sure how it work at you :) . Ok, thanks for your help

---

### Post by anewguy on 2009-05-01
I don't know why it could possibly make any difference, but since it's dealing with a .srt file, and I was able to unrar it with Archive Manager, perhaps it's because I have the extra codecs installed?  I installed the good, bad and ugly sets for gstreamer as well as the ubuntu-restricted-extras - there may even have been a few more.  I can't for the life of me see how this would make any difference in unrar.

Dave :)

---

### Post by SunnyRabbiera on 2009-05-01
Most of these issues can be resolved as there are plenty of alternatives, you got to learn linux and windows are separate operating systems so dont expect an exact linux clone.

---

### Post by moster on 2009-05-01
It is solved. Read my previous post. Thanks again :)

---

### Post by pbpersson on 2009-05-01
> **kai3393 said:**
> I also want to help but i dont know how to start and i needed to wait after my big!!! final exam(the exam that will affect my future life)..........

Wine is a program loader and translation layer that can translate Windows API calls into XServer calls from what I understand.  It has been in development for years and has come a long way.

What exactly will you be developing that will be better and what language will you be using to create it?

C++?
Java?
Ruby?

You also have the option today of running a Windows session in a virtual machine.  That will give you 100% compatibility but there are some limitations on the graphics.

---

### Post by billgoldberg on 2009-05-01
> **kai3393 said:**
> some software like microsoft office,winrar,some good utilities tool such as ccleaner and online games.With that compatibility system some window users to use linux ubuntu.I hope this system will add in linux to give more benefit to users.

I realize you are new.

You seem to be under the false impression that Ubuntu can do such things.

Stuff like ccleaner and winrar are either not useful on Ubuntu or have equally good alternatives (p7zip-full with Fileroller).

Most online games run using Shockwave. 

Shockwave is from Adobe and they don't make a Linux version.

Most games are made for Windows. That's why it says "Games For Windows" on the box.

You don't complain about the fact you can't play xbox games on your playstation.

You should really read this article called "Linux is not Windows".
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by billgoldberg on 2009-05-01
> **anewguy said:**
> I don't know why it could possibly make any difference, but since it's dealing with a .srt file, and I was able to unrar it with Archive Manager, perhaps it's because I have the extra codecs installed?  I installed the good, bad and ugly sets for gstreamer as well as the ubuntu-restricted-extras - there may even have been a few more.  I can't for the life of me see how this would make any difference in unrar.

Dave :)

A .srt file is a subtitle file, not an archive.

---

### Post by anewguy on 2009-05-01
Right, but the .srt file was inside (the only file) a rar file.  I had no trouble unrar'ing the file and moving the .srt file.  I think he may have gotten a solution from a previous post.

Dave :)

---

