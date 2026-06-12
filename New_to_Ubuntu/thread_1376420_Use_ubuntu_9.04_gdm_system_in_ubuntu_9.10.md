---
title: "Use ubuntu 9.04 gdm system in ubuntu 9.10"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by Macinbomzh on 2010-01-09
Is there a way I can bring back and use the login system used in ubuntu 9.04 instead of
the one in use within ubuntu 9.10?

---

### Post by shuttleworthwannabe on 2010-01-09
you may want to head over [here]("http://www.ubuntugeek.com/nice-themes-for-ubuntu-9-10-karmic-users.html") to take your pick.

---

### Post by Macinbomzh on 2010-01-09
How can I apply those themes?

I use this in the commandline
```

export DISPLAY=:0.0
sudo -u gdm gnome-control-center

```but it does only apply the gtk theme, not the form itself

---

### Post by shuttleworthwannabe on 2010-01-09
I just remembered, Karmic uses a different way of running the GDM system--may be someone here can help you hack that part. The GDM part may not install, but the themes may.

S

---

### Post by Macinbomzh on 2010-01-09
> **shuttleworthwannabe said:**
> I just remembered, Karmic uses a different way of running the GDM system--may be someone here can help you hack that part. The GDM part may not install, but the themes may.

S

Is there a way I can completely replace karmic's gdm system to use the one was in jaunty?

---

### Post by Methuselah on 2010-01-09
Unless you are reasonably comfortable with fixing problems I wouldn't suggest you mess with the gdm.
It would be preferable to run Jaunty if the ability to theme the login is of paramount importance to you.

Just my 2c.

---

### Post by Macinbomzh on 2010-01-09
> **Methuselah said:**
> Unless you are reasonably comfortable with fixing problems I wouldn't suggest you mess with the gdm.
It would be preferable to run Jaunty if the ability to theme the login is of paramount importance to you.

Just my 2c.

I have no problem with fixing problems.
I'm just saying if is there a way to access the source of gdm and change
the way the form looks like,
Or completely change the way karmic boots.
Tried over several threads, found nothing.

---

