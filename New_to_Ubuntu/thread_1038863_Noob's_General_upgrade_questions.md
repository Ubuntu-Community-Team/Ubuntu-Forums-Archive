---
title: "Noob's General upgrade questions"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by cyan on 2009-01-14
Hello, everyone. I am running Ubuntu EEE 8.04 LTS on an Asus EEE 1000H (a dual boot with XP on another partition). I am a newbie but have managed to tweak my install so that it's working beautifully. I am a happy (and permanent) convert to Linux. 

I have some general questions about upgrading (some of which I also posted on the Ubuntu EEE forums, so forgive me if this is a repeat).

First, I know that doing regular updates is a good idea to keep everything running smoothly. But that's not the same thing as upgrading, right? So my question is, should I make a habit of upgrading to the new version of the underlying distro? Put another way, does upgrading have the same benefits as updating (fixes or patches problems, updates software, improves performance, etc)? I guess what I'm really asking is, should I upgrade or stick with 8.04?

Second, when I upgrade, I don't lose the files and software I've installed, right?  But if I do a clean install of the new version, I have to re-download all my software, correct?

Finally, I've noticed that some people talk about putting their home directory on a separate partition. Am I correct in saying that if my home directory was on a separate partition I could simply install a new version of Ubuntu (or any distro for that matter), point to the home directory and all my files would be conserved?  What about tweaks to the distro?  Would those be conserved?  If someone has a good link on "best practices" with regards to upgrades and conserving a user's settings, that would be very helpful.

Sorry for the long post, it took me a while to get to where I thought I knew what to ask and didn't want to leave anything out. Thanks again for everyone's help.

---

### Post by zvacet on 2009-01-14
Every new version have it's benefits.It fix some things and improve others (this is simplifted explanation),but if you are satisfied with Hardy there is no reason to upgrade.

You are right,with clean install you will lose your installed software and with upgrade not.

Good thing about separate home partition is exactly that,to keep your data and settings.

---

### Post by mikewhatever on 2009-01-14
> **cyan said:**
> Hello, everyone. I am running Ubuntu EEE 8.04 LTS on an Asus EEE 1000H (a dual boot with XP on another partition). I am a newbie but have managed to tweak my install so that it's working beautifully. I am a happy (and permanent) convert to Linux.

A permanent convert, dual booting with windows, that's heresy! Let's not get too exited, shall we.:tongue:

> First, I know that doing regular updates is a good idea to keep everything running smoothly. But that's not the same thing as upgrading, right? So my question is, should I make a habit of upgrading to the new version of the underlying distro? Put another way, does upgrading have the same benefits as updating (fixes or patches problems, updates software, improves performance, etc)? I guess what I'm really asking is, should I upgrade or stick with 8.04?

The difference between updating and upgrading is simple, the former usually installs patches and fixes, but does not install newer versions; the latter installs newer versions for most of the packages.

> Second, when I upgrade, I don't lose the files and software I've installed, right?  But if I do a clean install of the new version, I have to re-download all my software, correct?

That seems to be correct.

> Finally, I've noticed that some people talk about putting their home directory on a separate partition. Am I correct in saying that if my home directory was on a separate partition I could simply install a new version of Ubuntu (or any distro for that matter), point to the home directory and all my files would be conserved?  What about tweaks to the distro?  Would those be conserved?  If someone has a good link on "best practices" with regards to upgrades and conserving a user's settings, that would be very helpful.

First, you'd have to manually point the installer to the home partition, because it wouldn't know by itself. When you reinstall, the root gets formatted, so having the home partition separate prevents it from being formatted too.

---

### Post by jmontelius on 2009-01-14
Stick with the version you have. Upgrading sounds trouble free but I've more than once been forced to recover from a half-way finished upgrade and having to install from scratch.   The upgarde will try to preserve as much as possible of your own settings and applicatiosn and I guess that it's that that makes things though. The thing that you don't get without upgrades are complete new versions of software, if there is a Firefox 4 out it will probably not be included in 8.04 etc 

When you move into the upgrading game do partition your drive so that /home is a partition of its own. You could then do a clean install of everything and your home directory (with a lot of settings for applications) will still be there. Applications will of course have to be installed again.

---

### Post by myromance123 on 2009-01-14
To upgrade, it is recommended to do a clean install, but it is also possible to upgrade through the terminal without losing your stuff.
 
 Just type the following:
```
sudo update-manager -d
```

After that and inputting your password the update manager should start up and a new button with the latest upgrade number will appear and click that to upgrade (if you aren't already using the latest upgrade).

 BUT, I strongly recommend giving new upgrades time(maybe a month or so) before actually moving to it. Take the new upgrade for example, 8.10 intrepid Ibex has lots of bugs. It may function awesomely on your computer and not on others. Study the upgrade a bit from those who have used it to see whether the problems are enormous or no solutions are available yet.

I had my fair share of problems with the new upgrade (although I love it so much) and had to revert to 8.04. Understand that to revert the only way I know of is to do clean install, so if you have problems with the new upgrade and wanna revert, you're gonna have to sacrifice. 

But hey I do not know everything so that was just how I operate :D
 It all comes down to personal choice and skill 
(skill for removing the probs hehe)


OOO the main point is that Ubuntu upgrades are awesome but sometimes take a bit of time to flatten all the bugs, so as soon as major problems are outta the way, GO FOR IT :P

Ubuntu ROCKS~:lolflag:

---

### Post by Sef on 2009-01-14
> First, I know that doing regular updates is a good idea to keep everything running smoothly. But that's not the same thing as upgrading, right? So my question is, should I make a habit of upgrading to the new version of the underlying distro? Put another way, does upgrading have the same benefits as updating (fixes or patches problems, updates software, improves performance, etc)? I guess what I'm really asking is, should I upgrade or stick with 8.04?


It is a personal choice.  Some questions to ask yourself:

1) Is 8.04 working fine for your needs?

