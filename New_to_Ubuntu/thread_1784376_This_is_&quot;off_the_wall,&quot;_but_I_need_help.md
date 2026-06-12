---
title: "This is &quot;off the wall,&quot; but I need help"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by lareynatortura on 2011-06-16
Hi all,

This post is kind of random, but I need help. . I have a Toshiba NB205 mini notebook running both Lubuntu and Windows XP.  In the Lubuntu partition, everything works great. No problems there.

But, in the Windows partition, I'm having a weird problem.  I'm trying to use some freeware that I got from CNET on the XP partition, and it's just not working. . When I start the program, I am immediately prompted to send an error report to Microsoft.  The error reads, "[the program] has encountered a problem and needs to close.  We are sorry for the inconvenience."  Yes, pretty standard. . I've seen that error before, but I've never had an issue like this, where a program just won't start and immediately displays that message each time it is opened.

I tried to do some research on possible causes and solutions before I posted in this forum, but it was slim pickin's.  The closest to any helpful information I could find was "make sure your video drivers work, they are notorious for messing up programs."  Well, that quote is not direct--the actual response was a bit incoherent--but it made me think about something.

My drivers.  I'm not sure if all my drivers are correct and are working properly.

Does anyone have any advice to offer me?

P.S.  I chose to bring my problem here to Ubuntu forums because most everyone here is waaay more "with it" than individuals on some of the other forums out there. . and I've learned to just forget Yahoo answers. . Some of the worst advice ever is given there! o.O  :-x  (The Toshiba forums are also good, but some people have frowned on my dual-booting ways. . )

---

### Post by LowSky on 2011-06-16
Hi welcome to the forums.. Unfortunately your issue can be any number of things. We need to know more information.

Could you please tell us the name of problematic application? Have you tried running it using WINE on Lubuntu? Is the "Freeware" a safe program and not malware? Are you sure you need it, and maybe there is a linux alternative?

---

### Post by lareynatortura on 2011-06-16
> **LowSky said:**
> Hi welcome to the forums.. Unfortunately your issue can be any number of things. We need to know more information.

Could you please tell us the name of problematic application? Have you tried running it using WINE on Lubuntu? Is the "Freeware" a safe program and not malware? Are you sure you need it, and maybe there is a linux alternative?

Hi there, LowSky

Thank you for your kind response.

The program I am attempting to use is called VDownloader. It can be found on CNET.  To my knowledge, the program is safe and benign.  I would love to use a Linux alternative. .but, I just use my Lubuntu for accessing websites containing sensitive information (Banking, shopping, work, college, etc.).  I use my Windows XP for more frivolous, entertainment purposes.  I decided to set the computer up this way because my husband and I would like to use more freeware on Windows. (More so my husband. I avoided most freeware as much as I could, because I was concerned with malware. . but well, just the other day, my husband inadvertently downloaded a trojan while snagging some freeware that he thought was safe.  Not fun, but I felt that this was a good solution for me in my current situation).

If you need any more information about my machine, I'd be happy to oblige.  I am also open to suggestions for possible alternatives.

lareynatortura :)

---

### Post by mister_playboy on 2011-06-16
Do you use Firefox?  The Download Helper add-on has similar functionality: [https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/](https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/)

For your information, any discussion about the subject of downloading videos from sites such as Youtube on this forum will result in the thread being locked.

---

