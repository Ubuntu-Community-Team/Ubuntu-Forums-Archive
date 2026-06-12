---
title: "Where is the REAL beginners forum?"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Carolla on 2009-06-05
I've just attempted to install Ubuntu 8.10 as a dual boot on my spare drive on my windows xp machine. I thought I'd done great, but now find it boots to the live user session I was running from my CD Drive and all my changes are lost. 

I thought I'd read around a bit for tips for beginners here. I don't even understand what you all are talking about! It's all still jargon to me, I was hoping the Absolute Beginners would speak clearly annotated English. :)

All I want to do is to get Ubuntu to run off my hard drive on the dual boot, then figure out how to get CIV IV BTS to run so I can play multiplayer games with my buds. I can handle the other apps - possibly just switch over to Ubuntu apps. 

HELP! I don't speak Linux!!!!

---

### Post by M4rotku on 2009-06-05
I'm sorry if this is completely off-base, but did you remove the cd?  I'm just wondering how it could still be running the live session.  If the cd is still in, then it will boot the cd before the harddrive.

---

### Post by QIII on 2009-06-05
The Live CD will allow you to make changes under certain conditions if you allow it to create space to do so.

But if you later did a full install (including repartitioning your drive), you likely lost all of that.

Are you able to boot properly to both XP and Ubuntu at least?

---

### Post by Cypher on 2009-06-05
How did you do the installation? By booting the Live CD and then clicking the "install" icon on the desktop? Once the installation was finished, during the restarting process, Ubuntu should have kicked out the CD and asked you to hit "Return" to restart? If so, that's the correct way. 

On the subsequent boot up, you shouldn't have put the CD in and should've seen the GRUB menu which should've listed not only Ubuntu but also your XP as a boot option?

If all of these are true, then you did the installation properly..

---

### Post by opethfan89 on 2009-06-05
If you are having trouble dual booting, I'd suggest following a video, [http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236), like that one. Its a great step-by-step guide, and there should be no issues afterwards.

If you have already installed Ubuntu (or tried) and its using the GRUB loader instead of your Windows loader, then you will want to uninstall GRUB and start on a clean slate. Its always best if you back up all your data (especially the data on your windows partition) and then do any sort of partitioning work.

The video was made for v5.10 of Ubuntu Linux, but the concept is still the same, and I used that video to help me install my own dual boot of Kubuntu 9.04.

Best of luck

---

### Post by furialis on 2009-06-05
Hopefully, I can help a little.

I think M4 is right. You probably just forgot to take the CD out of the drive.

If it's games you want to play, stick with XP. You can try running it in WINE, but I'm not sure how that'll go.

If you're a Windows guy, you're probably used to finding a program you want to use, downloading it double clicking it and it installs. It doesn't quite work that way with Ubuntu. Ubuntu apps come from what's called a repository. And I know you don't believe it, but almost everything you could possibly need will come from the repositories. You can find this magic pool of programs by going to System > Administration > Synaptic Package Manager.

There are several different repositories, and they are not all installed by default. In Synaptic Package Manager you will see a tab for third party software. That's where you can add repositories. [Medibuntu]("http://www.medibuntu.org/") is a repository that you are definitely going to want to add. This repository is where you are going to download all the stuff you need to play mp3's and movie files. Click on the Repository Howto link, and it will walk you right through the process. 

You should also get familiar with the command line. Terminal, Konsole, command line all refer to the same thing. Go to Applications > Accessories > Terminal and open it up. This is where you are going to need to learn to get software from.

---

### Post by presence1960 on 2009-06-05
Welcome!! You are in the **REAL **Beginner's forum. Maybe your expectations are what is confusing you. New Linux users should really forget everything they know or think they know about computers as it pertains to Windows. That knowledge will not help you in Linux and will only serve to get you frustrated by blocking your learning of the new operating system you have chosen to try.

Like anything else that we try new we must expect a learning curve that includes things previously unbeknownst to us. Expect to invest some effort & time learning and reading to learn.

Linux is not Windows and if you stick with it you will come to sing hallelujah as loud as you can that it is not like windows.

Try reading this : [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) 

Above all remember this is something unlike anything you have used before and keep an open mind. Spend time learning Linux, it is well worth it. Just like you learned how to use Windows, I am confident you didn't know jack about Windows when you started using it. That came over time and making plenty of mistakes. It will be the same with Linux. Stick it out!

---

### Post by andrew.46 on 2009-06-05
Hi Carolla,

