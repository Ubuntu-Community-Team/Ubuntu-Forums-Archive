---
title: "Update or Fresh install for 11.04?"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by Ken UK on 2011-04-27
Hi All,

I have a fresh install of 10.10 and was wondering which would be best, format and do a fresh install of 11.04 tomorrow or just upgrade?
If it was Windows it would be a no brainer, it would have to be a fresh install for sure!

I was also wondering about the new default software when you upgrade, will I still just have OOo with no LibreOffice etc.?

I've never done it before so don't know what to expect.

Thanks.

---

### Post by mörgæs on 2011-04-27
A vote for a fresh install, but wait a couple of months.

---

### Post by scott-ian on 2011-04-27
When you upgrade, you will end up with the old software and the new software.  So, you will have OOo and LibreOffice.  I have upgraded, and the process was similar to installing a large number of updates in the update manager.  A clean install probably would be better, but it is not necessary.  If you can easily do so, you can go ahead and do a clean install.

---

### Post by Ken UK on 2011-04-27
Stay on 10.10 for acouple of months and then fresh install or you mean upgrade to 11.04 then wait?

EDIT: Thanks Scott, I suppose that makes the most sense :)

---

### Post by sammiev on 2011-04-27
I also vote for fresh install. I tried the upgrade and ended up doing a fresh install the next day. GL :)

---

### Post by Ken UK on 2011-04-27
haha thats what I was thinking, at least you know none of the stuff from the old installation will mess things up lol

Votes are in and fresh install it is :D

---

### Post by wolfen69 on 2011-04-27
I see it's that time of year again! I always do fresh installs and have never had a problem. Therefore, I stick with what works. But that's just me.

But inevitably someone will jump in with: "I always upgrade and I've never had a problem". That's fine and dandy, but imho there's a better chance of success doing a fresh install, as with any OS.

After release there will be a flood of posts saying something like: "ubuntu broken after upgrade". Happens every 6 months.

---

### Post by Dutch70 on 2011-04-27
> **wolfen69 said:**
> I see it's that time of year again! I always do fresh installs and have never had a problem. Therefore, I stick with what works. But that's just me.

But inevitably someone will jump in with: "I always upgrade and I've never had a problem". That's fine and dandy, but imho there's a better chance of success doing a fresh install, as with any OS.

After release there will be a flood of posts saying something like: "ubuntu broken after upgrade". Happens every 6 months.

+1

This is what makes having a separate /home sooo nice. 
I wonder how that is going to work with 11.04 though.

---

### Post by Sal33m on 2011-04-27
An upgrade may take anywhere from 2 to 15 hours depending on your Internet speed. However, a fresh install will only take 30 minutes (excluding any tweeks after installation).

---

### Post by Fedz on 2011-04-27
> **Dutch70 said:**
> I wonder how that is going to work with 11.04 though.
I'd just highlight home & copy > paste to a 2nd drive or write to CD/DVD & replace after upgrade/fresh install :)

---

### Post by mörgæs on 2011-04-27
When people get into trouble upgrading, you can send them to this post:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

This saves a lot of time answering each and everyone.

---

### Post by Dutch70 on 2011-04-27
> **Fedz said:**
> I'd just highlight home & copy > paste to a 2nd drive or write to CD/DVD & replace after upgrade/fresh install :)

No need for that, I have /home on a separate partition. 

What I was wondering about is the .config folder that's in /home.

---

### Post by Rubi1200 on 2011-04-27
> **mörgæs said:**
> A vote for a fresh install, but wait a couple of months.
+1 to this suggestion.

When 11.04 comes out it will still be a bit rough around the edges so to speak.

If you wait 2-3 months, say until July, the initial bugs and problems (that were not detected during alpha and beta) will likely have been resolved and you can then do a fresh install.

Also, please read the release notes before upgrading/installing any version.

Testing it out as a LiveCD/USB beforehand is also usually a good idea.

---

### Post by wep940 on 2011-04-27
Another vote for fresh install, with an addition:

- if you don't have with your current installation, when you do the fresh install create a separate /home partition - then your personal data will be saved.

- also, be sure to tell the installer to format the partition(s) EXCEPT for your /home partition if you have one

---

### Post by Ken UK on 2011-04-27
How do you even create a separate /home partition? I've heard of that before and it seemed like a good idea but no idea how :D

