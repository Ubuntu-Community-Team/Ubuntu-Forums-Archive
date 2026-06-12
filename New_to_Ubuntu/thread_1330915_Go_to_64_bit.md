---
title: "Go to 64 bit?"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by BobJam on 2009-11-18
I'm agonizing over whether to switch to 64 bit or stay with my 32 bit Ubuntu.

I read the thread [here]("http://ubuntuforums.org/showthread.php?t=368607"), and while it's relatively old (and the links lead to old threads), it nevertheless has some good pros and cons.

I never realized my Intel Pentium T4200 dual core supported 64 bit, or else I probably would have installed 64 bit to begin with and tried it.

But now I have all my settings and programs in the 32 bit Ubuntu I have installed.  So the reason I'm agonizing about making the switch now is my fear that installing the 64 bit will wipe out everything I have built for the past year and I'll have to start over.

So is there a way I can install the 64 bit version and then migrate my current settings and programs to it so that the only change I will have is 64 bit and all else will remain the same?  Or will installing the 64 bit version require that I start all over again?

My concern isn't so much about what the advantages and disadvantages of 64 versus 32 are (I can figure that out myself), but rather keeping my desktop, settings, and programs as they are.

I wouldn't be asking this question if I hadn't realized my processor supports 64 bit.  But now it's a question of having the capability (one poster made an anology of having a corvette but pulling out 4 sparkplugs) and not using it.  Am I pouring ketchup on Fillet Mignon, taking a ham sandwich to a banquet, wearing brown shoes with a tuxedo . . . and all those truisms?

Or, is this a case of "if it ain't broke, don't fix it."?  I mean, the way I have things set up right now, it works just fine with the 32 bit Ubuntu.  I'm satisfied with the way it is . . . which is another reason why I'm agonizing over this.

---

### Post by Cheesemill on 2009-11-18
How much RAM have you got?
If it's less than 4GB and likely to stay that way for the lifetime of your installation then there is probably not much point.

Changing to 64-bit requires a clean install but if you back up your /home directory and create a list of installed packages then getting your system back to how it is now isn't that much of a big deal.

---

### Post by BobJam on 2009-11-18
> **Cheesemill said:**
> How much RAM have you got?
If it's less than 4GB and likely to stay that way for the lifetime of your installation then there is probably not much point.I have exactly 4GB of RAM.

> **Cheesemill said:**
> Changing to 64-bit requires a clean install but if you back up your /home directory and create a list of installed packages then getting your system back to how it is now isn't that much of a big deal.I have a 250GB HDD, with about 130GB free.  Can I put the 64bit version on a partition there, and then have a dual boot system show up in Grub?  That way I can try the 64bit and still have the 32bit available.

If that's not possible, then I can do the backup (store it on removable media I assume) and make the list of my installed packages as you suggest.  But would it be worth all that effort?

Another question:  Since I would be making the /home backup from my 32 bit system, would I run into compatibility issues trying to restore it to a 64bit system?

---

### Post by Zoot7 on 2009-11-18
> **BobJam said:**
> Or, is this a case of "if it ain't broke, don't fix it."?  I mean, the way I have things set up right now, it works just fine with the 32 bit Ubuntu.  I'm satisfied with the way it is . . . which is another reason why I'm agonizing over this.
I would echo that. I've been on the fence about upgrading to 64bit now for some time, but I still just don't see a worthwhile reason to jump ship.

---

### Post by bodhi.zazen on 2009-11-18
If you have a 64 bit processor I advise you start with 64 bit Ubuntu.

I have been running 64 bit Linux, Ubuntu and otherwise, without any issue specific to 64 bit versions for over 2 years starting with Ubuntu 8.10.

If you wish to stay with 32 bit processors, starting with Ubuntu 9.10 I suggest you try the pae kernel, this will allow you to use up to 64 Gb RAM.

---

### Post by BobJam on 2009-11-18
> **Zoot7 said:**
> I would echo that. I've been on the fence about upgrading to 64bit now for some time, but I still just don't see a worthwhile reason to jump ship.

Yes, it would have to be a SIGNIFICANT improvement to entice me to change.  The number one reason I am agonizing over it is that my machine has the capability and I just don't want to waste it if it means significant improvement.

Of course, "significant" is a very subjective term.  "Significant" to me would be a clearly noticeable improvement over what I have currently.

