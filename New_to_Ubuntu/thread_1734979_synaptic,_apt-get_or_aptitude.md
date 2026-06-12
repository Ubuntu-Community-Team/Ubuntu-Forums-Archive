---
title: "synaptic, apt-get or aptitude"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by wep940 on 2011-04-20
I posted in [http://ubuntuforums.org/showthread.php?p=10697140#post10697140](http://ubuntuforums.org/showthread.php?p=10697140#post10697140) and was told I was wrong, so I posted back asking for clarification so I could learn more.
 
Basically, a few years ago, I used apt-get to install a package and when it was installing it I got many, many of the nested "dependency not met" messages.  I posted on the forum (different userid then - computer crashed and lost all) asking for help.  Someone who is now one of the big gurus here posted back and told me for each missing piece to do apt-get build-dep.  I did that and everything was fine.  I was also told by this person to use synaptic package manager, not apt-get or aptitude.  So, ever since I have been using Synaptic to install packages.
 
Now, according to the link above, I am told I am completely wrong and to stop posting false information!!  This is followed by a post that says apt and aptitude both used to have problems with dependencies but they are all fixed now.
 
So, I really want to know - what method am I supposed to follow?  I was told in the other thread that Synaptic is just a front-end to apt, but nobody has explained why I had the problems I did and why apt-get still has build-dep as an option.
 
All I want to do is learn - I'm not trying to argue with anyone, etc., but I also don't like being accused of being a liar when in fact that is the experience I had.
 
Please help so I know the correct way, what if any differences there are between those 3 methods, etc., so I can go forward with more knowledge.
 
Thank you in advance!

---

### Post by LOIREE on 2011-04-20
Unless you're running Ubuntu server (VPS or Dedicated Server) and have to administer everything remotely, it is generally wiser to use Synaptic.

On other other hand, its Linux tradition to do thing in shell. Both should have no problems. But Synaptic is preferred.

---

### Post by brpylko on 2011-04-20
I THINK(I am not sure) that apt-get NOW gets the program and gets its dependencies but build-dep builds(as opposed to gets) the dependencies.


Hope this helps and please try to verify with someone that this is true.

---

### Post by jerome1232 on 2011-04-20
A long time ago, aptitude and synaptice were better than apt-get.

Now they are mostly equivalent in terms of functionality. I personally use apt-get out of familiarity.

---

### Post by Spiritof76 on 2011-04-20
If I am looking for an application I prefer shopping and looking at the dependeancies I will need using Synaptic.  Apt-get is prefered when installing packages for servers and when textually describing steps in web sites or email because you can't cut and paste mouse strokes and clicks.   
I'vw installed a lot of stuff using apt-get , and haven't had a dependency problem yet.

---

### Post by oldos2er on 2011-04-21
build-dep is used to install dependencies (mainly -dev packages ) when compiling source code, as *man apt-get* tells you. And, as far as I know, apt-get has always handled installing dependencies; aptitude used to be better at handling the removal of packages and their dependencies, maybe apt-get has caught up with aptitude in doing that; I don't know. I use aptitude.

It's possible that your problem in the past was caused by not having a particular repository enabled, but it's hard to say now.

---

### Post by wep940 on 2011-04-21
All I know is that I followed instructions for installing some package via apt-get.  It got the package, but in the installation I got the dependency errors, and hence the help to use apt-get build-dep.  It may have been source for that matter, I just don't remember now.
 
At any rate, thank you all for the replies.  It appears that apt-get should work fine now as long as I'm not getting source, though most of the time I usually use Synaptic to avoid the potential for a problem.
 
Thank you all again - it is greatly appreciated, and it helps educate me more in using Ubuntu.

---

### Post by KegHead on 2011-04-21
Hi!

I'v used the -f parameter w/success.

sudo apt-get update -f

sudo apt-get dist-upgrade -f

KegHead

---