For how long it takes might as well do a fresh install and as for download times, my Internet is slow but I'm sure Ill need a disc at some point anyway :)

All you guys that have spent time setting up fancy setups, do you need to do that from scratch if you fresh install?

In software fresh installs always tend to be the best option for anything I usually find.

---

### Post by Paqman on 2011-04-27
> **Sal33m said:**
> An upgrade may take anywhere from 2 to 15 hours depending on your Internet speed. However, a fresh install will only take 30 minutes (excluding any tweeks after installation).

If the main thing slowing down your upgrade is your internet speed, that's going to slow down the speed you get your install image from, too.

If it's a single machine, i'd just do the upgrade. If you've got multiple machines to do, it'd be quicker to use a disk or USB stick.

---

### Post by Rubi1200 on 2011-04-27
I haven't used this tutorial, but others have and it *may* work for you. This is to create a separate /home if you did not originally set one up:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

This explains how to do it when you install from scratch and are preparing partitions;
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

This also has useful information:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Ken UK on 2011-04-27
Thanks Rubi, that seems so simple I think even I could do it :D

"Note: Some more experienced Linux users like to have a fresh installation with every new Ubuntu release, and so **will have only a separate data partition and not a separate /home partition**, so all of their photos and music and documents will be preserved during a reinstallation, but all the settings will have to be redone. For novices, I would recommend just sticking with a separate /home partition."

What is the difference between a separate data partition and /home partition, presumably /home is just your documents (photos, documents, music etc.)?

---

### Post by Paqman on 2011-04-27
> **Ken UK said:**
> 
What is the difference between a separate data partition and /home partition, presumably /home is just your documents (photos, documents, music etc.)?

I don't see how having data on a separate partition from home denotes any kind of 1337-ness. A data partition is for your data (obviously), but there's no reason you could store that data in a home partition.

Home contains all your settings for applications, themes, etc. The advantage of keeping it separate is that as soon as you reinstall all the apps, they pick up the settings from the home folder. It means a fresh install can look and act just like the previous install.

By all means keep all your data in your home partition if you want.

---

### Post by Ken UK on 2011-04-27
Oh ok thanks I got confused but now its clear, sounds good though :)

---

### Post by Fedz on 2011-04-27
I've always done a seperate /home partition on previous installs but, on this 11.04 I did last week, I forgot so will either have to live with it or I was going to wait until the official 11.04 release & fresh install with 'correct' partitions :)

---

### Post by Dutch70 on 2011-04-27
Also, a separate data partition is especially useful if you multi-boot several OS's. They can all share a data prtn, really bad idea to share a /home. 
Having a separate /home for each causes a lot of confusion & takes up a lot of space, among other issues.

---

### Post by wykedengel on 2011-04-27
If I am running Ubuntu 11.04 beta 2, would you still recommend a clean install? Or, could I update into the final version?

---

### Post by Paqman on 2011-04-27
> **wykedengel said:**
> Or, could I update into the final version?

Yep.

---

### Post by RJ12 on 2011-04-27
I say do a fresh install, but if you are going to upgrade, use the CD... the new Natty installer has a built in upgrade option... this way at least if your install messes up you can use the CD to just reinstall :)

---

### Post by dFlyer on 2011-04-27
> **Ken UK said:**
> Hi All,

I have a fresh install of 10.10 and was wondering which would be best, format and do a fresh install of 11.04 tomorrow or just upgrade?
If it was Windows it would be a no brainer, it would have to be a fresh install for sure!

I was also wondering about the new default software when you upgrade, will I still just have OOo with no LibreOffice etc.?

I've never done it before so don't know what to expect.

Thanks.

Backup your home and than a fresh install. If you have programs you always install and use you can install then after the fresh install.

---

### Post by 3rdalbum on 2011-04-27
People, people, people; please get with the times :-)

Since 2008, it's no longer been necessary to keep /home on a separate partition. If you install Ubuntu over the top of an earlier Ubuntu (WITHOUT formatting), it will preserve the contents of /home even if it's on the same partition as everything else.

With 11.04, there's now an Upgrade option in the installer. This is not the same as a dist-upgrade; a dist-upgrade installs individual packages using Apt, but the Upgrade Install does a clean install and then downloads the other packages you were using in your earlier Ubuntu.

Upgrade Install preserves your /home, regardless of whether it's on the / partition or not.

