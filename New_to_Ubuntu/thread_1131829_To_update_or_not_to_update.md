---
title: "To update or not to update"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by lukeinvancouver on 2009-04-21
I am at my sixth installation of Ubuntu 8.10 and I'm making progress. I also love Linux more and more as my knowledge about it increases.

6th installation? 

Why?

When things got stuck and some didn't work any more, given my very limited knowledge of Linux, it just seemed easier (or the only alternative at times) to start over again. However, as I continue to build the system it would become ever more "expensive" in terms of time to do so. Also more frustrating.

Most of the times when "things got stuck" it happened after updating. I'd have no more internet connection, for instance.

That problem got solved with the kind help of people here and if it happens again I'll be able to fix it myself.

However, it made me weary about updating. ("If it ain't broke, don't fix it" is an old saying though it doesn't really apply to the world of computers; I know.)

The last time I updated was a few days ago and everything is fine right now. Presently, it's offering me an update to fix daylight savings time in Palestine. I live in Canada, so I declined.

But I know I can't go on forever and not update and there will be some that are relevant to me. (Can I selectively choose which updates to download if there are more than one?)

So **the question is**: Can I go on (at least for the time being) and just enjoy the working system and spend my time learning more about Linux? For most of my computing I'm still dependent on Windows and I would like to change that.

**Or put another way**, how do I decide when to update or not?

Do you Linux pros install any and every update that becomes available?

Thanks in advance for your help.

---

### Post by Paddy Landau on 2009-04-21
I haven't had any of those problems that you describe, so I'm curious as to what's different.

However, that doesn't answer your question. I would suggest that you do as I do:

[LIST]
[*]Make a *complete* backup of your partition. I use [SysRescCD]("http://www.sysresccd.org/") to run [Partimage]("http://www.partimage.org/") to back up the partition.
[/LIST]
This means that if there's a screw-up, you can just restore the entire partition back to the date of your backup. That happened when I reinstalled Vista and (surprise, surprise) it deleted up the Ubuntu installation. As I'd had the sense to back up my Ubuntu installation beforehand, an hour later I had my working installation back and running!

I suggest that you get an external hard drive if you don't have one, and back up to there. It's much easier. Partimage backs up only the used space, and compresses the image on the fly, so you need less space than you might expect.

Run this backup overnight once a week, and you'll never be more than a week out of date. Back up your daily data daily, and you can restore nice and fast.

---

### Post by Celauran on 2009-04-21
> **lukeinvancouver said:**
> ("If it ain't broke, don't fix it" is an old saying though it doesn't really apply to the world of computers; I know.)

Perhaps a wee bit off topic here, but I think that absolutely does apply to computers. If it's a second machine you're just toying around with and it's not going to interfere with your productivity, then that's one thing. For machines that I rely on to get real work done, however, I tend to get it working and then leave well enough alone save for security updates. I don't necessarily need absolute bleeding edge latest-and-greatest version of everything. I value stability over all else. Something to think about, at any rate.

I can't comment specifically on your Intrepid woes as I am still using Hardy (there's that if it ain't broke don't fix it for ya :P) but I'd recommend creating a separate partition for /home and making regular backups. Getting the OS reinstalled isn't a big deal if that's what it comes down to.

---

### Post by Bios Element on 2009-04-21
> **lukeinvancouver said:**
> Do you Linux pros install any and every update that becomes available?

Thanks in advance for your help.

I'm hardly a "pro" but yes, I install any and every update that becomes available from alpha releases on to help test things and I have yet to run into a total show-stopping bug.

---

### Post by Sef on 2009-04-21
> However, it made me weary about updating. ("If it ain't broke, don't fix it" is an old saying though it doesn't really apply to the world of computers; I know.)

Updating to the newest version is not necessary, but it should be done once the security patches are no longer supplied.

---

### Post by duanedesign on 2009-04-21
Installing your /home directory on its own partition can make reinstallation a little less of a headache. With /home on its own directory you would only need to install the OS and format your / directory partition. This allows you to keep all your personal settings and files. This is easiest when doing a new install. however here is a how to for creating a seperate home partition on a already installed system:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You can do a selective update using the synaptic package manager (System>Administration>Synaptic Package Manager).
 
Click Mark All Upgrades. 

This will mark all the updates. Simply find the update you do not want to apply and uncheck it. This can be made a little easier by sorting the list by status. You do this by clicking the "S" at the far left, top of the package list. The boxes that are green are packages you have installed. The boxes that are green with a gold star are packages that have an update. Clicking the "S" will bring the installed packages to the top. Additionally clicking the "Package" header will sort the list alphabetically.

Now click Apply

---

### Post by riza hylviu on 2009-04-21
hi
if it works well continue using it, the first release of jaunty may have still some bugs that will be fixed in time. If you need a stable desktop, you have it, but if you want the newest stuff without caring of probable issues to come than install jaunty. hope i helped:D

---

### Post by lukeinvancouver on 2009-04-21
> **Paddy Landau said:**
> I haven't had any of those problems that you describe, so I'm curious as to what's different.

It was a problem related to the (cheap) Atom processor and somebody who had the same hardware (and the same problem, i.e. the system not connecting to the network after reboot following an update. It had no problem connecting when I started the install with the live CD.) was so kind as to give me (a Newbie if ever there was one!) detailed instructions in how to fix it (i.e. go back to a previous kernel and change the boot order in Grub). It has since been fixed and I did not need to jump through hoops after the last install.

Thanks for your instrucitons about a backup. To do it will have to wait until I have the money for an external HDD. I'm also not that keen on an external HDD as I had one die on me while writing massive files. causing me to lose all my backups. This was under Vista I think. (Could have been my Win 2000 machine though.) As so often happens, this was just a little while after the warranty had expired.

My question really is: Can I safely ignore some files to download and if so which.

I realise that "security updates" are probably a must.

Recommended updates can probably be ignored.

Palestinian daylight savings time I definitely don't need as I havew no intention of moving my desktop machine (or myself) to Palestine.

Is it OK or dangerous to ignore "security updates" for the time being, i.e. until my knowlege of this marvelous OS is better?

Which leads me to a related question (maybe I should start another thread about this?): Do I need a virus scanner? I've been under the impression that there are no Linux viruses but have lately seen advertisements for Linux virus scanners.

---

### Post by lukeinvancouver on 2009-04-21
> **Celauran said:**
>  If it's a second machine you're just toying around with and it's not going to interfere with your productivity

Thank you for the advice.

I'm 66 and retired. So productivity is not a problem. Frustration can be as I have never been a patient person.

:D

---

### Post by lukeinvancouver on 2009-04-21
> **Bios Element said:**
> I'm hardly a "pro" but yes, I install any and every update that becomes available from alpha releases on to help test things and I have yet to run into a total show-stopping bug.


Thank you kindly for your help.

---

### Post by lukeinvancouver on 2009-04-21
> **Sef said:**
> Updating to the newest version is not necessary, but it should be done once the security patches are no longer supplied.


I just installed this a couple of weeks ago and am under the impression that it is supported for 18 months, so I have lots of time for that.

I however infer (correctly?) from your post that I should definitely install security updates as they become available. I shall do so.


Thank you for your help.

---

### Post by philinux on 2009-04-21
In your case I'd do this.

System>admin>software sources.

Click the updates tab. Ubuntu updates> Just have the security updates ticked. This is a bit like having a Long term support version like 8.04, which is very stable with very few updates.

---

### Post by Paddy Landau on 2009-04-21
> **lukeinvancouver said:**
> Which leads me to a related question (maybe I should start another thread about this?): Do I need a virus scanner? I've been under the impression that there are no Linux viruses but have lately seen advertisements for Linux virus scanners.
There are dozens of threads about this. Just search. The short answer is, no, you don't need a virus scanner. Linux has security built in.

---

### Post by lukeinvancouver on 2009-04-21
> **duanedesign said:**
> Installing your /home directory on its own partition can make reinstallation a little less of a headache. With /home on its own directory you would only need to install the OS and format your / directory partition. This allows you to keep all your personal settings and files. This is easiest when doing a new install. however here is a how to for creating a seperate home partition on a already installed system:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)




Thank you very much. I will try this sometime in the future. Right now I'm struggling with all sorts of frustrating problems.

(Latest: My pannel moved to the side - as Windows used to do me ever once in a while - and I couldn't fix it. So foolishly I deleted it and for the time being I don't know how to do anything. I'm posting this with my Vista machine. Sorry for being off-topic here but Linux can be a confusing world for a beginner.)

---

### Post by enduser000 on 2009-04-21
Hello,
     I know what you mean about reinstalling.  Mine would work fine if I didn't constantly mess with it.  There are two things that make it really easy for me to reinstall:

Keeping my data on another "data" partition.  Both windows (if I ever boot into it ;D) and ubuntu can access this, and I don't wipe it when reinstalling either OS

[remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html"), this allows me to make a backup of my system.  I usually choose 'distribution' so I can share an updated system with my friends.

So I reinstall, have my old data (and maybe 3 or so files I had to save for class) and need to install a graphics driver, then I install a couple of programs and I'm golden.  Awesome software, hope it works for you,

enduser000

---

### Post by lukeinvancouver on 2009-04-21
> **riza hylviu said:**
> hi
if you want the newest stuff without caring of probable issues to come than install jaunty. hope i helped:D

You did, or at least tried to as I don't even know what jaunty is.

Sorry.

Thank you very much.

---

### Post by lukeinvancouver on 2009-04-21
> **philinux said:**
> In your case I'd do this.

System>admin>software sources.

Click the updates tab. Ubuntu updates> Just have the security updates ticked. This is a bit like having a Long term support version like 8.04, which is very stable with very few updates.


Thank you kindly for your help.

---

### Post by lukeinvancouver on 2009-04-21
> **Paddy Landau said:**
> There are dozens of threads about this. Just search. The short answer is, no, you don't need a virus scanner. Linux has security built in.


Thank you very much for your help.

---

### Post by lukeinvancouver on 2009-04-21
> **enduser000 said:**
> 
Keeping my data on another "data" partition.  Both windows (if I ever boot into it ;D) and ubuntu can access this, and I don't wipe it when reinstalling either OS

[remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html"), this allows me to make a backup of my system. Awesome software, hope it works for you,

enduser000

"Keeping my data on another "data" partition."

That sounds great. 

Maybe I should start once more from scratch. 

Even though it's probably possible to create another partition without starting over again and move the data to I already have on the disk to that partition. The question is, am I capable of doing it without too much frustration or would it be easier to just start once more from scratch.

Right now I can't do anything, not even shut down.

:(

Thank you very much for your help.

:D

---

### Post by lukeinvancouver on 2009-04-21
Thank you all very, very much for you generous help!

I think one of my problems just got solved.

Grazie

---

### Post by carml on 2009-04-21
@ lukeinvancouver 
"Jaunty" = short for "Jaunty Jackalope" is the codename of the next release of Ubuntu,the 9.04 which should e available in a few days.
Just to make you know,often every release is referred only by his first codename word.;)

---

### Post by philinux on 2009-04-21
[http://ubuntuforums.org/showthread.php?t=971232](http://ubuntuforums.org/showthread.php?t=971232)

Thursday is the day.

I've been running it since alpha1.

---

### Post by lukeinvancouver on 2009-04-21
> **enduser000 said:**
>   Awesome software
enduser000

It sure is!

Over the last 2 or 3 years I've tried several distros (eg Mandriva, Fedora, Dynegy) and always gave up in frustration.

Ubuntu is soooo awsome, I think this time I'm going to succeed to eventually get away from Windows.

It really feels great.

---

### Post by lukeinvancouver on 2009-04-21
> **carml said:**
> @ lukeinvancouver 
"Jaunty" = short for "Jaunty Jackalope" is the codename of the next release of Ubuntu,the 9.04 which should e available in a few days.
Just to make you know,often every release is referred only by his first codename word.;)


Thanks for telling me but for the time being I'm going to stick to this version.

When I'll be much better with Linux I'll experiment more. For the time being my dream is to just end up with a really nice Linux system.

I think I'm well on the way thanks to all those people who share their time and experience.

I'm no programmer but I will find some way to contribute, perhaps helping with translations.

---

### Post by lukeinvancouver on 2009-04-21
> **philinux said:**
> [http://ubuntuforums.org/showthread.php?t=971232](http://ubuntuforums.org/showthread.php?t=971232)

Thursday is the day.

I've been running it since alpha1.

Thanks but as I said in the other post I'll do a lot more learning before jumping to another version.

---

### Post by jmszr on 2009-04-21
lukeinvancouver,

To take care of your panel problem: right click on your remaining panel, click on New panel - when it comes up (on the right side on my install) right click on the new panel and then click on Properties. Under General > Orientation select position (top I am assuming) and then to refill it right click on the new panel and then click on Add to panel - select relevant item(s) and click Add - arrange as you see fit.

---

### Post by juancarlospaco on 2009-04-21
Use **Back In Time** is just like a OSX's Time Machine, it can backup data and configurations.

**Block Version of Packages on synaptics "Package" Menu**

---

### Post by lukeinvancouver on 2009-04-21
> **jmszr said:**
> lukeinvancouver,

To take care of your panel problem: right click on your remaining panel,....

Thank you so much for helping with this but I got it worked out with the help files.

Cheers

:D

---

### Post by ugriffin on 2009-04-21
I always update. And, besides, Ubuntu, by default, only notifies you about the updates, so you can ignore the popup. 

Synaptic gives you a list of updates to be applied. I run kubuntu, but I think right clicking on it should give you an option to remove the update option. Play with Synaptic Updater's update list and see what happens. 

Besides, you can always disable updates. Linux is secure enough.

---

### Post by thraxsa on 2009-04-21
Updating I think is always a good move - updating helps patch security issue/bug fixes ... why would you not want to update ????

---

### Post by qwertyuiop96 on 2009-04-21
Go ahead and update- when the final release comes out in 2 days.  I updated, and unlike Windows, it keeps all your settings and files- nothing got messed up for me!  Worked great- and I LOVE KDE 4.2!

---

### Post by Sef on 2009-04-21
>  Besides, you can always disable updates. Linux is secure enough.

GNU/Linux is more secure than Windows, but it still can be attacked.   Linux botnets do exist.  If you fail to patch, then your machine could be taken over through a hole in Linux that has been fixed but not applied.

---

### Post by lukeinvancouver on 2009-04-21
> **juancarlospaco said:**
> Use **Back In Time** is just like a OSX's Time Machine, it can backup data and configurations.

**Block Version of Packages on synaptics "Package" Menu**

Thanks but a search doesn't turn up anything and I have no idea where this could be.

Is this a command to be used in Terminal?

If so my knowledge of command line input is next to non-existant at this point.

Thanks for trying to help me.

I was never rich enough to have a Mac and have not even used one. I started in the wonderful Microsoft universe (sarcasm) with DOS 2.4 and made it all the way to Vista. Can't wait to get away completely, though this is wishful thinking as some applications I use will only work in Windows.

---

### Post by lukeinvancouver on 2009-04-21
> **qwertyuiop96 said:**
> Go ahead and update- when the final release comes out in 2 days.  I updated, and unlike Windows, it keeps all your settings and files- nothing got messed up for me!  Worked great- and I LOVE KDE 4.2!

Well as I said, it couldn't connect to the net anymore after the initial update following the install. It was not the connection as the live CD would connect but a problem related to the Atom unit. It has since been fixed.


Got to go now: Hockey Night in Canada and the Canucks might - just might - win the Stanley Cup today. We only need to win one more game.

Thanks again.

Will be back after the game

---

### Post by lukeinvancouver on 2009-04-22
I guess the lack of sleep over the last 4 nights got to me: This was only the first round of the Stanley Cup and the Canucks have a long way to go (for all you may care).

Sorry for being off-topic but I just wanted to correct the wrong statement in the previous post.

:confused:

---

### Post by Paddy Landau on 2009-04-22
> **lukeinvancouver said:**
> ... some applications I use will only work in Windows.
Have you experimented with Wine?

Specifically, I strongly recommend that you load [PlayOnLinux]("http://www.playonlinux.com/"), as helps you install and uninstall Windows programs in Wine, and furthermore keeps those programs in separate areas (so that they don't interfere with each other).

Not all Windows programs will work under Wine, but many do.

Wine should be already installed on your system. To install PlayOnLinux through Synaptic Manager, add this to your software sources (System -> Administration -> Software Sources):
```
http://deb.mulx.net/ <os> main
```Replace "<os>" with your system, i.e. "hardy", "intrepid" or whatever.

---

### Post by lukeinvancouver on 2009-04-22
> **Paddy Landau said:**
> Have you experimented with Wine?



My Ubuntu machine has no Windows on it. So I guess Wine does not apply to my situation. Is this correct?

If I access Photoshop files on my other machine would Wine be able to handle them? I believe it can't. 

I know about GIMP but haven't had the chance yet to explore it and learn how to use it. I know also it can't handle Photoshop files but switching to GIMP in the future would be an alternative for new files, wouldn't it?

I have Vista on my latest machine and I really had resolved before buying it last August that my next machine would be powered by Linux. (I had made several attempts to get going with Linux using some older machines before but gave up in frustration with every distro I tried. Now I know, I'll make it with Ubuntu. It's the most beautiful distro I've tried my luck with.) 

It was because I got involved in trading (losing money would be more accurate but the intention was making some money) online and my old workhorse (and the nicest system I've had up to that date) a 2.4 gig P4 running Win 2000 (because I didn't like XP) was not suitable for the trading platform I'm using. I looked at buying the Vista machine (a not very expensive "back to school special") as an investment. Some investment (losses) it turned out to be!

Since I'm not rich I bought the Intel Atom system for $300.- for Ubuntu. It's actually not that bad and I understand that Linux doesn't hog resources like Windows does.

As frustrating as it can be to learn how to use another OS it's also a lot of fun and I love the spirit of co-operation in this community and will also contribute eventually. I just put together a Ubuntu system on an old clunker to give to an aquaintance tomorrow, who is making his first steps into the world of computing. I'll explore the possibility of helping with translations for Ubuntu when my system is up and running. (I'm fluent in three languages and have done some translations in the past but translating "computerese" will be a new experience.)


Thank you very much Paddy.

---

### Post by carml on 2009-04-22
Wine is meant to run under Linux software created for Windows,whether there's Windows on the machine or not.
Sometimes you can also launch using Wine any software installed under Windows onto the same machine.
I hope I nailed your question :).

---

### Post by egalvan on 2009-04-22
> **philinux said:**
> In your case I'd do this.

System>admin>software sources.

Click the updates tab. Ubuntu updates>[COLOR="Red"] Just have the security updates ticked. This is a bit like having a Long term support version like 8.04, which is very stable with very few updates[/COLOR].

+1 for this.

This is how I have my main work machine set up...

8.04 LTS with only security updates...

No problems, going on a year.

---

### Post by egalvan on 2009-04-22
> **lukeinvancouver said:**
> 
 I got involved in trading online and my old workhorse () **a 2.4 gig P4  was not suitable for the trading platform I'm using.**

Thank you very much Paddy.

OK, I find it hard to believe that a P4 @ 2.4GHz can't handle a "trading platform".

Perhaps if it's a Celeron with 128MB of RAM?

My main work machines (as of this morning) are Pentium 4 machines.
Northwood and Prescott cores, the slowest @ 1.4GHz, the fastest @ 2.8GHz.
With at least 512k cache, one @ 2Meg cache.

No Celerons here, I chunked those as soon as eBay came through with cheap full P4's.

But all my machines are maxed out on RAM..
most have 4GB, two have 8GB. (NewEgg Christmas specials! woohoo!)

I have found that this is the main problem with many "inadequate" computers....
insufficient RAM.

I liked Win2K more than XP, but found XP was better once it was optimized.
As for speeding up XP, the most important tip is

TURN OFF THE EYE CANDY!

Next, eliminate what is not needed. 
LitePC does wonders here.

Lots more XP tips out there.

Sorry for running on like this...

I get upset when I hear folks say
"I need a new machine, my old one is only 3GHz" !!!

To make myself feel better, I volunteer to "dispose" of their "obsolete" computer... no charge :)

ErnestG

---

### Post by lukeinvancouver on 2009-04-22
> **carml said:**
> Wine is meant to run under Linux software created for Windows,whether there's Windows on the machine or not.
Sometimes you can also launch using Wine any software installed under Windows onto the same machine.
I hope I nailed your question :).


Just to make sure I really understood (sorry, I am an absolute beginner after all): I use Wine to open Windows files on a Linux platform?

If that is so, this is great.

Would it be able to open and manipulate a PageMaker file, for instance?

Just a simple yes would do. 

Thank you for your help.

:)

---

### Post by lukeinvancouver on 2009-04-22
> **egalvan said:**
> OK, I find it hard to believe that a P4 @ 2.4GHz can't handle a "trading platform". ....

ErnestG

I live on Old Age security, which is very little and you can believe me that I would not have spent $ 900.- on the Vista machine if my P4 had been capable of doing the job. It has 4 gigs of RAM, four hard drives with plenty of free space. Maybe the trading platform didn't work because of Win 2000 but I wasn't going to get into installing another OS and pay MS $ 150.- for XP.  

I also still use the P4 for recording from TV or VHS tapes and my WinFast PVR works like a charm. I was thinking of maybe putting it into my Ubuntu machine but couldn't find a driver for Linux anywhere. In a way I don't really want to rip the capture card out of the P4 and then discover that I can't make it work with Ubuntu. Same with my Epson scanner: It works fine with Win 2000 but the output with Ubuntu was totally useless. Maybe there is a solution for that but at the moment I've got lots of other things to set up. Besides, when I'll have managed to connect to the P4 from my Ubuntu machine I can just copy the output from there.

I know the difference between a Celeron and a P4. My first Windows machine was a Celeron 300A which I built myself in 1998. Btw that's the one I'm setting up for the acquaintance I mentioned above to get started with computing. He's got NO experience whatsoever and it performs kind of OK. It's slow on the net but he doesn't have an internet connection anyway. (I was surprised  that it manages reasonably well to connect to internet radio stations.) To learn how to use Open Office, or for that matter basic commands, it's an OK machine and that's what the guy needs to start. The games work remarkably well for such an old clunker. I'm giving it to him and if he likes to use computers (he too is not very well off financially) then he could perhaps go for the cheapie I use for my Ubuntu platform: An Intel Atom for $ 300.- For the price it's not that bad.

Thank you for the tip about XP. I am about to help another friend reinstall XP on her totally run down machine. She picked up a lot of nasties downloading Hollywood films and pretty well nothing works anymore. I got her a Ubuntu disk and tried to convince her to switch but she doesn't feel up to it.

I have NO desire to build yet another Windows platform. (I even still have a Win 98 machine - as much as I've hated that version - because of some amazing audio software that was bundled with my Soundblaster Value Plus (for $ 65.-!), which won't work with anything else.

Microsoft products have never stopped me from getting enraged with the sloppy work of this outfit and Vista is no exception. For instance, it rearanges my many desktop shortcuts ever once in a while for no apparent reason. I got tons of them and hate wasting my time looking all over the desktop for the library shortcut, for instance. I had the dubious pleasue of starting with DOS 2.4 and I feel Bill Gates owes me money for the suffering he inflicted on me. (Not just a refund. :) ) If you are old enough to have used DOS 3.1 (or was it 3.3?) you will remember that it was a total failure (I bought it bundled with my Amstrad "luggable") and it was unceremoniously replaced about 3 months after its release.

Nough said about MS.

Thanks for helping me.

---

### Post by Paddy Landau on 2009-04-23
> **carml said:**
> Sometimes you can also launch using Wine any software installed under Windows onto the same machine.
This I didn't know! Thanks for the tip; I've experimented and indeed it works for me.

---

### Post by Paddy Landau on 2009-04-23
> **lukeinvancouver said:**
> My Ubuntu machine has no Windows on it. So I guess Wine does not apply to my situation. Is this correct?
No, incorrect. Wine stands for _WIN_dows _E_mulator, and it comes standard with Ubuntu. Wine isn't perfect, but it can run many Windows programs. You install your Windows program using Wine. As I said before, I strongly recommend that you install PlayOnLinux first, and install your Windows programs through PlayOnLinux; this makes it easy to install, and even easier to uninstall (unlike Windows!).

As carml says, you can also run (some) programs directly from your Windows partition.

> **lukeinvancouver said:**
> If I access Photoshop files on my other machine would Wine be able to handle them? I believe it can't.
I don't know if you can install Photoshop under Wine, or if you can run it from your Windows partition. Why don't you try?

> **lukeinvancouver said:**
> I know about GIMP but haven't had the chance yet to explore it and learn how to use it. I know also it can't handle Photoshop files but switching to GIMP in the future would be an alternative for new files, wouldn't it?
I would recommend that you learn GIMP. It has a steep learning curve, but heck, it's a quality product, it's free, and you can get plug-ins that extend its functionality. It also runs under Linux, Windows and Mac.

> **lukeinvancouver said:**
> I looked at buying the Vista machine (a not very expensive "back to school special") as an investment. Some investment (losses) it turned out to be!
Have you considered running Ubuntu on your Windows machine? You'll find it lightning fast. You can split your hard drive into two, which means that you still get to keep Windows. Each time that you turn on the machine, you choose whether to load Windows or Ubuntu.

> **lukeinvancouver said:**
> I love the spirit of co-operation in this community...
Me too. The community on this site is one of the warmest and most helpful I've ever come across. I'm proud to contribute in my own small way.

---

### Post by Paddy Landau on 2009-04-23
> **lukeinvancouver said:**
> Microsoft products have never stopped me from getting enraged with the sloppy work of this outfit and Vista is no exception. ... I had the dubious pleasue of starting with DOS 2.4 and I feel Bill Gates owes me money for the suffering he inflicted on me. (Not just a refund. :) ) If you are old enough to have used DOS 3.1 (or was it 3.3?) you will remember that it was a total failure (I bought it bundled with my Amstrad "luggable") and it was unceremoniously replaced about 3 months after its release.
:D - I often feel that Microsoft single-handedly held back the development of computers by several years (all that time, money and talent wasted on making antivirus products and coping with Windows-related problems). Mind you, with the current rash of malware taking control of government PCs throughout the world, I could feel that Microsoft has single-handedly reduced world security. Not a bad legacy, Mr Gates!

---

### Post by tom56 on 2009-04-23
> **Paddy Landau said:**
> No, incorrect. Wine stands for _WIN_dows _E_mulator

No it doesn't. It stands for **W**ine **I**s **N**ot an **E**mulator.

---

### Post by Linux_Kid66 on 2009-04-23
I like ubuntu so i update every time.

---

### Post by lukeinvancouver on 2009-04-23
> **Paddy Landau said:**
> ... Wine isn't perfect, but it can run many Windows programs. ...

Why don't you try? ...

I would recommend that you learn GIMP. It has a steep learning curve, but heck ... It also runs under Linux, Windows and Mac. ...

Have you considered running Ubuntu on your Windows machine?...

... I'm proud to contribute in my own small way.

First of all: Thank you Paddy for your generous help and the many interesting suggestions.

I will follow up on all of them but at the moment I'm still very much at the beginning of building my new system. Ooops, I should have said 'two', which sounds crazy but isn't really IMO.

I am working on my Atom machine as well as on an old clunker for an acquaintance who has never had a computer. I'm installing Ubuntu on both of them and that's why I don't think it's crazy  what I'm doing. I am getting to know Linux better and repetition will help my aging memory. (Without going into the details - I will start another thread about it - I get different problems with the old machine v.s. the new one.)

I believe you that GIMP has a steep learning curve, so has Photoshop (and I'm not that good with it). They are powerful programs, so it takes time to be able to work with them. *Learning how to use GIMP is way down the line for me*, i.e. after I finished setting up this system.

I also want to try PageMaker sometime in the future. I did a number of projects with it and know it much better than Photoshop. I hope it'll work.

I hadn't known that GIMP also runs under Windows. But then again, I'm trying to get away from Windows as much as possible.

[I]The same goes for using WINE. I mean, it is way down the line for me, i.e. after I finished setting up this system.
[/I]

But please make no mistake: Your effort is not wasted as I'm keeping the links to the threads I started not only for my future reference but possibly also to help others with the same problem. (That's what happened with the person who helped me with the connection problem I had: He has the same machine, had the same problem and managed to solve it and then helped me when he noticed what hardware I am dealing with.)

I'd rather not run Ubuntu on the Vista machine ( I also got a Win 2000 machine and - don't be shocked - a Win 98 machine because of some neat audio software that won't run on anything else.)

As much of a waste of time it really is to compete with machines in the FOREX market I somehow can't get away from it totally. It's addictive. I have my gambling under control (having lost a bundle helps in that respect somehow) and I don't really think I can get my money back. But there are moments (e.g. Bernanke announcing that he is going to flood the market with greenbacks) where it is possible to make a bit without too much risk. I'm not some kind of capitalist but a senior with a very small OAS income a month; so trying to make a little money is perhaps not so objectionable. Stupid or arrogant maybe because of the implied belief I can beat the machines. Perhaps as much as 75 % of FOREX trading is done by automated systems owned by banks and other sharks wanting the money of the small guy: witness the proliferation of these direct trading platforms. I digressed but it was for a reason, i.e. that I'd rather not install another OS on the Vista machine. There are enough problems with these, e.g. the program crashing while one has an open position. (Losses can and do happen at lightening speed.) Please excuse the long digression, I'm naturally longwinded and just wanted to explain why I don't want to take up this particular suggestion.

"I'm proud to contribute in my own small way."

You have every reason to be proud and I wouldn't call it "in a small way."

Thank you so much for your generosity.

---

### Post by Paddy Landau on 2009-04-23
> **tom56 said:**
> No it doesn't. It stands for **W**ine **I**s **N**ot an **E**mulator.
:redface: - Thanks for the correction! I've been reading up on it.

It makes sense, because an emulator would be unreasonably slow, whereas an API interface (as WINE is) leaves my Windows programs running faster on Linux than they do under the native Windows (on the same machine).

---

### Post by lukeinvancouver on 2009-04-23
> **Paddy Landau said:**
>  Not a bad legacy, Mr Gates!

At least he's now giving away much of his money (perhaps because of Melinda?) some - but not necessarily all (as a lot of the funds go to rich research foundations in the West rather than being spent in Africa or other needy places)- of it to where it should go IMO.

---

### Post by lukeinvancouver on 2009-04-23
> **Paddy Landau said:**
> ... Windows programs running faster on Linux than they do under the native Windows (on the same machine).

I find that astounding!

---

### Post by Paddy Landau on 2009-04-23
> **lukeinvancouver said:**
> [quote=Paddy Landau;7125352]...Windows programs running faster on Linux than they do under the native Windows (on the same machine).I find that astounding![/quote]
Well, not once you think about it.

Windows needs four times the resources to run as Ubuntu does.

And that's without the anti-virus and anti-malware that has to run in the background.

---