> **Carolla said:**
> HELP! I don't speak Linux!!!!

I can understand your frustration :-). A good start might be:

The ultimate Ubuntu book!
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

and best of all this is a free download!

Andrew

---

### Post by Carolla on 2009-06-05
> **Cypher said:**
> How did you do the installation? By booting the Live CD and then clicking the "install" icon on the desktop? Once the installation was finished, during the restarting process, Ubuntu should have kicked out the CD and asked you to hit "Return" to restart? If so, that's the correct way. 

On the subsequent boot up, you shouldn't have put the CD in and should've seen the GRUB menu which should've listed not only Ubuntu but also your XP as a boot option?

If all of these are true, then you did the installation properly..

That's what happened the FIRST time, exactly. I messed with the live session from the CD, thought I'd try it. Then I booted to windows, opened the CD and installed it from the CD, it did call for me to remove the CD and booted properly with the dual boot menu. I changed my boot sequence to boot from the hard drive again as the first option, btw. However, later I booted from the hard drive without the Ubuntu CD in the CD drive and it did the dual boot menu, went through all that and went into something called "checking installation" which ran partitioners, etc, then gave me an error saying the CD didn't work. I put the CD in and got the live user CD session again. Is my hard drive installation messed up somehow? I didn't notice any errors in installing it.

---

### Post by Carolla on 2009-06-05
> **andrew.46 said:**
> Hi Carolla,



I can understand your frustration :-). A good start might be:

The ultimate Ubuntu book!
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

and best of all this is a free download!

Andrew

Thanks, I have that and it's just too much at this point. After I read a bit, my eyes just glaze over - without experience it doesn't make sense and I don't have quite enough savy to get started yet. :)  Edit: Maybe its just old age and a lack of mental flexibility - it used to be SO easy to deal with DOS back in the day!! lol

---

### Post by anewguy on 2009-06-05
I don't think you can INSTALL from the LiveCD WHEN you booted into Windows and then opened the CD and tried to install.  I wouldn't be a bit surprised if you actually copied the installation procedure to disk instead of doing an install.

In your case, you know Windows is installed, so BOOT using the LiveCD, then either select the option on boot to install Ubuntu, or start a live session with the CD and click on Install on the desktop.

Dave :)

---

### Post by rcayea on 2009-06-05
If you have the time, patience, and blank disk, I would suggest redownloading Ubuntu and installing it again with the new disk. It sounds like maybe your installation was corrupted.

---

### Post by steveneddy on 2009-06-05
Allright.....I'm backing out slowly. No one saw me here, right?

Look, nothing hidden in my hands.

I'm just gonna reach back and open the door, OK?

Everyone just stay calm. Just .. .. stay .. .. .. caaallmm.

---

### Post by Carolla on 2009-06-05
> **presence1960 said:**
> Welcome!! You are in the **REAL **Beginner's forum. Maybe your expectations are what is confusing you. New Linux users should really forget everything they know or think they know about computers as it pertains to Windows. That knowledge will not help you in Linux and will only serve to get you frustrated by blocking your learning of the new operating system you have chosen to try.

Like anything else that we try new we must expect a learning curve that includes things previously unbeknownst to us. Expect to invest some effort & time learning and reading to learn.

Linux is not Windows and if you stick with it you will come to sing hallelujah as loud as you can that it is not like windows.

Try reading this : [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) 

Above all remember this is something unlike anything you have used before and keep an open mind. Spend time learning Linux, it is well worth it. Just like you learned how to use Windows, I am confident you didn't know jack about Windows when you started using it. That came over time and making plenty of mistakes. It will be the same with Linux. Stick it out!

Thanks for the encouragement. I'm sure that when I get the hang of the jargon it'll all start to make sense. I'm not afraid of the "non Windows" aspect or learning a different OS - I came up through DOS after all! As I start to use it, I expect the various online manuals and helps will begin to fit my experience and I'll be like "oh!!! THAT's what they were talking about!!"

I don't normally eat white bread, I grind my own wheat and make my own. I don't like the way Microsoft assumes I am an idiot - so I guess I'll come here and prove it until I get it worked out! 

I read the link, useful, not quite the problem I have. I don't expect Windows and don't really want Windows, I'm just a bit lost as how to get started.

---

### Post by cariboo on 2009-06-05
I have nothing really to add, I just want to say welcome, all of us were in the same boat at one time. Unfortunately jargon comes with the territory, but we try to write in terms that everybody can understand.

---