I'd definitely recommend the Upgrade Install.

---

### Post by wep940 on 2011-04-27
Never seen this mentioned - even in the 10.04 info here on the forum it was still recommended to create a separate /home partition.  I thought the entire idea was so that you could keep your personal data, do a fresh install and let it reformat the other partition(s).  It's been a lot later than 2008 that I have seen this recommended, as well as doing a fresh install with partition formatting to avoid spurious libraries, etc., from still being there and causing difficulties.  I'm definitely not arguing, nor am I saying you're wrong.  What I AM saying is these recommendations have been on the forum from some pretty well respected members later than 2008.  That being said, I'd like someone to give us the definitive answer to how this all works now (are you there, Bohdi.Zazen??).  I don't have a clue now, and dumping this in here just confuses many of us who are not knowledgeable and are just looking to learn.  Do you have some official ubuntu docs you could point us to that gives the recommended way to do things now?

Thanks, as I'm just trying to learn.

---

### Post by wolfen69 on 2011-04-28
> **Ken UK said:**
> Thanks Rubi, that seems so simple I think even I could do it :D

"Note: Some more experienced Linux users like to have a fresh installation with every new Ubuntu release, and so **will have only a separate data partition and not a separate /home partition**, so all of their photos and music and documents will be preserved during a reinstallation, but all the settings will have to be redone. For novices, I would recommend just sticking with a separate /home partition."

What is the difference between a separate data partition and /home partition, presumably /home is just your documents (photos, documents, music etc.)?

I go a step further and use 3 hard drives at any one time. I have a separate /home partition, but I don't keep a lot of stuff in it. My stuff (media, photos, etc.) stays on another drive, and then it is backed up again on yet another drive. And then I back up my essential config files like .mozilla/.thunderbird, etc. just in case. Obviously I believe in storing stuff on separate drives. It may not be for everyone, but it's pretty much disaster proof. Then I can go nuts and install anything as much as I want.

I'm not the kind of computer user that believes in trying to make an install last forever. Plus, I thinks it's fun to reinstall every 6 months and use the latest and greatest. But like anything else, to each their own. And linux makes it possible to "have it your own way".

---

### Post by Rubi1200 on 2011-04-28
> **3rdalbum said:**
> People, people, people; please get with the times :-)

Since 2008, it's no longer been necessary to keep /home on a separate partition. If you install Ubuntu over the top of an earlier Ubuntu (WITHOUT formatting), it will preserve the contents of /home even if it's on the same partition as everything else.

With 11.04, there's now an Upgrade option in the installer. This is not the same as a dist-upgrade; a dist-upgrade installs individual packages using Apt, but the Upgrade Install does a clean install and then downloads the other packages you were using in your earlier Ubuntu.

Upgrade Install preserves your /home, regardless of whether it's on the / partition or not.

I'd definitely recommend the Upgrade Install.
This is very interesting. However, and wep940 also mentioned this, most of the experienced users here seem to suggest a separate /home partition. This is the first time, for me personally, that I have heard about what you are saying here. Moreover, have you tested this? Can you confirm that this is a method that we can recommend to new users? I suspect most new users would likely install and not even think about _not _formatting in the process, thus losing all their data.

---

### Post by laffinet on 2011-04-28
> **3rdalbum said:**
> 
With 11.04, there's now an Upgrade option in the installer. This is not the same as a dist-upgrade; a dist-upgrade installs individual packages using Apt, but the Upgrade Install does a clean install and then downloads the other packages you were using in your earlier Ubuntu.

Is this documented somewhere ? Link ?

Can someone confirm this ?

Thanks.

---

### Post by mörgæs on 2011-04-28
> **3rdalbum said:**
> People, people, people; please get with the times :-)

Since 2008, it's no longer been necessary to keep /home on a separate partition. If you install Ubuntu over the top of an earlier Ubuntu (WITHOUT formatting), it will preserve the contents of /home even if it's on the same partition as everything else.

With 11.04, there's now an Upgrade option in the installer. This is not the same as a dist-upgrade; a dist-upgrade installs individual packages using Apt, but the Upgrade Install does a clean install and then downloads the other packages you were using in your earlier Ubuntu.

Upgrade Install preserves your /home, regardless of whether it's on the / partition or not.

I'd definitely recommend the Upgrade Install.


That was good news! 

