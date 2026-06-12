---
title: "Kid friendly ubuntu ?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by kdm on 2008-12-17
Hi,

I am setting up a system for my niece & nephew (5 & 3yrs respectively) as a christmas present & I was wondering if there is a child friendly alternative to having to enter the password ?

Thanks

---

### Post by linuxguymarshall on 2008-12-17
Autologin

---

### Post by OutOfReach on 2008-12-17
+1 Autologin.
Unless of course you want to teach them how to type in the username and password. Which I think in the case of 5 & 3 year olds wouldn't be much help.

---

### Post by SunnyRabbiera on 2008-12-17
> **linuxguymarshall said:**
> Autologin

Indeed, but it is very unsafe.
Personally I would teach them the value of passwords to keep them safe.

---

### Post by donkyhotay on 2008-12-17
Autologin is the easiest for kids that age, make certain though that their account is limited. You don't want them accidently gaining root access and messing up your system. 
<shuddering at the thought of a 3 year old with root access>
Once they get older (maybe starting with the 5 year old) you should create their own (once again limited) accounts for them to teach them proper computing practices.

---

### Post by nhasian on 2008-12-17
when my 3 & 5 year old nieces come over, I switch them over to the Guest Session in Ubuntu 8.10.  That way they dont accidentally delete or muck up anything.  

There is a lot of educational software to choose from in Applications->Add/Remove Software->Education  typing tutors, hangman, tuxpaint, etc