### Post by Carolla on 2009-06-05
> **anewguy said:**
> I don't think you can INSTALL from the LiveCD WHEN you booted into Windows and then opened the CD and tried to install.  I wouldn't be a bit surprised if you actually copied the installation procedure to disk instead of doing an install.

In your case, you know Windows is installed, so BOOT using the LiveCD, then either select the option on boot to install Ubuntu, or start a live session with the CD and click on Install on the desktop.

Dave :)

Oh golly, now I'm not sure if that was even what I did! lol 

I did run the LiveCD session and looked at the installation from within that (before I tried whatever I did do, I'm going to have to start taking notes as I'm working on this a little bit here and there). It was not entirely clear which drive was the one with Windows on it and which one was the empty drive I wanted to use. The word "Partition" scared me, I do not want to partition over or format my Windows at this time, so I backed out. 

Whatever I did do gave me the choice of two drives with the Windows names on them to install to, so I was confident I wasn't messing up my Windows boot drive. Looking back on it, I may have booted from CD and used the dual boot installation option there. Oops, I'm so sorry that I'm a bit airheaded. Can I use the excuse of being blonde? A grandmother?? It's pretty sad when I have to ask the experts to even figure out what *I* did for me! 

Should I download the file again and burn another CD? Last time I downloaded on this computer, copied to my husband's (he's got a dvd with a burner, I don't), found he didn't have the software to burn the iso, copied the file to computer #3 which is SUPPOSED to be my Ubuntu computer and burned the file on that CD burner. I'm afraid that is sort of how I normally do things. What can I say? I'm sure it would be better to wipe the drives on that one and install there, but we just built two new 'puters and haven't taken all the backed up data off #3 yet. More than you want to know. :roll:

---

### Post by presence1960 on 2009-06-05
> **Carolla said:**
> Thanks for the encouragement. I'm sure that when I get the hang of the jargon it'll all start to make sense. I'm not afraid of the "non Windows" aspect or learning a different OS - I came up through DOS after all! As I start to use it, I expect the various online manuals and helps will begin to fit my experience and I'll be like "oh!!! THAT's what they were talking about!!"

I don't normally eat white bread, I grind my own wheat and make my own. I don't like the way Microsoft assumes I am an idiot - so I guess I'll come here and prove it until I get it worked out! 

I read the link, useful, not quite the problem I have. I don't expect Windows and don't really want Windows, I'm just a bit lost as how to get started.

Rome wasn't built in a day. This community is awesome and will be a great experience. Common sense applies here too. if you get too frustrated log off and walk away for a while. Take a break & come back to it later. We all have been a complete newbie so most will be willing to help you. 

BTW that free pdf download someone linked is a good place to start. If we all can run Linux so can you. Again remember "Rome wasn't built in a day!" Hang in there and come to this forum. You will learn and begin to understand just as we did and still do.

Here's a good link with a lot of good info that I found I was able to understand and follow in the beginning. I still refer to it today. [http://www.psychocats.net/](http://www.psychocats.net/)

---

### Post by jmszr on 2009-06-05
Carolla,

This Sticky by ugm6hr has a wealth of information: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) (and yes, some might be a little eye-glazing at first). It is an excellent resource for the beginner (and not-so beginner) and well worth bookmarking. This is a good guide for dual-booting: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by QIII on 2009-06-06
No worries, Carolla . . .

I started the computer gig using punch cards and acoustical coupling devices.

I've been using Ubuntu since Warty, other early Linux distros and Unix before that.

If you don't feel like a noob, you aren't trying to learn anything new.

---

### Post by mpennell on 2009-06-06
Carolla,
I SO know this feeling. I showed up here just days ago and sort of... made an *** of myself.

But hey. I'm cool now. I know all the jargon now... No, I don't. Just messin' with ya. I am working on the challenge of arriving at Staples before closing time so I can buy CDs to back up my family photos before I attempt to install Xubuntu. That's where I stand next to the others around here...;)

I did have the success of figuring out how to use my CDRW drive as the bootable drive after my other drive conked out. THAT was a cool moment for me! 

Hey-- do you drive a Corolla? I do-- 95 stick shift. I love it! Very reliable.

Oh-- and your title for the thread reminds me of my suggestion to start a forum called the "Completely !@#$% Clueless" forum. I will be its king.

...haha! It won't let me use the three letter word for "donkey." Ah, come on!

---

### Post by andrew.46 on 2009-06-06
Hi Carolla,