Recently there has been a lot of talk of deleting old posts in the fora and using the wiki more. Wasn't this a good candidate for being written in the wiki?

---

### Post by el_koraco on 2011-04-28
> **laffinet said:**
> Is this documented somewhere ? Link ?

Can someone confirm this ?

Thanks.

Sure. You just put the CD in and hit install, and get the option to upgrade. I'm not sure it works for 10.04, though.

---

### Post by laffinet on 2011-04-28
> **el_koraco said:**
> Sure. You just put the CD in and hit install, and get the option to upgrade. I'm not sure it works for 10.04, though.

Not exactly what I would call documentation...:roll:

---

### Post by georgelappies on 2011-04-28
> **Dutch70 said:**
> +1

This is what makes having a separate /home sooo nice. 
I wonder how that is going to work with 11.04 though.


For sure, a seperate /home and even /data is must have imo

---

### Post by aaron76 on 2011-04-28
I'm going for a fresh install as I just upgraded to 11.04 and my laptop wouldn't start up. Just got the Ubuntu logo.
Dunno what the problem was...
Luckily I still have my 10.10 cd around. I am downloading 11.04 and starting from scratch.

---

### Post by motherboyxx on 2011-04-28
[COLOR=black][FONT=Verdana]I am running beta2 with the gnome 3 shell but plan to do a fresh install in a couple months.  I am new to this game and have not set up the /home partition.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]On my fresh install I will set up /home, but when I save my files and programs I want on all future versions do I have to designate specifically /home as save location? Will it automatically save to this partition? [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I know this is noob, but heck that’s what I am.  [/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by wep940 on 2011-04-28
I would suspect as well that most will want to format when they install.  Somehow I just don't see an upgrade without formating not leaving old stuff behind that could cause problems.  For me, and this is just me speaking, I will go ahead and install with the formatting option(s) as i would rather do that than run into some unforeseen difficulty.  For others who may be reading the thread, this is just how I will do it.  If you decide to do a fresh install with formatting, be SURE to back up ANYTHING you want to keep before proceeding.
 
Somehow this new idea on updating just sounds like the old update but included as an option on the disk now.  I would like to know that it deletes ALL of the old system files before proceeding into an installation.

---

### Post by GaryTheCat on 2011-04-28
Just checking - for a fresh install are we talking selecting the 'Erase 10.10 and reinstall option?

Also I have a drive just for data, music etc on my PC that isn't in my /home ... will that get affected by doing the above?

And finally, if my data drive won't get affected by the install method above, could I make a copy of my /home directory in it and just replace that copy once I've reinstalled?

Thanks in advance

G

---

### Post by Dutch70 on 2011-04-28
> **motherboyxx said:**
> [COLOR=black][FONT=Verdana]I am running beta2 with the gnome 3 shell but plan to do a fresh install in a couple months.  I am new to this game and have not set up the /home partition.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]On my fresh install I will set up /home, but when I save my files and programs I want on all future versions do I have to designate specifically /home as save location? Will it automatically save to this partition? [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I know this is noob, but heck that’s what I am.  [/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
On future install you will have to set your mount point for that partition to /home just like you set your mount point for the install to /. Do not format the /home partition. 

> **GaryTheCat said:**
> Just checking - for a fresh install are we talking selecting the 'Erase 10.10 and reinstall option?

Also I have a drive just for data, music etc on my PC that isn't in my /home ... will that get affected by doing the above?

And finally, if my data drive won't get affected by the install method above, could I make a copy of my /home directory in it and just replace that copy once I've reinstalled?

Thanks in advance

G

You don't have to erase 10.10, It will be erased when you format & reinstall.
Your data partition will not be affected, neither will /home if it's in a separate prtn & you don't format it.
And finally :) I've heard that you can by many people, but I've never done it myself. However, if you data partition is NTFS I don't think it will work.

Thanks to mörgæs, there is some really good info about upgrading & reinstalling right here...
[[COLOR="Red"]I upgraded, and now I have this error... [/COLOR]]("http://ubuntuforums.org/showthread.php?t=1580857")

---

### Post by Dutch70 on 2011-04-28
> Originally Posted by 3rdalbum View Post
People, people, people; please get with the times

Since 2008, it's no longer been necessary to keep /home on a separate partition. If you install Ubuntu over the top of an earlier Ubuntu (WITHOUT formatting), it will preserve the contents of /home even if it's on the same partition as everything else.

That is good info, if we had some documentation to teach us about it. We could..."get with the times" :)
I can't find anything anywhere on it.

The downside is...If I had done that since 2008, I'd still be formatted to ext2 & actually, my /home prtn is ext2.

---

### Post by Rubi1200 on 2011-04-28
I just found something about it:

> Renewing the Installation **without formating** the  partitons (in contrast to upgrading), will also keep the personal data  and configurations under /home but will renew all system settings under  /etc as well as the default set of installed packages. [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

What I have not found yet, however, are precise instructions how to do this or more detailed documentation about how to do this safely.

---

### Post by Ken UK on 2011-04-28
I did the fresh install and loving it. Unity took some getting use to but I'm getting there. I did the separate /home partition and swap file manually and it seems to have worked as far as I can tell :D

---

### Post by Dutch70 on 2011-04-28
> **Ken UK said:**
> I did the fresh install and loving it. Unity took some getting use to but I'm getting there. I did the separate /home partition and **swap file** manually and it seems to have worked as far as I can tell :D

swap file???...or swap partition? 

Just curious, how big is your / parititon?

---

### Post by Ken UK on 2011-04-28
Sorry I mean a swap partition. I set it at 10gb which I know is crazy especially when I already have 2gb of ram but my new hard drive is 1tb and I know I will barely use a fraction of that :)
Set my home directory to 50gb, no idea how big its suppose to be.

---

### Post by Paqman on 2011-04-28
> **Ken UK said:**
> Sorry I mean a swap partition. I set it at 10gb which I know is crazy especially when I already have 2gb of ram but my new hard drive is 1tb and I know I will barely use a fraction of that :)