### Post by dzon65 on 2010-01-09
Gdm and xsplash can be fully tweaked.The easy way is just to replace the background in usr/share/images/xsplash (root).
Then there's this tutorial by Tinivole which allows you to change gdm even to act as a quick browser:[http://ubuntuforums.org/showthread.php?t=1333683](http://ubuntuforums.org/showthread.php?t=1333683)
Not too long ago exosyst even made a menu allowing you to change xsplash,gdm and icon theme:
[http://ubuntuforums.org/showthread.php?t=1358026](http://ubuntuforums.org/showthread.php?t=1358026)

---

### Post by warfacegod on 2010-01-09
```
sudo apt-get remove gdm

sudo apt-get install gdm2.28
```

Will remove 9.10's gdm and replace it with 9.04's.

Warning: I did this but never got it running correctly and had use startx to get my GUI running before logging in.

---

### Post by dzon65 on 2010-01-09
> **warfacegod said:**
> ```
sudo apt-get remove gdm

sudo apt-get install gdm2.28
```Will remove 9.10's gdm and replace it with 9.04's.

Warning: I did this but never got it running correctly and had use startx to get my GUI running before logging in.

Hi warface!Say,that's a tricky one.You might wanna have alook at Tinivole's how to.There's a backup in there in case something should go wrong.And besides,it looks pretty cool.

---

### Post by warfacegod on 2010-01-10
I need to modify my last post. It should read ....install gdm 2.20 not 2.28, sorry for my mix up.


A more concise way of doing it is on post #16 of this thread:
[http://ubuntuforums.org/showthread.php?t=1332432]("http://ubuntuforums.org/showthread.php?t=1332432")

I f you have problems with it, like I did, then:

```
sudo apt-get install gdm
``` should put you back to where you started.

dzon65 Greetings from the heavens. It is a tricky one considering ...install gdm2.28 won't do a damn thing at all. Yeah, I've scanned through Tinivole's thread a few times but never got around to trying it (maybe I'll test it on my wife's computer). It does look slick though.

---

### Post by Macinbomzh on 2010-01-10
> **warfacegod said:**
> I need to modify my last post. It should read ....install gdm 2.20 not 2.28, sorry for my mix up.


A more concise way of doing it is on post #16 of this thread:
[http://ubuntuforums.org/showthread.php?t=1332432](http://ubuntuforums.org/showthread.php?t=1332432)

I f you have problems with it, like I did, then:

```
sudo apt-get install gdm
``` should put you back to where you started.

dzon65 Greetings from the heavens. It is a tricky one considering ...install gdm2.28 won't do a damn thing at all. Yeah, I've scanned through Tinivole's thread a few times but never got around to trying it (maybe I'll test it on my wife's computer). It does look slick though.

Erm.. I wouldn't suggest to do such a thing, for some reason it says that it cannot
load "module i810" and when I try to delete it, it says:
```

E: gdm-2.20: subprocess installed pre-removal script returned error exit status 2

```

can anyone help?

---

### Post by warfacegod on 2010-01-10
sudo apt-get remove gdm2.20

sudo apt-get install gdm

---

### Post by Macinbomzh on 2010-01-10
> **warfacegod said:**
> sudo apt-get remove gdm2.20

sudo apt-get install gdm

```

Removing gdm-2.20 ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing gdm-2.20 (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 gdm-2.20
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

not working

---

### Post by warfacegod on 2010-01-10
Reboot.

Try it this way:
```
sudo apt-get remove gdm (no 2.20)

sudo apt-get install gdm
```

If not then just try installing gdm. It's newer so it should want to replace the older version.

Make sure you have all updates installed.

---

### Post by Macinbomzh on 2010-01-10
> **warfacegod said:**
> Reboot.

Try it this way:
```
sudo apt-get remove gdm (no 2.20)

sudo apt-get install gdm
```If not then just try installing gdm. It's newer so it should want to replace the older version.

Make sure you have all updates installed.

Nope.... it says gdm is not installed and I cannot execute
```

sudo apt-get install gdm

```since it requires gdm-2.20 to be removed and the removal returns exit status 2
I tried to edit gdm-2.20 conflicts in the /var/lib/dpkg/status and gdm worked well but
then the Xsplash did not appear.

Whatcha say.... maybe I should completely remove all files that come with the package and remove it 
from the list? I'm just thinking.. if there's an easier way to fix this, before I take such drastic measures >.>

---

### Post by warfacegod on 2010-01-10
I think your archive cache is full.

```
sudo cd /var/cache/apt/archives
sudo rm -rf *
sudo mkdir partial

sudo apt-get update
```

Then retry gdm stuff.

---

### Post by Macinbomzh on 2010-01-10
> **warfacegod said:**
> I think your archive cache is full.

```
sudo cd /var/cache/apt/archives
sudo rm -rf *
sudo mkdir partial

sudo apt-get update
```Then retry gdm stuff.

I have found how to fix it, may also fix all problems of that type:
[http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/](http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/)

I guess I'll just have to sit down and wait until something will move and an ability
to edit the xml of the gdm screen will be an option.

But thank you for your help anyways :D

---

### Post by kansasnoob on 2010-01-10
> **methuselah said:**
> unless you are reasonably comfortable with fixing problems i wouldn't suggest you mess with the gdm.
It would be preferable to run jaunty if the ability to theme the login is of paramount importance to you.

Just my 2c.

+1!

---

### Post by warfacegod on 2010-01-10
Sorry you couldn't get it to work. You had the same problem I did, that's why I gave you fair warning. It was, however much easier for me to fix. I didn't need to do any of the hacks in your thread. Messing with the gdm is never a good idea.

---

### Post by Macinbomzh on 2010-01-10
I still feel the emptiness inside of me, lack of complete customization (and speed) made
me leave windows.
I wonder, is there a way to edit the source of gdm2.28, or maybe change to
another login screen application?

---

### Post by warfacegod on 2010-01-10
If you are hell bent on changing login, you could use kde ideas in this thread:

[http://ubuntuforums.org/showthread.php?t=1332432]("http://ubuntuforums.org/showthread.php?t=1332432")

Warning: Read the entire post. I got some odd results but it worked. I ended up doing a 9.10 fresh install soon after so the only thing I really ended up with, when all was said and done was using ktorrent over Transmission. *It did work though.*

---

### Post by Macinbomzh on 2010-01-10
Bah, a whole framework for just the login screen....
I'll just leave it as it is.

---

### Post by warfacegod on 2010-01-10
I ended up using this on my new install. Works fairly well.

[http://ubuntuforums.org/showthread.php?t=1358026&highlight=gdm-setup]("http://ubuntuforums.org/showthread.php?t=1358026&highlight=gdm-setup")

---

### Post by Macinbomzh on 2010-01-10
> **warfacegod said:**
> I ended up using this on my new install. Works fairly well.

[http://ubuntuforums.org/showthread.php?t=1358026&highlight=gdm-setup](http://ubuntuforums.org/showthread.php?t=1358026&highlight=gdm-setup)

me too, used it before asking this question.

---

### Post by warfacegod on 2010-01-10
> **Macinbomzh said:**
> Bah, a whole framework for just the login screen....
I'll just leave it as it is.

This made me laugh. Bah! Indeed!

---

### Post by dzon65 on 2010-01-10
This GDM thing keeps reappearing.Like I said,an easy way to change the xsplash is by just changing (root)the wallpaper in usr/share/images/xsplash.The Tinivole option is far more advanced.But Exosyst made a real menu for it,which is safe and lets you change your xsplash,gdm and icontheme.Check out this thread:
[http://ubuntuforums.org/showthread.php?t=1358026](http://ubuntuforums.org/showthread.php?t=1358026)
Edit:never mind the link,it was mentioned before exept,today the how to have it as a regular menu is added.
(major hangover).Forgot to mention though:for the easiest way,besides the wallpaper,you can change the logo as well.Get rid of the four sizes logos and replace them with your own.if you want to stay in a more or less same logo,take the example (screenshot),run it through gimp,do whatever you like with it,make four sizes and put them in the xsplash folder.It won't change your gdm but....

---

### Post by warfacegod on 2010-01-10
I already posted that thread but it won't change the login interface itself. At least not for me.

---

### Post by dzon65 on 2010-01-10
Warface!  (maybe I'll test it on my wife's computer)...........LOL

---

### Post by warfacegod on 2010-01-10
>  Warface! (maybe I'll test it on my wife's computer)...........LOL


Don't laugh, she'll her you!

---

### Post by Methuselah on 2010-01-10
Alas...as I said three pages back; not worth the trouble.
I expect that the new gdm wil eventually mature to the point of having useful theme support.

---

### Post by warfacegod on 2010-01-10
> **Methuselah said:**
> Alas...as I said three pages back; not worth the trouble.
I expect that the new gdm wil eventually mature to the point of having useful theme support.

You're absolutely right but some people just can't help doing things they know are bad ideas: install 9 OS's, mess with gdm, use Windows, stuff their faces with fast food, stuff their VCR's with fast food.

---

### Post by dzon65 on 2010-01-10
If she does......greetings from Ghent,John&co

---

### Post by warfacegod on 2010-01-10
Actually she's at work, so I've been considering dropping her comp. into a recovery shell and changing her password.

---

### Post by llawwehttam on 2010-01-10
Naa. Just add a script to shutdown her computer 10 mins after login. Could be funny.

---

### Post by warfacegod on 2010-01-10
I'll have it play sound bites of Austrian Death Machine every 52 seconds.

---

### Post by dzon65 on 2010-01-10
Or a forever turning cube?

---

### Post by warfacegod on 2010-01-10
Desktop could invert itself randomly.

---

### Post by dzon65 on 2010-01-10
Put in a wav replacing the drum login sound to the schnitzel song.

---

### Post by Macinbomzh on 2010-01-10
> **warfacegod said:**
> You're absolutely right but some people just can't help doing things they know are bad ideas: install 9 OS's, mess with gdm, use Windows, stuff their faces with fast food, stuff their VCR's with fast food.
Don't forget stuffing their fast food with VCRs

And coding under .NET

> **warfacegod said:**
> I'll have it play sound bites of Austrian Death Machine every 52 seconds.

You should make the computer ask her not to leave it each time she starts a shutdown procedure;
like "Please, don't close me, I don't want to be left lonely :("

I tried it on some people, it really works.

---

### Post by Macinbomzh on 2010-01-10
> **Methuselah said:**
> Alas...as I said three pages back; not worth the trouble.
I expect that the new gdm wil eventually mature to the point of having useful theme support.

Actually it does worth the trouble, I wouldn't say you have advanced in anything with such
an attitude.

Just sitting around doing nothing of lack security, saying something is a bad idea
while it has 99% result of fail in the first attempt and afterwards yapping about your ability to
see forward; it is like winning the fight, of being right-and losing the war, of progressing.
sitting around doing nothing does not worth your time spent.
Trying in this case is the best choice, as all is revertable.

But I guess I will leave gdm atm to my
 [IMG]http://img192.imageshack.us/img192/5914/spongebobimaginationdes.jpg[/IMG][IMG]http://yfrog.com/5cspongebobimaginationdesj[/IMG]
 imagination

also I've heard of [SLiM]("http://slim.berlios.de/") but when hearing "on which... functionalities are not needed" it just repels me

---

### Post by warfacegod on 2010-01-10
I could have it display an error message every 5 minutes:

```
Your operating system is currently about experience a major failure. Please stand up for further instructions
```

Then I could ask her "Why the hell do you keep standing up!?"


The guys making Sponge Bob cartoons need to lay off the drugs.


New song:

(Death Metal Roar)
Who lives in a pentagram under the sea?
Sponge Bob Satan Pants!

Who's wicked and evil and demonic is he?
Sponge Bob Satan Pants!

---

### Post by warfacegod on 2010-01-10
Hell, if I was on drugs, I'd say I need to lay off 'em too with the above song.




(Audience shouting warface, warface...aahhhh!)

This next one's called!...

[SIZE="3"]***Satan Versus The Carebears! Rrooooaaaarrrrrrrr!***[/SIZE]

---

### Post by Macinbomzh on 2010-01-10
> **warfacegod said:**
> Hell, if I was on drugs, I'd say I need to lay off 'em too with the above song.




(Audience shouting warface, warface...aahhhh!)

This next one's called!...

[SIZE=3]***Satan Versus The Carebears! Rrooooaaaarrrrrrrr!***[/SIZE]

I wouldn't post again to avoid the transformation of this thread into a shitpost.
a damn, I just did.

anyways....** ALL HAIL THE CAREBEARS**!!!!!

> **warfacegod said:**
> I could have it display an error message every 5 minutes:

```
Your operating system is currently about experience a major failure. Please stand up for further instructions
```Then I could ask her "Why the hell do you keep standing up!?"

You should add a sad face into it and make it say "please don't let me die...."


someone should lock this thread before it keeps growing pages.

---

### Post by warfacegod on 2010-01-11
> someone should lock this thread before it keeps growing pages.

Come on, a dive into utter madness and lunacy is just what we need around here.

[SIZE="2"]

Nobody lock the thread! Leave it open for all eternity. Other wise, I'll send the Carebears after you right after their done with Satan's beatdown.[/SIZE]



So this is what 26 hours of sleep deprivation feels like when your 30.

---

