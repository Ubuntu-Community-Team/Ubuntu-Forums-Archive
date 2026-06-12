---
title: "Backups!.."
date: 2009-02-06
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-02-06
It seems Backups is the numero-uno thing to learn about Ubuntu, when you're a novice...  You are gonna destroy the OS in a day, by messin' in it like you did in windows...  

Thing is..  Do you want to have to go through that whole install and downloads again, just cuz you click-killed something you shouldn't have..?  Almost every novice does...  

Why not have a backup, that can quickly correct the destruction you do to the Ubuntu OS, before you start biopsying & autopsying it..?


I stumbled upon this informative thread... 

[http://ubuntuforums.org/showthread.php?t=1054777&highlight=backup](http://ubuntuforums.org/showthread.php?t=1054777&highlight=backup)

Learning this is gonna be my priority one.. Only then will I attack the OS with gusto, like a 4-year old kid taking apart daddy's alarm-clock...

I wants to know all there is to know about making and running backups in Ubuntu...  Five reinstalls in two weeks is a bit much...

---

### Post by callan79 on 2009-02-06
> **DonaldJ said:**
> Thing is..  Do you want to have to go through that whole install and downloads again, just cuz you click-killed something you shouldn't have..?  Almost every novice does...
I wants to know all there is to know about making and running backups in Ubuntu...  Five reinstalls in two weeks is a bit much...



5 re-installs in two weeks?

And "cuz you click-killed something you shouldn't have..?"

Exactly what _are_ you clicking, that perhaps you should not?

I've got 30 months experience under my belt, but back in 6.06 I was a novice too. Sure, I made a few mistakes, but I can't say that I ever really managed to kill the system completely.

As for the answer to your question - Ubuntu 8.10 takes 40 minutes to re-install from CDROM. It's take you far longer to restore from backups.

BUT - if you are messing with config files, make a backup of that file before you play with it :

```
sudo cp filename filename.backup
```

Then if you mess things up :

```
sudo rm filename
sudo mv filename.backup filename
```


Either way, I'd be interested to hear what you're up to .... I'm curious :)

Cheers
Callan

---

### Post by hyper_ch on 2009-02-06
backups are essential... you never know what happens... your harddisk may fail...

---

### Post by DonaldJ on 2009-02-06
> **callan79 said:**
> 5 re-installs in two weeks?

And "cuz you click-killed something you shouldn't have..?"

Exactly what _are_ you clicking, that perhaps you should not?

I've got 30 months experience under my belt, but back in 6.06 I was a novice too. Sure, I made a few mistakes, but I can't say that I ever really managed to kill the system completely.

As for the answer to your question - Ubuntu 8.10 takes 40 minutes to re-install from CDROM. It's take you far longer to restore from backups.

BUT - if you are messing with config files, make a backup of that file before you play with it :

```
sudo cp filename filename.backup
```

Then if you mess things up :

```
sudo rm filename
sudo mv filename.backup filename
```


Either way, I'd be interested to hear what you're up to .... I'm curious :)

Cheers
Callan


I uninstalled games, and it seemed to damage the OS a tiny bit...

And I suspect that the OS got hit by someone in the know once, whom I upset a little...  Someone who needed a little vengeance to feel content...

When I say "killed a system", I mean I can't fix the bit of damage I did, or that got done from an outside source...

I ran three cleaners, and some of the OS got damaged...  I didn't know what to do, so I reinstalled...

I installed PhotoPlus-8 with Wine, and I just couldn't get rid of it...

I did a test by trying to install WinWall...  It made a huge mess, so I reinstalled...

The last install took about "40-minutes", but the update took about 7-hours this time...  Probably there was a lot of activity at the downloads site today, and on the cable system that I'm connected to..?

I just want to clear out all the stuff I know I'll never use.. Games for one...  If I never see another video game it will be fine with me...  I used to repair coin-op pinball and video games.. I had my fill...

 I  noticed after I killed games, that the OS ran a little faster, but then I added a bunch of softwares I though I might like to test, and ran a few cleaners, and suddenly the OS was full of weird glitches...  I figured it would be easier to just dump the big mess I made by doing a new install...

Once I got the OS like I like It, I'm gonna do an image DVD, so when I mess it up, I just pops-in the CD, and applies the image.. I hope...  How long would that take?..

---

### Post by ajgreeny on 2009-02-06
I make sure I have a backup of my /home, but don't worry about a system backup as it is so quick to reinstall if everything goes belly up.  The one extra thing I do is run aptoncd every so often, and make an iso file (in my /home) of all the updates I have added and packages I have installed with apt.  Then if I need to reinstall ever, I have a downloaded package for everything and can just get back to the same state without all the download palaver and time wasted.  I just keep the most up to date iso file and get rid of the old ones.

---

### Post by cartisdm on 2009-02-06
I understand what he means.  Yes, ubuntu can be reinstalled quickly (I've had to do it a number of times) but that's only the first step.  All your settings and configurations have to be reinstalled - and not to mention running all the updates.  If I was smart I'd look into creating an image of my OS once I get it how I like.

Actually, I'd like to do the same thing for Firefox now that I think about it.  I can NEVER remember what plugins and themes I've downloaded.  After a reinstall I have to search through everything again!

---

### Post by hyper_ch on 2009-02-06
updates and configs are restored quickly...

---

### Post by newbee70 on 2009-02-06
> **DonaldJ said:**
> I uninstalled games, and it seemed to damage the OS a tiny bit...

  I figured it would be easier to just dump the big mess I made by doing a new install...

Once I got the OS like I like It, I'm gonna do an image DVD, so when I mess it up, I just pops-in the CD, and applies the image.. I hope...  How long would that take?..

Hey, I hear ya: I crash my install often: not because of Ubuntu's failure but my constant playing and learning Ubuntu "Linux", and not being able or know enough yet to do a full recovery without a clean install. Eventually I will be able to; but until then I use Remastersys and have an up to-date copy of my whole system: load time from scratch is about 18 to 30 minutes without having to update anything afterwards. do a google on remastersys, and try it.

and above all have fun learning the operating system.

---

### Post by DonaldJ on 2009-02-06
Great!..  Thanks!..  That's what I need...

__________________


"Solved" isn't totally complete when there still might be new stuff happening in this area, that does the same job, maybe even better...  Let's keep it open for now, even if it is solved by your expert advice, which is definitely what I'm gonna try.. is what I've looking for...  It's the reason I was pushed into switching to Linux in the first place...  I tried and tried to get a way to make the same for W2000, given that the bully-gorillas were slamming my PC a couple times a month, and they would crash posts while I keyed them, even in freshly installed OS's...  For Windows image CD, I found I would need to spend a couple hundred bucks to get it to work..  All I got was a runaround with Windows, and crap and grief, and hit and hit and hit...  If you ever tried to find free windows hardware drivers, you know the stretch, the runaround, and the grief...  

The mindless-gorillas literally shoved me Out of Windows... And I "flushed Windows down the toilet"... Now all my Windows CD's are in a bag in the shed, on the shelf Under the weed killers, the fertilizers, and the bag of sheep manure...  It should be in the sheep manure bag, but I'm saving them just in case someone's PC needs a fix with them...

---

### Post by jerome1232 on 2009-02-06
I think your just resorting to a reinstall as a quick fix to often, I mean seriously wine? You just nuke your .wine directory and all wine troubles are solved.

That being said rsync is a great backup tool [http://www.cyberciti.biz/tips/linux-use-rsync-transfer-mirror-files-directories.html](http://www.cyberciti.biz/tips/linux-use-rsync-transfer-mirror-files-directories.html)

I think imaging your drive is a good way to make a backup that can just be dropped back in place.
[apt:partimage]("apt:partimage")
dd and partimage are good programs to create images of your drive.

---

### Post by Dumbestcrayon on 2009-02-06
> **DonaldJ said:**
> It seems Backups is the numero-uno thing to learn about Ubuntu, when you're a novice...  You are gonna destroy the OS in a day, by messin' in it like you did in windows...  

Thing is..  Do you want to have to go through that whole install and downloads again, just cuz you click-killed something you shouldn't have..?  Almost every novice does...  

Why not have a backup, that can quickly correct the destruction you do to the Ubuntu OS, before you start biopsying & autopsying it..?


I stumbled upon this informative thread... 

[http://ubuntuforums.org/showthread.php?t=1054777&highlight=backup](http://ubuntuforums.org/showthread.php?t=1054777&highlight=backup)

Learning this is gonna be my priority one.. Only then will I attack the OS with gusto, like a 4-year old kid taking apart daddy's alarm-clock...

I wants to know all there is to know about making and running backups in Ubuntu...  Five reinstalls in two weeks is a bit much...



The best way to 100% back up is here..

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Do that and it will create a tar.gz of your / folder. After that you can put the tar.gz in a safe place. I put mine on a seperate partition so that its easily moved and extracted.

---

### Post by yknivag on 2009-02-06
> **ajgreeny said:**
> I make sure I have a backup of my /home, but don't worry about a system backup as it is so quick to reinstall if everything goes belly up.  The one extra thing I do is run aptoncd every so often, and make an iso file (in my /home) of all the updates I have added and packages I have installed with apt.  Then if I need to reinstall ever, I have a downloaded package for everything and can just get back to the same state without all the download palaver and time wasted.  I just keep the most up to date iso file and get rid of the old ones.

aptoncd sounds like a very good idea.  Does it work with putting updates done on one system on to another too?

---

### Post by celticbhoy on 2009-02-06
have a look at Timevault - on the fly backup with snapshots.

[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)

---

### Post by Bablefish on 2009-02-06
I back everything up by habit, flash drives and CDs

---

### Post by ChildOfMana on 2009-02-06
[quote="cartisdm"]Actually, I'd like to do the same thing for Firefox now that I think about it. I can NEVER remember what plugins and themes I've downloaded. After a reinstall I have to search through everything again![/quote]

For backing up Firefox extensions try[FEBE]("https://addons.mozilla.org/en-US/firefox/addon/2109").

Works a treat! Will even restore them for you too :)

---

### Post by Regnulify on 2009-02-06
I'm an ubuntu noob who started in a couple of months ago. I migrated to get off of a bloated xp instance on an aging laptop. I had to keep xp (Visual Studio) so I converted it to a vm. The vm (with all the unneccessary stuff removed) ran much better than an install. Go figure.

That said, yesterday the laptop died. I head out and get a new one. Elapsed time to get back to business with Ubuntu?
1 hour.
Elapsed time to back up the system restore in Vista so I can return the laptop if I hate it: 3 hours.

I'm a believer.

---

### Post by cartisdm on 2009-02-07
> **ChildOfMana said:**
> For backing up Firefox extensions try[FEBE]("https://addons.mozilla.org/en-US/firefox/addon/2109").

Works a treat! Will even restore them for you too :)

Right on!!  That will save me so much trouble, plus I don't have to worry about it when I'm doing installs on my other computers either. Thanks!

---

### Post by DonaldJ on 2009-02-07
There are lots of good backup-plans in this thread...  It's difficult to pick one.. so in I went to System>Administration> and I ran "create a USB startup disk"... I'm thinking I'm gonna run all the available back-up methods..  so I'll have the whole package of options when it comes time to rescue the system from my messing it up,till I eventually stops treating Linux like I treated windows...  Running windows for many years made me vulnerable, paranoid, and bullied...  It's gonna take a while to get over it, and to get accustomed to all this Linux honesty and freedom, and brotherhood...  
I would install a windows OS, then run through it with claws, fangs, and the best available cleaners, and even then I couldn't block the attacks...  It made a feel like "sitting on tacks"...  I do an y of that windows style cleanup with Ubuntu, and it damages the OS...  Best op is to not treat Ubuntu like windows, cuz it isn't windows...

Does anyone have a complete list of the available options for Ubuntu backups.. Where and how to get them.. How to make a back-up with them, and How to apply the back-ups..?  This thread would be a good place to post them all in...

Maybe post it in an established format..  
I.E.:  
Backup One:  FEBE
Description:  Firefox files backup...
Link: to the download install...
How to install it...
How to run it to create its its backup...
How to run it to apply its back-up...
Notes:  I doubt I would want a Net-connected browser to hold a backup... I'd want to know how vulnerable it is to hack attack...

Back-up Two: Create a USB start-up disk...
Description:  USB Start-up Disk...
Link: System>Administration>Create a USB start-up disk (on a DVD)...

Back-up Three, Four, Five, Six..


I figure you install Ubuntu.. Add all the updates.. Add all your music and pix and notes.. Reboot.. Add all the update options from the above list, which will eventually happen next in this thread..  Reboot, then run each back-up method...  Label them properly..  File them in a proper place...  If there are unscrupulous-folks in your place, then store your back-ups in another place, like safe at granny's...  

I wonders how many huge-corporations have their precious backups hidden at "granny's house"..?  
I wonders how many governments have their precious data backups hidden in a "granny's house"..?
Who knows.. maybe grannies hold all nations top-secret data backups..?  
or it's all hidden under the her woodpile, or in the rafters of granny's garage..?

Me thinks back-ups for your fresh new OS install is the number-uno consideration, after getting the system like you like it.. then you won't be stressing so much trying to fix it as much as you must, in finding your selves in those "pickles"...

The comedy of it, is nearly everyone learns what not to do, by dismantling a new thing, in doing what they aren't supposed to do to it...  It's like a curious-kid dismantling daddy's alarm clock... It's "Science".. it's like a huge everything grinder-upper... It's like how many of us treat secondary domestic relationships.. We push them to breaking-points, in testing them for strength, almost destroying them with the silly tests.. is why there's so much pain in love...
Neat thing about Linux, is that it's build on love.. It's fueled with love.. It is love...  Linux is one giant step by man, toward realizing a "brotherhood of man"...  Linux people are the best of the best...

---