also take a look at [http://edu.kde.org/](http://edu.kde.org/)

The KDE Education Project

Free Educational Software based on the KDE technologies

---

### Post by kdm on 2008-12-17
Thanks for the help everyone !

Their accounts are limited, but it wouldn't really matter anyway because as of Christmas Day, it becomes their system and if they messed it up I could just reinstall for them - but I take your point.   

About autologin, can it be set up to only log them in automatically - or once installed does it treat all users the same ? 

Given the choice, I would opt for the password route, and I think that the 5year old would get it no probs, but it was the 3 yr old I was worried about.  I think he would probably get it too after a while, but I didnt want to suck all the fun out of this ubuntu thing for them before they even begin with it !  I have set them up with a ubuntu/XP dual boot system and I would love it if, over time, they favoured ubuntu, so I didnt want to scare them off before they really begun.  

I have stuck all their favourites (which they play on my system) on it (e.g. Tux racer / Edu suite / Mr. Potato Man etc. etc.) Would anyone reccomend any other good apps for kids ?

---

### Post by geo316 on 2008-12-17
FWIW I set the password for my youngest to his name. He knows how to spell and type his name!

He has indeed learned the value of a password protected account and has the peace of knowing that his brothers wont wreck his desktop and play his games but currently the password is at a level he can grasp - and remember... as he gets older he'll either set himself or ask for a more complex password like everyone else in the family...

my two cents...

---

### Post by kdm on 2008-12-17
> There is a lot of educational software to choose from in Applications->Add/Remove Software->Education typing tutors, hangman, tuxpaint, etc

also take a look at [http://edu.kde.org/](http://edu.kde.org/)

Answered my question before I even asked it - Now thats service !!! :-)

---

### Post by HotShotDJ on 2008-12-17
I agree with earlier posts -- a password protected account is not appropriate for a 3 year old.  At the same time, it is not appropriate to allow a 3 year old unsupervised access to a computer (or any other appliance, such as a TV).  The use of a guest session is the more sensible option.  The adult who will at all times be supervising the 3 year old can log into his/her account and then open a guest session for the child.

The 5 year old, while also requiring supervision, is old enough to learn about basic system security and should be able to manage a simple password (I suggest a two word password, where the two words are not obviously related but can be easily remembered by a 5 year old).  This is similar to allowing a child this age to have a key to the house, even though he'll never be left alone at home.  Teaching skills (personal safety, cooking, computer software and security, etc.) should be done as early as possible using age-appropriate methods.

Also, for young children, consider installing [Dansguardian]("http://dansguardian.org/"). While I strongly disagree with web content filtering for children over 12 or 13 years of age, it is a good idea for children as young as your niece and nephew.

---

### Post by kdm on 2008-12-17
> FWIW I set the password for my youngest to his name. He knows how to spell and type his name!****

I had considered this one too, but of course I had already taken the short cut of creating a joint account for them.  Maybe I should just seperate them after all.

---

### Post by donkyhotay on 2008-12-17
I would seperate the accounts, the 5 year old should begin learning proper computing practices now and it will help if he/she has their own account for their passwords, personal files, etc. The 3 year old will probably need his/her own in another 2-3 years as well so might as well do it now since your setting everything up anyways. As they age you will want to slowly (and carefully) grant them further privileges to the system until they are able to handle administering the computer on their own. I personally wouldn't use a web content filter just because they give a false sense of security that doesn't exist. Web filters don't catch everything, doesn't take kids long to figure out how to bypass them if they want to (kids are more computer savvy then many parents give them credit for), and they should be supervised using the computer anyways at that age.

---

### Post by ubuntu27 on 2008-12-17
You can put a different GDM (The login screen where you type your username and password), where all you have to do is to select a user name or the user avatar (instead of typing the username), and type password.

That way it is easer to memorize. You van put their photos as their avatar
Tell them to click on to the avatar, and then type their password.

The password can be short..

MyDearKitty, dogcat, etc.

Here is a exmaple of a GDM with avatar:

[http://gnome-look.org/content/show.php/Intrepid-Ibex+3+GDM?content=92876](http://gnome-look.org/content/show.php/Intrepid-Ibex+3+GDM?content=92876)

You can find more at [GDM Themes]("http://gnome-look.org/index.php?xcontentmode=150")

---

### Post by Keen101 on 2008-12-21
Yeah, i also like the GDM idea.

I don't know what to recommend for easy logging in. I recommend against autologin, and favor timed login if that's what you need, because if the xorg or something gets screwed up you will not really be able to fix the system easily, because it will keep trying to autologin.

on the other hand it looks like you are thinking of having seperate accounts anyway, so maybe no timed login at all.

some programs the kids might like:

Supertux
tuxpaint
Kolourpaint
glest
pingus (although not finished)
warzone 2100
Ri-Li
greenfoot programming maybe for later ([http://www.greenfoot.org/](http://www.greenfoot.org/))
maelstrom


While i agree with some sort of filtering software, i don't think the computer should have Internet access at all until a middle school age. As long as there is no Internet access, i don't see a problem with unsupervised access. I go my first computer when i was 5 or six. I had unsupervised access all the time, but no Internet. I had fun playing games first with DOS, and eventually windows. In high school i converted to linux.

these two are only for firefox, but they do help.

WOT (addon)
Foxfilter (addon)

---

### Post by The Cog on 2008-12-21
As root, you can set easier passwords than normal users are allowed to (including blank passwords I think). You can set any user's password using roots priviledges with this command (for user cog, for instance):
**sudo passwd cog**
Sudo might ask you for your password before giving you the "Enter UNIX password" prompt for the new password - don't let that confuse you.

---

### Post by earthpigg on 2008-12-21
> **Keen101 said:**
> Yeah, i also like the GDM idea.
some programs the kids might like:

Supertux
tuxpaint
Koloupaint
glest
pingus (although not finished)
warzone 2100
Ri-Li
maelstrom


planet penguin racer
moonlander
lbreakout2


also, im 25 and i use kolourpaint as my primary image editor lol...

(when you go looking for it in the repos, make sure you notice that its kolo_***u***_rpaint.)

---

### Post by ugm6hr on 2008-12-21
What login setup have you chosen for the XP part of this dual-boot?  And do they cope with it?

The only thing that GDM will not allow is a no password, click on avatar only option.

I think autologin is not unreasonable if you are going for a "joint" limited user account.

However, a "face-browser" GDM login may be better (like XP with individual passwords), if they manage that.

Consider setting a separate /home for any future reinstallations (if you are going to give them sudo privileges).

---

### Post by stalkingwolf on 2008-12-21
Here is my experience. I have set up Edubuntu for 4 children ( 3 6yrolds and a 4yrold.)

One of the boxes is for the sole use of the young'un.  It was set up with her fathers user name and password. He logs in or helps her login, then off she goes to play the games or log in to a couple "childsafe' sites.

The second has edubuntu and 7.10 on it.  As a rule this girls mother spends as much time in Edubuntu "playing" as does her daughter.

The Third is a dual boot I set up for My Grand Nephews.  They spend a lot of time in Edubuntu playing games and such.  That is when they can get My Sister and/or her unemployed Husband off their favored poker site.  That is where the dual boot comes in . I was forced to install XP so My sister and her current other can use it.

Scary huh. A 6 yr old can function fine.  Their Grandparents are at a loss.

---

### Post by northern lights on 2008-12-21
You also just choose a simple one-letter pass for the kids user accounts. They could remember where the "A" key is, so just make it lower-case "a". Sorted.

Or opt for a Guest session as previously recommended.

---

### Post by abn91c on 2008-12-21
Not sure if I missed it in the previous post but you may just want to install the Edununtu desktop, it will have all the learning kid oriented games and programs you want

---

