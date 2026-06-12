---
title: "Failed to execute child process &quot;sound-juicer&quot; (No such file or directory)"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by John Peschken on 2010-08-22
In my "Places" menu, an "Audio Disk" item appears when I put a CD in the drive.  This might seem like a good thing, but when I click on it I get the following error.

[B]Could not open location 'cdda://sr0/'
Failed to execute child process "sound-juicer" (No such file or directory)[/B]

I _did_ have Sound Juicer installed, but I uninstalled it using the "Ubuntu Software Center".  Apparently it has left this annoying gift behind.  

How can I make it go away?

---

### Post by stoogiebuncho on 2010-08-22
Never had this problem before, but I'd try opening up Nautilus and going to Edit > Preferences > Media and checking what the default action is for a CD.  It's possible it's still set to open in Sound Juicer, and if you change that maybe you won't get the error anymore.

---

### Post by John Peschken on 2010-08-22
> **stoogiebuncho said:**
> Never had this problem before, but I'd try opening up Nautilus and going to Edit > Preferences > Media and checking what the default action is for a CD.  It's possible it's still set to open in Sound Juicer, and if you change that maybe you won't get the error anymore.

The default action is "Do Nothing" for everything.  Sound Juicer is not mentioned anywhere, but it seems to have left behind this nasty little residue.  

I found what it said has SJ configuration information in the Synaptic package manager after this problem started.  That didn't help

---

### Post by ranch hand on 2010-08-22
I would run;
```

sudo apt-get purge sound-juicer

```
as a start and see if that helps.

Post the terminal out put here when you run that.

---

### Post by John Peschken on 2010-08-22
> **ranch hand said:**
> I would run;
```

sudo apt-get purge sound-juicer

```
as a start and see if that helps.

Post the terminal out put here when you run that.
Well, my frustration got the better of me, and I just did a fresh install of Ubuntu.  I'm new to Ubuntu, and I didn't have a lot invested in my installation yet.  It's the second time i have done that, both times apparently due to problems with Sound Juicer residue.  I'm staying a mile away from that one from now on.

I'll file your solution away for future use, though.  That could be a handy one.

---

### Post by ranch hand on 2010-08-22
That is a true noob response.  Don't take that wrong.  Check my join date here.  That was 3 weeks before I installed my first Linux ever.  Ubuntu 8.04.

Reinstalled 5 times in 7 days when I installed.

This is Linux, it can actually be fixed.

The problem is using USC to remove the package.  It does not remove it all (purge).

If you want a gui for that job use Synaptic and choose "complete removal" instead of "remove".

Apt-get purge is better.

Here are a couple things you should read.  First read all of this (not long).
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Next, download and refer to this when you have problems.  Will probably help a lot, did me.  If not it will at least give you the ability to ask better questions and maybe even understand the answers.
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

That first link, I think, should be read before installing for the first time.  It is well written and insiteful.  It helps understand what you have gotten into and, hopefully, what you have gotten out of.

The learning curve is not that bad.  It was easier for me because I wiped MS off my box and switched.  You probably did not.  I would try to use Ubuntu only for a week or two.  It will help.

I did get smart and dual boot the second week.   I dual booted with Ubuntu 8.04 on a small partition.

Everything I did, I did to that one first.  Upgrades, installs, removals, everything.  I still have the original install (after the dual booting started) of Hardy on here now.   Runs smooth and solid.  It is nice to be able to break the OS with out busting the one you use.

Read the stickies at the top of every forum index page, the first post is really all you need to read.  Those on the ABT and General Help forums are very good and should be read by all of us once in a while.  I know I do not do it enough.

Remember to have FUN.

---

### Post by John Peschken on 2010-08-23
I am prone to impatience when it comes to computers.  I am used to knowing how to solve the problems as a result of years of net admin and help desk experience in a dos/netware and then Windows environment.  I do remember going through the same mutiple install drill with Windows when that was new to me.  My lack of knowledge about Linux combined with that impatience drove me towards the brute force solution.  It's simple things like for instance; on your tip to use "sudo apt-get purge sound-juicer" to remove it.  How does one know the "sound-juicer" part.  You could probably guess it eventually, but it would have taken me a while to try it with the dash.  No doubt there's a place to look, but I don't know where it is yet.  One forgets how much small knowledge there is in learning a new OS.  It makes empathize better with those users I supported all those years.  Learning any new OS is hard.
 
Thanks for the tips.  I will check them out.

---

### Post by ranch hand on 2010-08-23
I did not actually know the "sound-juicer" part.

I looked it up in Synaptic.  I realize that USC is popular with folks and that Ubuntu wants to use it to be the main way to get packages.

I do not like it for a number of reasons but the main one is that it does not use, or supply, the actual package name.

Synaptic and Apt are the only ways I use for package management.  You may want to also look at Aptitude.  It is a CLI tool like Apt but a lot of folks like it a lot better.  It is not installed in 10.10 by default so many in testing have installed it.

It has a very nice terminal gui like interface and the ability to list a lot of different things.  It may well be the tool for you with your background.

I started with computers only in the 90s (later than a lot of folks I know) but first used MSDos and then MSDos with DosShell.  I am not sure that that was not the peak for MS.

All I am saying is that you need to watch out for what is going on in USC.  It does not give the information you really need.

With your background Synaptic is not going to confuse you and it has the ability to tell you just about anything to do with packages and do just about anything with packages.  It also has the "remove completely" option which gets rid of things much better than "remove" will.

You might want to, in terminal, run "man dpkg".  Dpkg is the foundation of package management and what every thing else is built on.  When things really go south you can generally use it to whip things into shape.

---

### Post by John Peschken on 2010-08-23
Of course now I realize the "sound-juicer" part was in my original error message. Duh!
 
A new OS has a way of making you feel disoriented, helpless. and stupid. That's hard for me. I am used to knowing 90% of the answers off the top of my head. 
 
When the frustration starts to build, I just need to make myself step away from the keyboard, take a deep breath, and be patient about trying to find the solution instead of blowing things up and starting over. 
 
Thanks for the help.

---

### Post by ranch hand on 2010-08-23
Yup, I have to remember to breath too.

Have fun with the now OS.  It is one thing that Linux has that MS does not seem to permit.  FUN.

---

### Post by Tonyr63 on 2011-03-04
Hi

i have the same problem and i ran the sudo apt-get purge sound-juicer command and i got a response package sound juicer not installed, so not removed.

i still have the problem reported above and I have never installed sound juicer on this system.

Do you have a suggested solution as this install of Ubuntu will not play an audio CD in Rythembox which is the default although movie player will play.  If there is not CD in the drive Rythembox will start however if a music disk is loaded it will not start.

I have removed and reinstalled Rythembox to no avail.

This is basic functionality that should work however many have posted problems and I have not found definitive solutions yet.

Can you help

---

### Post by mjhouska on 2012-01-25
bump same problem this is a new ubuntu studio 10.04 install.

---