2GB of swap would have been plenty, but hey, you're not likely to notice the missing space.

> 
Set my home directory to 50gb, no idea how big its suppose to be.

Depends if you're storing data in it. If not, then 5GB is plenty. If you are storing data in it, make it as big as you need.

---

### Post by Dutch70 on 2011-04-28
Think our terminology is getting crossed. :P

Your home directory is your /home partition, if I'm saying that right.

"/" aka "root" is where the Ubuntu system lives & where you would reinstall, or install programs to. 
5GB will work, but is not recommended. 10-20GB is usually recommended & of course 30 should be enough for anyone...lol.

swap should be slightly larger than your physical RAM, or at least that would be sufficient. Doesn't hurt to make it larger if you have the extra space. You may want to add RAM one day.

---

### Post by wep940 on 2011-04-28
> **Rubi1200 said:**
> I just found something about it: 
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) 
What I have not found yet, however, are precise instructions how to do this or more detailed documentation about how to do this safely.
 
What I am hesitant about is:
 
Renewing the Installation **without formating** the partitons (in contrast to upgrading), will also keep the personal data and configurations under /home but will renew all system settings under /etc as well as the default set of installed packages
 
Nowhere in that part does it says it does a "clean" installation - removing ALL old libraries, etc., besides the DEFAULT set of installed packages.  This is what has always gotten people "in trouble" in the past.  This appears to me to be the same as the "upgrade" path that has always been there - maybe it's just that now that option is on the CD - so if you hose the upgrade you at least have a CD already burned you can do a fresh install from.
 
It's just me, I suppose, but this still sounds like the old upgrade - nothing on the link says anything about doing a "clean" upgrade, and the warnings are still there about 3 party packages, etc..  For me, I'll save some headaches and do the burn and install method.

---

### Post by 3rdalbum on 2011-04-28
> **Rubi1200 said:**
> This is very interesting. However, and wep940 also mentioned this, most of the experienced users here seem to suggest a separate /home partition. This is the first time, for me personally, that I have heard about what you are saying here. Moreover, have you tested this? Can you confirm that this is a method that we can recommend to new users? I suspect most new users would likely install and not even think about _not _formatting in the process, thus losing all their data.

Well, TBH, my /home is on a different hard disk. The Upgrade Install option in the installer does say that it preserves your /home. However, I've used the older Ubuntu installers on a computer with only one hard disk and only one partition, and they definitely preserved the /home. I was most surprised, the first time it happened.

---

### Post by Zanderist on 2011-04-28
If a fresh install is the best option why even bother having the choice to upgrade?

Doing a fresh install sounds like a pain.