I'm not a gamer, nor do I do CAD or any manipulations that require substantial numbers crunching, which as I understand it are the main advantages to 64 bit.

My uses are primarily email and surfing (Thunderbird and Firefox), and an occasional use of spreadsheets and word processing (OpenOffice), plus building a web site.  No real intense processor activities.

---

### Post by sandyd on 2009-11-18
you should read here to begin.
[http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)

---

### Post by sandyd on 2009-11-18
> **BobJam said:**
> Yes, it would have to be a SIGNIFICANT improvement to entice me to change.  The number one reason I am agonizing over it is that my machine has the capability and I just don't want to waste it if it means significant improvement.

Of course, "significant" is a very subjective term.  "Significant" to me would be a clearly noticeable improvement over what I have currently.

I'm not a gamer, nor do I do CAD or any manipulations that require substantial numbers crunching, which as I understand it are the main advantages to 64 bit.

My uses are primarily email and surfing (Thunderbird and Firefox), and an occasional use of spreadsheets and word processing (OpenOffice), plus building a web site.  No real intense processor activities.
64-bit offers improvements in what you can call "number crunching", which means that stuff like video conversion, extracting large files, and some other operations should be faster.

---

### Post by QIII on 2009-11-18
The industry is moving to 64 bit.

Do you need it, really?  Really?  Probably not.  Ubuntu (and most Linux distros) will continue to have 32 bit versions for years to come, because one of the things about Linux is its support for older machines.  But that is probably not written in stone for eternity.

But as more and more developers focus their efforts on using the greater power of 64 bit machine architecture and operating systems, eventually someone who doggedly sticks to 32 bit systems will be left behind.  Not forgotten, of course.  But it will be like having a Volkswagen Beetle when everyone else has Ford Mustangs.

That old '58 Beetle of mine got me around.

---

### Post by BobJam on 2009-11-18
> **bodhi.zazen said:**
> If you have a 64 bit processor I advise you start with 64 bit UbuntuCan't "start" with that . . . already have 32 bit installed . . . which is why I'm agonizing over the switch to begin with.  Read my original post.

Or by "start" do you mean "use"?

> **bodhi.zazen said:**
> I have been running 64 bit Linux, Ubuntu and otherwise, without any issue specific to 64 bit versions for over 2 years starting with Ubuntu 8.10.Yes, I have seen many people say things like that, and I also have seen many people say the opposite.

How it works on one machine is no guarantee that it will work good on another machine.  As I'm sure you know, it all depends on hardware, software, and system configs.  What works and plays well with one system may not on another system.

But I'm willing to take that risk if the risk/reward equation tilts to the reward side.  That's what I'm trying to figure out.  And see my previous post where I detail my predominant uses . . . that seems to be very pertinent to this issue.

All that said, I will try the switch if it makes sense.

> **bodhi.zazen said:**
> If you wish to stay with 32 bit processors, starting with Ubuntu 9.10 I suggest you try the pae kernel, this will allow you to use up to 64 Gb RAM.As I said in a previous post, I have exactly 4GB of RAM.

Perhaps I should have added that this is the max for my machine, and I don't anticipate getting another machine with more RAM for at least the next couple of years.  So, having the capability to access 64GB of RAM is not an enticement for me to use the pae kernel.

BTW, I have no idea what the "pae kernel" is anyway.  Are there any other advantages to using it on a 32 bit installation?

---

### Post by QIII on 2009-11-18
PAE is Physical Address Extension.  In layman's terms, it simply allows a 32 bit operating system to address more memory than it would otherwise be able to.

If you have only 4GB and are not upset by the memory hole or any memory lost to hardware that might reserve it (onboard graphics, for instance), then 32 bit PAE is pointless for you on your current machine.

There is no burning reason to switch to 64 bit if it isn't worth the trouble to you to reinstall.

But for the next machine, go with 64 bit.

---

### Post by bodhi.zazen on 2009-11-18
I suggest you install the 64 bit version of Ubuntu. You can easily revert if you do not like it.

With the standard 32 bit kernel you can use only 3.2 Gb or your 4 Gb of you RAM. The PAE kernel will allow you to use a full 4 Gb.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

[http://packages.ubuntu.com/karmic/linux-image-2.6.31-14-generic-pae](http://packages.ubuntu.com/karmic/linux-image-2.6.31-14-generic-pae)

Of course you may not need it, your computer needs may be relatively small.

For the vast majority of users for the vast majority of desktop tasks 64 bit is not significantly faster.

64 bit does of course have some security advantages =)