2) Do you really want to take a chance of something not working right with an upgrade or clean install?

If you answered yes for 1 and no for 2, then stick with 8.04, unless you want later versions of the applications; however, on the other hand, you answered the opposite, then I would upgrade or do a clean install.  

The desktop for 8.04 is supported until 2011.

---

### Post by stevoo on 2009-01-14
> **cyan said:**
> Hello, everyone. I am running Ubuntu EEE 8.04 LTS on an Asus EEE 1000H (a dual boot with XP on another partition). I am a newbie but have managed to tweak my install so that it's working beautifully. I am a happy (and permanent) convert to Linux. 
Sounds a lot like me :) ( except the newbie status ) 
> **cyan said:**
> 
I have some general questions about upgrading (some of which I also posted on the Ubuntu EEE forums, so forgive me if this is a repeat).
We will try, but cant promise anything

> **cyan said:**
> 
First, I know that doing regular updates is a good idea to keep everything running smoothly. But that's not the same thing as upgrading, right? So my question is, should I make a habit of upgrading to the new version of the underlying distro? Put another way, does upgrading have the same benefits as updating (fixes or patches problems, updates software, improves performance, etc)? I guess what I'm really asking is, should I upgrade or stick with 8.04?
Just for you to know. Any Ubuntu that is labeled *.04 always includes new updates and new functionality. Not all of them are stable. A *.10 is all about stability. That version will expand and what was included in the .04 and produce more stability to the system.
Update is not upgrade. You can update your system with new patches and stuff. But when upgrade you will install newer version of software that will add functionality. 
Now i would reccomend 100% to upgrade if you were using a normal version. Since i am unaware of what are the limitation on a Eee, as i havent used one or know how the OS was changed i cannot tell you to do, as there could be a risk involved there. But it all comes down to you

> **cyan said:**
> 
Second, when I upgrade, I don't lose the files and software I've installed, right?  But if I do a clean install of the new version, I have to re-download all my software, correct? A clean install will remove everything you have and youll end up with what comes with the system. So youll need to backup important files if you do that. 
I dont reccomend it yet it is best to do a normal upgrade as nothing dramatical changes. Maybe at 10.* you can do a fresh install. The good thing with ubuntu is that with a single command you can re install all your programs. :) 

> **cyan said:**
> 
Finally, I've noticed that some people talk about putting their home directory on a separate partition. Am I correct in saying that if my home directory was on a separate partition I could simply install a new version of Ubuntu (or any distro for that matter), point to the home directory and all my files would be conserved?  What about tweaks to the distro?  Would those be conserved?  If someone has a good link on "best practices" with regards to upgrades and conserving a user's settings, that would be very helpful. Have no idea of that ... 
But if you have a different hard disk, you can always backup everything there. :)


> **cyan said:**
> 
Sorry for the long post, it took me a while to get to where I thought I knew what to ask and didn't want to leave anything out. Thanks again for everyone's help.
It is the best thing to give us long post with a lot of info so we can help out more :) 

So keep it on .., ):P

---

### Post by cyan on 2009-01-14
Wow, thank you all for the amazing feedback.  My experience with Ubuntu and the community has been amazing.

So I think the general consensus seems to be "don't fix what ain't broke."  And right now, everything is working just fine.

I think I will take it easy and work on creating a new partition and moving my home directory to that.  If I can figure that out without borking my install, then I'll be ready for when I do want to upgrade.

One other question, stevoo mentioned there is a command in Ubuntu that allows you to reinstall all your programs after upgrading.  What is that command?

Thanks again, everyone!

---

### Post by MLX on 2009-01-14
In the past I have upgraded to every version that came out. It is fairly time consuming to do that every six months. For me 8.04LTS works fine and does everything that I need so I have decided to only upgrade to the LTS versions as they come out. It sounds like you have come to the same conclusion. When in the future you do an upgrade to the next LTS version your installed programs will stay and you will not need to reinstall them. The only time you would need to reinstall them is if you were to do a clean install. I have a separate home partition and would recommend doing it. (It makes doing a backup of your whole home partition easy.) Here is a link that may help. 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Here is another link that has a lot of great info about installing and partitions.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Hope this helps.

---

### Post by cyan on 2009-01-14
Greatest. Community.  Ever.

Thanks, everyone, for the great advice.  I plan to set up a new /home partition and then play with new installs (maybe even other distros) and continued exploring, knowing that my settings and files will remain and that my stable 8.04 install is safe and sound.

---