---

### Post by Dutch70 on 2011-04-29
> **Zanderist said:**
> If a fresh install is the best option why even bother having the choice to upgrade?

Doing a fresh install sounds like a pain.

:lol:

A fresh install is just about as simple as it gets... 20-30 min. 
An upgrade is a royal pain... 2-15 hours, and unless you have a very basic system, 
it will probably fail &  you'll be doing a fresh install anyway.

Of course, some people will tell you that they've upgraded just fine. I've never been able to.

---

### Post by Ken UK on 2011-04-29
Well on other versions of Ubuntu I would have said fresh install is quick but this is the first Linux LiveCD I have tried (And I've tried alot) that has taken soooooooooo long to load and sooooooo long to install. Thats the only major negative thing I could say about it so far, plus when running from the LiveCD (before it took ages to download more updates) the behaviour was hit and miss at times.

I hope the LiveCD slowness is just me not alot of people or it will probably give a bad impression to new users...

---

### Post by Baldrick_NZ on 2011-04-29
> **Ken UK said:**
> Stay on 10.10 for acouple of months and then fresh install or you mean upgrade to 11.04 then wait?

Stay with 10.10 for now, and wait for 11.04 to become more stable. It'll take a couple of months to iron out the biggest bugs.

Or you could install 11.04 into a fresh partition and run it along side 10.10 as a dual boot. Once 11.04 has become more stable, remove 10.10 and reclaim hdd space for 11.04.

---

### Post by Ken UK on 2011-04-29
> **Baldrick_NZ said:**
> Stay with 10.10 for now, and wait for 11.04 to become more stable. It'll take a couple of months to iron out the biggest bugs.

Or you could install 11.04 into a fresh partition and run it along side 10.10 as a dual boot. Once 11.04 has become more stable, remove 10.10 and reclaim hdd space for 11.04.

The problem with that is unless you encounter any major problems you are lagging behind half a release just for stability problems. It makes it almost seem like that you are defeating the point of 6 month releases...

I'm just glad *fingers crossed* that 11.04 runs as good as if not better than 10.10 for me especially with having an old computer.

---

### Post by Rasa1111 on 2011-04-29
> **3rdalbum said:**
> Well, TBH, my /home is on a different hard disk. The Upgrade Install option in the installer does say that it preserves your /home. However, I've used the older Ubuntu installers on a computer with only one hard disk and only one partition, and they definitely preserved the /home. I was most surprised, the first time it happened.

but you still didn't tell us *how*..
Ive used many ubuntu cd's and don't recall that option being present. Not clearly anyway.. :???: :confused:

---

### Post by beew on 2011-04-29
> **Sal33m said:**
> An upgrade may take anywhere from 2 to 15 hours depending on your Internet speed. However, a fresh install will only take 30 minutes (excluding any tweeks after installation).

It takes only 15-20 minutes for a fresh install if you use a live usb instead of a CD. :)

---

### Post by Rubi1200 on 2011-04-29
> **Rasa1111 said:**
> but you still didn't tell us *how*..
Ive used many ubuntu cd's and don't recall that option being present. Not clearly anyway.. :???: :confused:
I have also never seen the option before.

I am also concerned about the language used in the wiki. It clearly says "renew...[COLOR=Red]in contrast[/COLOR] to upgrading." 

To be honest, this sounds more like some kind of system restore (sorry for the poor analogy) rather than an actual upgrade which preserves /home data and settings.

Is there some way we can ask Colin Watson, who wrote that page, to clarify this for us?

---

### Post by beew on 2011-04-29
> **Rasa1111 said:**
> but you still didn't tell us *how*..
Ive used many ubuntu cd's and don't recall that option being present. Not clearly anyway.. :???: :confused:

You mean to preserve /home? Basically you choose manual partition and choose the same /home partition without formatting it. I am not sure if that is what you're asking.

---

### Post by Rasa1111 on 2011-04-29
> **beew said:**
> You mean to preserve /home? Basically you choose manual partition and choose the same /home partition without formatting it. I am not sure if that is what you're asking.

ahh, that may just be what i'm asking! 
lol

Yeah, as 3rdalbum said..

"choose not to format" , but only reinstall "without formatting", and it will leave /home intact? 

 So I guess *i think?* you did answer the question!..
thanks man. :) <3

Ill have to play around and check it out i guess. lol