And I forgot to mention in my previous post: 'Welcome to Ubuntu'!!! I hope your initial problems will be resolved and you will start to enjoy both the distro and the community that has grown around it :-).

All the best,

Andrew

---

### Post by jonobr on 2009-06-06
Hey Carolla


Dont dis the dos :-)

Welcome to the funny farm!!!

---

### Post by chokey on 2009-06-06
stick with it.  i tried SUSE about 5 years ago and in the end had to revert back to xp because it didn't quite do what i needed and i found that early linux experience all about 'programmers' - installation of an app was a nightmare.  i tried ubuntu last year and found that usability had gone through the roof...

...now i'm a complete convert.  it's quicker and more stable.

---

### Post by andrew.46 on 2009-06-06
Hi jonobr,

> **jonobr said:**
> Dont dis the dos :-)

Well believe it or not I had to write a batch file for windows the other day and it brought back a lot of memories from DOS 6.22. I am sure there are some here who have used older versions :-).

The batch file was for running the classic cli newsreader [slrn under Windows]("http://www.andrews-corner.org/usenet/slrn_windows_1.png").

Andrew

---

### Post by QIII on 2009-06-06
I come from a time before MS DOS, and even M DOS.

Glory days!

---

### Post by jonobr on 2009-06-06
We are going to end up starting our own thread here.

The first code I wrote was on a atari 800 xl ,
ill never forget it, it was in the back of the user manual,
all in basic,
Spent the weekend typing it, and a week debugging it.

In the end I got it to work.
Talk about disappointment, 
I was expecting something akin to Halo or Left 4 dead, or at least something to make my jaw drop.
Instead I got a very bad rendition of a rainbow with about 5 colors.

You tell the kids today that and they wont believe you :-)

---

### Post by QIII on 2009-06-06
Oh, god!  Basic!

FORTRAN, COBOL, Pascal, C ...

And none of this mamby-pamby IDE stuff!

---

### Post by iponeverything on 2009-06-06
UNIX and UNIX-like systems are nothing more dos on steroids. Its a very natural transition. I switched directly from dos to UNIX (ultrix)  in 1991 and to linux in '93 -- bypassing the whole windows "revolution".  No system that I have ever owned has had Windows as it primary OS and the majority of them never had it installed as at all.

I have to say that the first time I used UNIX and was playing around with streams, pipes, filters (utils like grep, sed and awk), I/O redirection and process control -- it was like someone took off the handcuffs!

Some people don't think that wondering around an unfamiliar environment is fun, but I live for it and still get a great kick out discovering new things. 

Speaking off cool something like this could give NetAPP a run for their money:

[http://www.linux-mag.com/cache/7345/1.html](http://www.linux-mag.com/cache/7345/1.html)

---

### Post by QIII on 2009-06-06
Kabul?

I have one (semi-adopted, sort of, no father, lived with us) kid headed your way in September and another in the Summer of 2010.

Keep an eye out for them.

As I recall from my days on the two-way live fire range, toilet paper was in high demand.  Could you stock up on some for my boys?

---

### Post by k3lt01 on 2009-06-06
Memories, pressed between the pages of my mind
Memories, sweetened thru the ages just like wine

Quiet thought come floating down
And settle softly to the ground
Like golden autumn leaves around my feet
I touched them and they burst apart with sweet memories,
Sweet memories

Of holding hands and red bouquets
And twilight trimmed in purple haze
And laughing eyes and simple ways
And quiet nights and gentle days with you

Memories, pressed between the pages of my mind
Memories, sweetened thru the ages just like wine,
Memories, memories, sweet memories

---

### Post by HavocXphere on 2009-06-06
> **Carolla said:**
> I'm just a bit lost as how to get started.
Don't worry...everyone starts there.

> **Carolla said:**
> CIV IV BTS to run so I can play multiplayer games with my buds
You'll find that in most cases a well-crafted google search will turn up tons of stuff on pretty much any ubuntu-related topic you can think of:
[Like this[link]]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+civilization+4&btnG=Google+Search&aq=f&oq=&aqi=")

---

### Post by Carolla on 2009-06-06
Oh my....

I remember my IBM PC Jr - my first computer! I remember old magazines and ever so carefully copying line for line programs into the command prompt to run little basic games. I remember DOS 3.2 and I'm quite sure that a few years ago the transition into something like Ubuntu would have been a breeze. Somehow in the last ten years I'm a bit vaguer and a lot lazier. And I'm NOT that old! 

I remember meeting with my younger brother when he worked for Hullet Packard in Boise (that spelling doesn't look right somehow!) and he excitedly showed me "Adventure" text game on their mainframe at work (after hours, of course!). He is a programmer and runs a UNIX server I think - of course I didn't even think to ask him! LOL  I really am a space cadet lately! To be honest, I think it has to do with playing CIV every night until 2 am, then trying to run a more normal schedule during the day. 

I'm almost embarrassed to have to ask questions, except I know people love to answer questions and forum addicts love to carry on conversations - I won't say how I know THAT! 

Anyways... if I can go back to the subject at hand for a moment, what is the consensus on whether I ought to re-download Ubuntu and should I go with version 8.10 or try another one? 

Fortunately I have my daughter home for the weekend, she's very sharp at computer stuff and I'm sure we can figure stuff out together, if we can find any time to mess with it. 

Thanks again for the warm welcome and the help!

---

### Post by k3lt01 on 2009-06-06
I'd download 9.04 as its the latest version.

You may want to take a look at these sites as well. [UbuntuGeek]("http://www.ubuntugeek.com/") and [Psychocats]("http://www.psychocats.net/") are both great sources of information.

Remember to have fun :popcorn:

---

### Post by Carolla on 2009-06-06
Ok, assuming that my installation CD isn't working right, I'm going ahead and downloading 9.04 tonight. I'll burn the ISO tomorrow. 

Do I need to remove the Ubuntu installation on  my hard drive before I reinstall (esp with the newer version)? If so, how do I go about that properly?

---

### Post by ashmew2 on 2009-06-06
Hi Carolla , if you have a USB Pen Drive , I'd suggest using that to install Ubuntu onto your main hard drive instead of burning the ISO to a CD (I personally hate burning CDs because of all the bad burns and stuff). Just download and run unetbootin to make a live bootable USB Pen Drive. Itll also go faster than a CD.

And i think you should be good if you just format the partitions you previously installed Ubuntu to.Dont worry about this , you can do it in the partioning option which you will get when installed Ubuntu 9.04 Jaunty.

To install Unetbootin : Go here : [http://nchc.dl.sourceforge.net/sourceforge/unetbootin/unetbootin-linux-344](http://nchc.dl.sourceforge.net/sourceforge/unetbootin/unetbootin-linux-344)

Download and save it to your Desktop. Next in a terminal (one line at a time)  :
```

sudo apt-get install mtools p7zip-full

cd ~/Desktop
chmod +x unetbootin-linux-344
./unetbootin-linux-344
```

This should bring up unetbootin window.

---

### Post by SunnyRabbiera on 2009-06-06
> **Carolla said:**
> Ok, assuming that my installation CD isn't working right, I'm going ahead and downloading 9.04 tonight. I'll burn the ISO tomorrow. 

Do I need to remove the Ubuntu installation on  my hard drive before I reinstall (esp with the newer version)? If so, how do I go about that properly?

You shouldnt have to, normally the installer will detect your current system and be able to overwrite the previous install.
Bad installs happen, as do bad burns.
When burning your Ubuntu disk try lower speeds on your burner and make sure to check the integrity of the disk.
Also if Ubuntu still doesnt work, try other linuxes too.
Distrowatch is a good place to start on that, Ubuntu just happens to be popular though so it gets a lot of media to it.

---

### Post by iponeverything on 2009-06-06
> **QIII said:**
> Kabul?

I have one (semi-adopted, sort of, no father, lived with us) kid headed your way in September and another in the Summer of 2010.

Keep an eye out for them.

As I recall from my days on the two-way live fire range, toilet paper was in high demand.  Could you stock up on some for my boys?

Your right about the TP, its not easy to come anything that can't double as sandpaper. Shipping out to Dushanbe very soon, so there won't any overlap. Things are heating up a bit, so make sure they keep a [towel]("http://www.towel.org.uk/index.php/The_Hitchhiker%27s_Guide_to_the_Towel") handy.

---

### Post by ashmew2 on 2009-06-06
Well no offence intended , but lets help the OP first and then talk about our own computer experiences! xD

---

### Post by chokey on 2009-06-06
> **ashmew2 said:**
> Hi Carolla , if you have a USB Pen Drive , I'd suggest using that to install Ubuntu onto your main hard drive instead of burning the ISO to a CD 

i installed via this method last weekend, and for a non-programmer type it was dead easy.  highly recommended.

---

### Post by 73ckn797 on 2009-06-06
> **jmszr said:**
> Carolla,

This Sticky by ugm6hr has a wealth of information: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) (and yes, some might be a little eye-glazing at first). It is an excellent resource for the beginner (and not-so beginner) and well worth bookmarking. This is a good guide for dual-booting: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

These are good info source links. I could only add to begin at the beginning. I assume you may have already done that but I pass along this link, similar to the one I quote above only from the first page:
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

---

### Post by shadowlands on 2009-06-06
This is true  one musst forget what one has learned or think they know, but a lot of folk in the forum are computer savvy and tend to forget that some folk here  are just end users. Individuials who wwere tired of being shafted by companies and for end users one must go step by step in their directions and often times it take pics to go along with the written  stuff so folk can see as well as read the directions in order to get things right.  

If one would care to read some information in the field of library science one can see how this end user and computer savvy mind are often tend to come in to conflict.  > **presence1960 said:**
> Welcome!! You are in the **REAL **Beginner's forum. Maybe your expectations are what is confusing you. New Linux users should really forget everything they know or think they know about computers as it pertains to Windows. That knowledge will not help you in Linux and will only serve to get you frustrated by blocking your learning of the new operating system you have chosen to try.

Like anything else that we try new we must expect a learning curve that includes things previously unbeknownst to us. Expect to invest some effort & time learning and reading to learn.

Linux is not Windows and if you stick with it you will come to sing hallelujah as loud as you can that it is not like windows.

Try reading this : [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) 

Above all remember this is something unlike anything you have used before and keep an open mind. Spend time learning Linux, it is well worth it. Just like you learned how to use Windows, I am confident you didn't know jack about Windows when you started using it. That came over time and making plenty of mistakes. It will be the same with Linux. Stick it out!

---

### Post by Carolla on 2009-06-06
I went to the [http://www.psychocats.net/](http://www.psychocats.net/) and read through the Ubuntu tutorials - very good stuff! Thanks! It was very helpful because there were pictures and simple explanations of what was what, what it means and how to use it. I hope to become much more than just an end user, but am certainly starting out there. 

Looking at the pictures and explanations, I realized that, yes, I did install by opening the CD from within Windows and used the Wubi installer (just didn't know it!). That was actually the recommended way to do it if I wanted to be sure to keep my Windows installation intact and my gut feeling that I could get into trouble by booting the LiveCD and installing from the boot menu was correct - you could easily erase your Windows partition. 

So, given that information, I guess something just went wrong with the installation. I downloaded the Ubuntu 9.04 version last night and will burn the iso later today and try again. It's quite possible there is something wrong with my CD or just the actual installation. I'm sure that having the right information will help you all to help me and I highly recommend the Psychocats site for total newbs. 

Unfortunately I don't have a cool USB drive to use.

---

### Post by philinux on 2009-06-06
Points to remember.

Burn at no more than 4x speed.

When you boot the livecd up, at the menu, choose "check cd for defects".

---

### Post by samcan on 2009-06-06
I've gotten Civ IV to run (not BTS expansion, but I don't have it). It runs pretty well, minor graphical glitches, but not bad at all. The guide I used is at:

[http://forums.civfanatics.com/showthread.php?p=8038403]("http://forums.civfanatics.com/showthread.php?p=8038403")

It's the first attachment. It uses PlayOnLinux, which uses Wine.

---

### Post by mpennell on 2009-06-06
Someone mention psychocats? I have one of those! Actually, she's mellowing a bit...

I found their site too and it was helpful.

Meow.

---

### Post by crapshoot on 2009-06-06
Hi Carolla,

From one neophyte to another, WELCOME.  I too remember computers when they had one 5.25" drive, no HDD, and connecting to a network was left to the compsci majors.  My first was a zenith 386 monochrome (green) screen.  

I just brought back a dell dimension from the dead and decided to dedicate it to a nonproprietary software box (where possible).  

I only have one word of warning for the installation.  I went and installed the latest version (Jaunty) and it tried my patience.  I used the instructions from ubuntu (download, burn, check the hash(?), check the burn, check the disk, etc.).  I found the instructions pretty straight forward. 

Unfortunately, Juanty seems to be a bit of a work in progress.  What I did, and you may want to as well to keep the learning curve a little less than a cliffside LOL, is install one of the 8.xx versions (Heron or Intrepid).  

It is already done and there is a lot more solutions documented if something comes up.  I switched to Heron and I am quite happy.  I only have one problem to fix but everything seems to be running.

---