---

### Post by QIII on 2009-11-18
I would agree with you Bodhi, but for one thing:  It has to be worth the effort for the OP.

You and I have separate /home partitions, know how to preserve our settings/themes/installed apps, etc, and be up and running virtually immediately after a clean installation.

Personally, I'd go 64 bit in a heartbeat.  That's me.

I'm just not getting that vibe from the OP.

---

### Post by stoogiebuncho on 2009-11-18
You asked earlier if it's possible to dual-boot 32-bit and 64-bit ubuntu.  I believe it is.  That might be your best bet.  Give it a try without getting rid of your existing system and see if you notice a difference in performance.

---

### Post by 3rdalbum on 2009-11-18
Your settings (like your e-mail, Tomboy notes, Firefox bookmarks, Gnome desktop layout, program settings etc) are stored in hidden folders inside your home directory. When you install 64-bit, you can just put these into your new home directory and they will be used. Apart from the lack of programs, your new 64-bit system will feel exactly like your old system once all the settings are in place.

In fact, the Ubuntu installer will preserve the contents of your home directory if you just install Ubuntu "over the top" without reformatting. However I'd still highly recommend backing up your data to guard against user error or previously-unseen bugs in the installer :-)

Your programs will have to be re-downloaded, but the good news is that if you know what you've downloaded from the repositories, you can easily just get them again from Synaptic. There are a couple of HOWTOs that let you generate a script to tell Ubuntu to download every repository package that you already have - so generate it on your old 32-bit system, and run it on your new 64-bit system.

Anything you have manually compiled will need to be recompiled, but the source code you used to compile from can be recompiled on 64-bit without drama.

---

### Post by Spiritof76 on 2009-11-19
I guess I don't get it I run my systemwith 2 Gigs, I've never seen my Karmic system use more than 550 meg.  I run mail and browser full time watch an occassional movie etc.  As Inderstand it 64 bit code will run a little bit slower and code will always be a little bit bigger.  I use Linux to get away from inefficient systems that require vast resources. 

People are still running inmto problems with 64 bit flash and watching youtube with the 64 bit system.. I suppose there really are people that can use more than 3.5 gigs of memory. but I can't see why the average Ubuntu user would need it or want it.

---

### Post by Axos on 2009-11-19
> **bodhi.zazen said:**
> 64 bit does of course have some security advantages =)
There shouldn't be unless there is some kind of design flaw in the processor. Please explain. Thanks!

---

### Post by blackienl on 2009-11-19
Yes, please expand on the security bonus with 64 bit if you could.

From my experience with KK64 vs KK32,the KK64 version runs cooler on  my notebook. With the 32 bit version my fan was kicking in alot and the thing ran noticeably hotter. The 64 bit version rarely kicks the fans in high gear unless I'm running some HD video or something of the sort. I also do find the 64 bit version more responsive and generally faster, even with my simple 4g of ram.

---

### Post by egalvan on 2009-11-19
You state that  you have plenty of drive space.

so go ahead and dual-boot 32 and 64 bit Linux.

I did that with Hardy, just to experiment.

I set up three new partitions, and  named (LABEL) them thusly...

/64
/boot64
/home64

helped distinguish them.

---

### Post by 3rdalbum on 2009-11-20
People only run into problems with 64-bit Flash if they try to use the repository version (which isn't 64-bit anyway - it's the 32-bit version, haha). If you use the alpha 64-bit Flash Player from Adobe Labs, you don't have any problems.

64-bit Ubuntu does have extra security features that are present in all 64-bit processors but not in many 32-bit ones. I believe they have to do with preventing buffer overflow exploits and randomising library locations in memory. Karmic has introduced the ability for some of these protections to be emulated on 32-bit systems, but it's better to have this in place on the hardware.

64-bit Ubuntu uses a slight amount of more memory, but it doesn't run slower - it runs faster for certain operations.

---

### Post by lavinog on 2009-11-20
There are still some apps that are not available for 64bit systems...such as freeorion.

---

### Post by QIII on 2009-11-20
64 bit security...