---

### Post by Rubi1200 on 2011-04-29
> **beew said:**
> You mean to preserve /home? Basically you choose manual partition and choose the same /home partition without formatting it. I am not sure if that is what you're asking.
No, I don't think this is what we are talking about at all. What 3rdalbum was saying, and the wiki seems to suggest, is that there is no need for a separate /home partition. 

In other words, you install normally using / for the partition, which includes /home. Then, when it comes time to, and this is where I am not sure what the wiki means, either reinstall/renew/upgrade you use manual partitioning and tell the installer not to format, thus preserving /home but renewing/upgrading the / partition.

This is what I understood from this. The problem is; where is there better documentation about this and how safe is it?

Most new, or even slightly more experienced, users are likely to go ahead and click Forward without thinking about what is about to happen.

---

### Post by beew on 2011-04-29
> **Rubi1200 said:**
> No, I don't think this is what we are talking about at all. What 3rdalbum was saying, and the wiki seems to suggest, is that there is no need for a separate /home partition. 

In other words, you install normally using / for the partition, which includes /home. Then, when it comes time to, and this is where I am not sure what the wiki means, either reinstall/renew/upgrade you use manual partitioning and tell the installer not to format, thus preserving /home but renewing/upgrading the / partition.

This is what I understood from this. The problem is; where is there better documentation about this and how safe is it?

Most new, or even slightly more experienced, users are likely to go ahead and click Forward without thinking about what is about to happen.

I don't know about that, I always keep a separate /home partition. It is a natural thing to do if you do manual partition. I always do manual partition because I multiboot with several Linuxes and it gives me more control like where to put grub.

---

### Post by Rasa1111 on 2011-04-29
Damn,
Now Rubi has made me doubtful again! :lol: 
[probably a good thing] lol

hmm...
I think Im going to have to read again on how to make a separate /home partition..

You guys have been telling me for the past 3-4 installs that I should do it..
 i just get confused when I get reading how.. :???: 

I need a "how to make separate /home partition for dummies" or something apparently.. 
any takers? lol
*hides face*

---

### Post by beew on 2011-04-29
> **Rasa1111 said:**
> Damn,
Now Rubi has made me doubtful again! :lol: 
[probably a good thing] lol

hmm...
I think Im going to have to read again on how to make a separate /home partition..

You guys have been telling me for the past 3-4 installs that I should do it..
 i just get confused when I get reading how.. :???: 

I need a "how to make separate /home partition for dummies" or something apparently.. 
any takers? lol
*hides face*

When you install, choose manual partition, then you will be offered the option to partition the hard drive (using the installer, or you can do it before install with gparted)

Make one partition as / and format to ext 4. Then make another ext4 partition and label it /home (and a third one as swap). If you have already a /home partition use the same one, and make sure you don't format it, if you don't have one already (say it is a freshly wiped hard drive) format your /home as ext 4. Then proceed as usual.

---

### Post by Rubi1200 on 2011-04-29
> **Rasa1111 said:**
> Damn,
Now Rubi has made me doubtful again! :lol: 
[probably a good thing] lol

hmm...
I think Im going to have to read again on how to make a separate /home partition..

You guys have been telling me for the past 3-4 installs that I should do it..
 i just get confused when I get reading how.. :???: 

I need a "how to make separate /home partition for dummies" or something apparently.. 
any takers? lol
*hides face*
Certainly didn't mean to confuse you, or anyone else. For the most part, the 3 partition method suggested by beew is the standard way of setting things up.

---

### Post by abnordude on 2011-04-29
Another vote for fresh install.
I tried the upgrading process.
Too slow.
I hate it.
I'm with fresh install.

---

### Post by Dutch70 on 2011-04-29
I think I'm in the perfect situation to give the "renew installation" thing a try. 

I've got Kubuntu Maverick on a  20GB partition in a multi boot system that uses a data prtn instead of a separate /home. So I don't have anything in my home directory that I care to lose, and I can add more files to it for the sake of the experiment. 

So, how do I renew the installation? 
Is that just a typical install without formatting? 

Well :( ....I don't see me doing this very soon. Right now it's taking me 3+ hours to get a 16MB update for FF4.

I already have Ku-Natty on a usb stick, because I got it on April 27th ;) but I'd still have to update it. 

I am going to give this a shot when things slow down some.

---