### Post by pqwoerituytrueiwoq on 2011-06-16
there are alot of alternatives to that application
[http://alternativeto.net/software/vdownloader/?platform=linux](http://alternativeto.net/software/vdownloader/?platform=linux)
the top rated was mentioned by mister_playboy

---

### Post by deconstrained on 2011-06-16
This seems like it's entirely a Windows issue and has nothing to do with Ubuntu. You may have downloaded a build of the program intended for a different CPU architecture or different version of Windows than the one you're using.

Just a bit of background info: most programs are mostly made of files that contain binary files (instructions that are loaded into memory and issued directly to the processor). However, these instructions often require "shared libraries" (preexisting common system binaries that are used by other programs as well), so if the libraries are missing or in a location different from the one the expects them to be in, the program won't run. Also, if the binaries are not built/compiled for the kind of CPU architecture (i.e. 32 or 64 bit) that it is to be used on, it won't run properly.

More:
[http://windows.microsoft.com/en-US/windows7/32-bit-and-64-bit-Windows-frequently-asked-questions](http://windows.microsoft.com/en-US/windows7/32-bit-and-64-bit-Windows-frequently-asked-questions)

---

### Post by dFlyer on 2011-06-16
This really sounds more like a windows problem and not a linux question. Have you search the internet for an answer or tried a windows forum? I haven't used windows for so long I'm unable to offer any advice.

---

### Post by lareynatortura on 2011-06-16
> **mister_playboy said:**
> Do you use Firefox?  The Download Helper add-on has similar functionality: [https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/](https://addons.mozilla.org/en-US/firefox/addon/video-downloadhelper/)

For your information, any discussion about the subject of downloading videos from sites such as Youtube on this forum will result in the thread being locked.

Yes, I figured that. : )


I actually switched to Chrome (not exactly sure if I like it more than Firefox, though. . ) But, thank you for presenting another option to me.

---

### Post by lareynatortura on 2011-06-16
> **pqwoerituytrueiwoq said:**
> there are alot of alternatives to that application
[http://alternativeto.net/software/vdownloader/?platform=linux](http://alternativeto.net/software/vdownloader/?platform=linux)
the top rated was mentioned by mister_playboy

Thank you.  I appreciate it.

---

### Post by lareynatortura on 2011-06-16
> **dFlyer said:**
> This really sounds more like a windows problem and not a linux question. Have you search the internet for an answer or tried a windows forum? I haven't used windows for so long I'm unable to offer any advice.

Hi dFlyer,

Yes, definitely a Windows issue.  :-/  I didn't mean to bother anyone, though.  I decided to post here because I figured it would be more likely for me to get advice. (It seems to me like most Linux users know more about Windows than the Windows users. . That's my opinion, but anyway!) Also, like I mentioned, I just started to dual-boot that computer.  I was uncertain if that had anything to do with the problem, or not.

Thank you for your reply

---

### Post by deconstrained on 2011-06-16
> **lareynatortura said:**
> I just started to dual-boot that computer.  I was uncertain if that had anything to do with the problem, or not.
Most likely not. Have you run the program successfully in Windows *before* setting up Linux? If the answer is no then there is no way you could fault an installation of Linux for the problem.

---

### Post by lareynatortura on 2011-06-16
> **deconstrained said:**
> This seems like it's entirely a Windows issue and has nothing to do with Ubuntu. You may have downloaded a build of the program intended for a different CPU architecture or different version of Windows than the one you're using.

Just a bit of background info: most programs are mostly made of files that contain binary files (instructions that are loaded into memory and issued directly to the processor). However, these instructions often require "shared libraries" (preexisting common system binaries that are used by other programs as well), so if the libraries are missing or in a location different from the one the expects them to be in, the program won't run. Also, if the binaries are not built/compiled for the kind of CPU architecture (i.e. 32 or 64 bit) that it is to be used on, it won't run properly.

More:
[http://windows.microsoft.com/en-US/windows7/32-bit-and-64-bit-Windows-frequently-asked-questions](http://windows.microsoft.com/en-US/windows7/32-bit-and-64-bit-Windows-frequently-asked-questions)

Hi deconstrained, 

Thank you for the tid-bit of information.  I do not think it is that sort of problem, though.  I'm almost certain the program can run with my version of Windows. (I could be wrong, but I'm pretty sure the specs for the application included my version of Windows).

Yes. . this is definitely a Windows issue.  Please do not misunderstand me--I'm not trying to waste anyone's time.  I'm trying to learn how to figure these things out.  I want to learn more about computers in general, and I find so much more help and valuable information from many Linux users, than I do Windows users.  Oddly enough.  :-|  Just my opinion, though!  

I would have ditched Windows completely, were it not for two things:

1. I like to play games like "The Sims" series, and whatnot. (I'm not sure if those will work with Linux distros, or not. I've never actually looked into it).

2. My husband is stubborn and doesn't really want to learn Linux!  (Just reading this one makes me laugh. . Oy, funny.  And yes, I have tried to show him the more "Windows user-friendly" side of Linux. . No dice!)

:-|

---

### Post by lareynatortura on 2011-06-16
> **deconstrained said:**
> Most likely not. Have you run the program successfully in Windows *before* setting up Linux? If the answer is no then there is no way you could fault an installation of Linux for the problem.

Hi again deconstrained,

I understand now.  That makes perfect sense.  I am not sure if the program would have ran correctly with Windows before, or not.  I installed Lubuntu along side my Windows XP, before I had added the program.

You're more than likely right--maybe it would not have worked anyway.

Dang piece of crap freeware!  Dang piece of crap Windows XP!

Sigh.  Ever since I got that machine up and running, I've realized just how much I hate XP.  If I have to be stuck with Windows, I'd personally rather be using 7.  (That's what I run on my Satellite.  Definitely not as cool as Linux, but. . it'll do.

---

### Post by lareynatortura on 2011-06-16
Well guys,

I think I know what I'm going to do--I'm going to just ditch that program.  I don't have the patience for this, and I don't want to end up in the virtual--or perhaps even the real!--hoosegow!

Thank you for all your help, though.  I definitely want to keep logging on, because I think I can learn a lot here.

---

### Post by idoitprone on 2011-06-16
which sims?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664)

simd 3 work pretty well with wine the last time i looked. the rest not so much

---

### Post by lareynatortura on 2011-06-16
> **idoitprone said:**
> which sims?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664)

simd 3 work pretty well with wine the last time i looked. the rest not so much

Ah, I wish Sims 3!

I currently play Sims 2, and occasionally, I play Sims 1 (I still have all my old stuff. . o.o); I know, I know. I'm lame and behind the times. XD

---

### Post by idoitprone on 2011-06-16
> **lareynatortura said:**
> Ah, I wish Sims 3!

I currently play Sims 2, and occasionally, I play Sims 1 (I still have all my old stuff. . o.o); I know, I know. I'm lame and behind the times. XD

look at me, i play aoe2 occasionally and boot legged worms. lol I not in a  position to judge.

 You can try both sim, but try to use the latest wine. The results are both a little outdated. Sim2 is test with 1.3.17 and sim1 with 1.1 while current version of wine is at 1.3.22.

---

### Post by lareynatortura on 2011-06-16
> **idoitprone said:**
> look at me, i play aoe2 occasionally and boot legged worms. lol I not in a  position to judge.

 You can try both sim, but try to use the latest wine. The results are both a little outdated. Sim2 is test with 1.3.17 and sim1 with 1.1 while current version of wine is at 1.3.22.

Hee hee hee!  You're awesome!  I have AOE2 as well.  I used to have Civilization 2 also, but I succumbed to an upgrade on that one. .-.-  

I have a question for you, idoitprone.  Are you concerned about downloading things and using your machine for entertainment purposes--music, Hulu, games, etc.--while at the same time, using it for banking?

That is a major concern of mine, especially since I have ran Windows. . :-/

---

### Post by idoitprone on 2011-06-16
that is a question of the browser. Most viruses, trojan, malware are basically browser base. People are making less and less operating system viruses since windows step up their game and released vista.

There is few browsers i will never touch unless i am forced to. internet explorer and saferi.

You can play aoe2 on linux, just get a no-cd crack with the legal copy game(when i mean legal, i mean you brought it, rented it, or borrow indefinately from a friend, not pirated)

---

### Post by lareynatortura on 2011-06-17
> **idoitprone said:**
> that is a question of the browser. Most viruses, trojan, malware are basically browser base. People are making less and less operating system viruses since windows step up their game and released vista.


So you use two different browsers? -One for banking, one for surfing and such?

-That is what I have done for a long time. My husband thought I was crazy. .

> **idoitprone said:**
> 
There is few browsers i will never touch unless i am forced to. internet explorer and saferi.

OY!  Same here! >.<

---

### Post by idoitprone on 2011-06-17
> **lareynatortura said:**
> So you use two different browsers? -One for banking, one for surfing and such?



nope, i use whatever browser i feel like it. I do not use seperate browser for banking and etc. Browsers such as chromium or firefox 4 maintain their commitment to security, so there not as much to worry about. Even if they try to download crap to my computer. With linux default exclude executable. I have less to worry about.

i just dont save passwords, security risk on it own

---

### Post by shibu_sawyer on 2011-06-17
Is only that downloader Application in windows creating the problem,then remove it and try other downloaders like speed bit,if the problem is with windows  itself ,i suggest you to repair it using boot-up cd.,

---

### Post by lareynatortura on 2011-06-17
> **shibu_sawyer said:**
> Is only that downloader Application in windows creating the problem,then remove it and try other downloaders like speed bit,if the problem is with windows  itself ,i suggest you to repair it using boot-up cd.,

Thank you, shibu_sawyer.  I agree with you completely.  While I decided to not install the particular application, I thought perhaps I had a few driver conflicts and outdated drives.  Sure enough, I did.  One I fixed, another I could not, so I just disabled it.  I also downloaded some additional ones from Toshiba Support, and now my computer is a little closer to its out-of-the-box state.  Which is how I prefer that computer to be.

(I also should mention that this machine does not have a boot-up CD.  It slipped my mind to order one from Toshiba, and I could not create one myself at that time because the computer is a mini notebook, and does not have an internal CD or DVD drive.  These days, I have an external, though. )

:)

---