[http://www.linuxtoday.com/developer/2009110600635SCRLUB](http://www.linuxtoday.com/developer/2009110600635SCRLUB)

---

### Post by BobJam on 2009-11-21
The consensus I'm getting is that FOR ME, sticking to 32 bit RIGHT NOW is probably the better option, though I may take egalvan's suggestion and try it on another partition.

I'm also understanding that 64 bit is "the wave of the future" and that sooner or later I'll have to step up to the plate.

I probably have the skills right now, because I have a seperate home partition, know how to back it up (and have), and know how also I think to back up my settings (as I understand it, that would be included in my /home backup anyway, because the settings are contained in all the dot files in the home directory . . . though I guess I might make a copy on removable media of all the dot files).

In any case, as you probably can see in that statement, I'm just not real confident yet.

That actually fits nicely for me, because I can wait and in that time become more confident of my "Ubuntu skills".  So when the time comes (in a couple of years?), I'll likely be ready to do it smoothly.

A post from the link that carlee gave me in post #7 of this thread:[INDENT] [I][COLOR=Blue]"64-bit version really makes sense only in a very few cases, actually in only one case: when you need to run a *single* application that needs more than 3 GB memory.
The catch is, that 64-bit applications also take more memory than 32-bit apps with the same data/code set (in the case of Java it's two times more - means 1gb 32bit app == 2gb 64bit app), so you may need to start with 8 GB ram for the 32 to 64 bit upgrade to make any sense."[/COLOR][/I][B][I][COLOR=Blue]
[/COLOR][/I][/B][/INDENT]That would seem to indicate that switching to 64bit doesn't make much sense for me RIGHT NOW since I don't have an app that goobles up/needs 3GB of memory.

QIII's advice makes sense to me.  The risk/reward equation for me RIGHT NOW doesn't seem to tilt heavily enough to the reward side, but I don't want to have "a Volkswagon Beetle" when everyone else "has Ford Mustangs", which is why I keep saying "RIGHT NOW".  For now, driving the 32 bit "gets me around".   As far as 64bit security goes, this thought prevails RIGHT NOW:[INDENT] *[COLOR=Blue]Between the extremes of caution and blissful ignorance, there is some comfort point, which will be different for everyone.  I choose to run some risks, if they entail compensatory advantages, while avoiding others.[/COLOR]*[B][I][COLOR=Blue]
[/COLOR][/I][/B][/INDENT]> **QIII said:**
> If you have only 4GB and are not upset by the memory hole or any memory lost to hardware that might reserve it (onboard graphics, for instance), then 32 bit PAE is pointless for you on your current machine.I have about 3.7GB available, so the loss of about 300K in RAM doesn't really bother me.  Would gaining that back with PAE or 64 bit really produce any noticeable improvement in performance considering my uses?

> **QIII said:**
> But for the next machine, go with 64 bit.This machine I'm currently using has the 64 bit capability.  So if I get another machine in a couple of years I'll be ready to run 64 bit.  Probably going to 'speriment with it on another partition right now anyway.

> **3rdalbum said:**
> There are a couple of HOWTOs that let you generate a script to tell Ubuntu to download every repository package that you already have - so generate it on your old 32-bit system, and run it on your new 64-bit system.Links for the HOWTO's?

> **egalvan said:**
> so go ahead and dual-boot 32 and 64 bit Linux.Links to any HOWTO's or tips for that?

---

### Post by gn2 on 2009-11-21
If you have 32-bit with a separate /home partition, you can install 64-bit, using the manual partitioning option to keep your /home intact and when your done all your settings from 32-bit will still be there for 64.

I've done this myself and it works a treat.

I do a bit of video encoding and the time taken to complete is significantly reduced with 64-bit.
Other than that there is no noticeable improvement.

---

### Post by Zoot7 on 2009-11-21
> **carlee said:**
> 64-bit offers improvements in what you can call "number crunching", which means that stuff like video conversion, extracting large files, and some other operations should be faster.
Number crunching is the big deal alright.
By using 64bit your Processor (assuming it's 64bit) is able to use it's ALU to it's full capacity, so simulations, encoding audio/video etc. should se a big jump.

But if your needs don't warrant such performance the regular ol' 32bit is a-okay for you.

---

### Post by stoogiebuncho on 2009-11-21
> 
Quote:
Originally Posted by 3rdalbum View Post
There are a couple of HOWTOs that let you generate a script to tell Ubuntu to download every repository package that you already have - so generate it on your old 32-bit system, and run it on your new 64-bit system.
Links for the HOWTO's?

Here's one:
[http://ubuntuforums.org/showthread.php?t=261366]("http://ubuntuforums.org/showthread.php?t=261366")

---

