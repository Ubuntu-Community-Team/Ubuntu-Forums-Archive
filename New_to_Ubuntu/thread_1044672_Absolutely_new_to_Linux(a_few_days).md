---
title: "Absolutely new to Linux(a few days)"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by S0m3th1ngw13rd on 2009-01-19
Here is a new to Linux question for someone.  I keep reading on this forum and webpages around the web, to not run anything as root.  Understanding that this can open holes and what not in my security. I don't think I'm running anything as root not sure though.  How do I know I'm not running as root(want to be sure). I made a user(me), only thing I have installed is WOW and Guild Wars(using Wine) and Mplayer through add/remove and a Neverwinter nights install on Linux(not wine). Am I using ROOT I dont even know, how n00bish is that?

Please advise

---

### Post by DariusS on 2009-01-19
That is a very good question, something that every new user should try to understand.
Typically, anything you do, unless otherwise specified by you, is done WITHOUT super user privileges (sudo). The most common way to do anything as root (sudo) is through the command line by prefixing any command with sudo, then typing in your password.
If someone tells you not to use sudo or operate as root, they are not being fully truthful; there are some things that can only be done as root. Now, you as a new, average user may not for a while need to do these things, but do not be afraid of root, only apprehensive. Knowing what you are doing will normally prevent anything bad happening. The best way to learn what you are doing, what you should do and what you can do is by asking questions here and reading through other threads.

Again, because it warrants repeating, ***Knowledge of what you are doing will prevent most mistakes***

hope this helps:)

---

### Post by llamakc on 2009-01-19
> **S0m3th1ngw13rd said:**
> Here is a new to Linux question for someone.  I keep reading on this forum and webpages around the web, to not run anything as root.  Understanding that this can open holes and what not in my security. I don't think I'm running anything as root not sure though.  How do I know I'm not running as root(want to be sure). I made a user(me), only thing I have installed is WOW and Guild Wars(using Wine) and Mplayer through add/remove and a Neverwinter nights install on Linux(not wine). Am I using ROOT I dont even know, how n00bish is that?

Please advise

If you are starting the computer and logging in as your username, you are not running as root. Yes, there are programs that run as root, but they are system programs that require such. The comment "don't run as root" refers rather loosely to users not running programs such as Firefox or Nautilus (unless expressly desired) as root.

The user "root" has full command of the filesystem, and damage can be done quite easily for those who are unaware of the power that root commands. Experienced users have an entirely different take on using root, but since your question was about new users, I recommend you heed the advice and not attempt running as root.

HTH

---

### Post by 73ckn797 on 2009-01-19
> **S0m3th1ngw13rd said:**
> Here is a new to Linux question for someone.  I keep reading on this forum and webpages around the web, to not run anything as root.  Understanding that this can open holes and what not in my security. I don't think I'm running anything as root not sure though.  How do I know I'm not running as root(want to be sure). I made a user(me), only thing I have installed is WOW and Guild Wars(using Wine) and Mplayer through add/remove and a Neverwinter nights install on Linux(not wine). Am I using ROOT I dont even know, how n00bish is that?

Please advise

I believe that if you were running as root you would not be prompted when entering Synaptic or certain other areas where changes can take place.

---

### Post by zmjjmz on 2009-01-19
Entering ```
 ps -U root
``` in a terminal will show you what processes are running as root.


Most of what you'll see has not been started by the user, and is part of the system.

---

### Post by S0m3th1ngw13rd on 2009-01-19
Ok good to know. I have used sudo like this once before.


> wget [http://kde-files.org/CONTENT/content-files/41569-wow-icon-scalable.svg](http://kde-files.org/CONTENT/content-files/41569-wow-icon-scalable.svg) -O WoW.svg
sudo mv WoW.svg /usr/share/pixmaps/
gksudo gedit /usr/share/applications/wow.desktop

Used this to make a shortcut for WOW on desktop/ Also have picked up a couple of books.  Linux in a nutshell - A desktop quick reference   and
Linux Bible from the local library. To help educate myself with Linux.  Also when I open Synaptic Package manager it does prompt for password. 

Thanks for info

PS: how do you get the little box around code that says
code:

---

### Post by DariusS on 2009-01-19
when you are in the reply screen area, there is an option at the top that looks like an #. that puts the code tags on text. alternatively, you could just type ["CODE"] your code here ["/CODE"] without the quotes.

---

### Post by illurim on 2009-01-19
I'm no expert, so please don't take my words as gospel. But, you can check what user you're running things as by opening up the System Monitor - I'm not at home, so can't give you accurate directions - and it will show the user.

If you want to go to a command line you can open up a terminal window and type in "ps -ef | grep wine" for example, which will show you any processes with "wine" in the name. This should tell you what it's running as.

In general you will always be asked to run things with your administrator (pops up password, unless you elect to save password) privileges (though I think the administrator privileges are different from the root user - a bigger geek can probably give you the ins and outs of it).

Anyway, hope I helped.

---

### Post by mrbiggbrain on 2009-01-19
what they mean when you shouldnt run as root, is dont do it unless you have to.

once day i was doing some clean up and was going to run

```
rm -r /mnt/lfs/nick-source/

```
which i had previously created a link to at /

and as we all do i made a mistake

i ran
```

rm -r /
```

now, becuse i wasnt running as root, the system said, sorry you cant do this. you cant just delete every folder in your whole file system! had i run as root, my whole install would be damaged.

for most of the averge day things your going to do, you dont need root privlages, and it will keep you from being a victim to dumb mistakes, i wasnt running as root ebcuse i didnt need to run as root to delete files i owned (as i had sudo chowned earlier) but linux caught my mistake (it didnt even know) and said, you cant do this.

---

### Post by mrbiggbrain on 2009-01-19
> **illurim said:**
> I'm no expert, so please don't take my words as gospel. But, you can check what user you're running things as by opening up the System Monitor - I'm not at home, so can't give you accurate directions - and it will show the user.

If you want to go to a command line you can open up a terminal window and type in "ps -ef | grep wine" for example, which will show you any processes with "wine" in the name. This should tell you what it's running as.

In general you will always be asked to run things with your administrator (pops up password, unless you elect to save password) privileges (though I think the administrator privileges are different from the root user - a bigger geek can probably give you the ins and outs of it).

Anyway, hope I helped.

i BELIVE (but might be wrong) and administrator is anyone who has sudo rights (not everyone does) so instead of being a root (as in always haveing full acess) they can for short times gain most of roots privliges.

---

### Post by Kellemora on 2009-01-19
Hi SW

First, let me Welcome you to the wonderful world of Ubuntu!

If you are coming from using Windows, you'll find that in Linux Security is job one!  This is why we are NOT plagued with viruses, trojans, worms, etc.  And because the default setting in Windows is for the Owner/User to automatically BE the Administrator of the system, most Windows user don't drop out of Administrator and just become a simple user.  Doing so would eliminate a LOT of problems.

Many Linux Distro's (That's short for Distributions) require a separate ROOT Password, a separate Administrator Password, and a User Password if desired.  Ubuntu has simplified all these passwords by letting the OWNER use a single password for both log-in and Administrative duties.  BUT, anything that requires Administrative Action will require that you Enter your password AGAIN to gain that privilege.  This way you basically cannot ACCIDENTALLY be running as Administrator without knowing it!

I feel Ubuntu is much more LOGICAL than many other Distro's, easier to learn (although it may seem strange at first).  The more you learn, the more you will appreciate the CONTROL you have over your own system.

One way of looking at Linux is like comparing the family sedan, complete with Automatic tranny and Idiot lights, To a Ferrari with a Stick Shift, full instrument cluster in the dashboard and a major power plant under the hood!  If you've never driven a Stick, it takes a little practice to learn.  Thus it is with Linux!  If you WANT the POWER and User Options found no where else, you climbed into the Right Machine!

And to avoid a LOT of Frustration, just remember, not every service center works on Muscle Cars or even knows how.  Parts for a Sunbeam are hard to find these days!  Or in plain English, manufacturers are still riding on Gates shirt tail and do not support the Linux community YET!  A few are coming out of the closet as Distro's like Ubuntu ROCK the #1 position and make some mighty big waves in the process.

It's easy to see how Ubuntu has taken over the #1 position in the Linux Community.  These Forums are a major contributor.  Help is available, often within minutes instead of weeks or months.

But when you consider the following, the issue almost seems MUTE:
The ultimate Spyware OS called Vista $319.95 - Ubuntu FREE
msOFFICE Ultimate $679.95 - Open Office FREE
PhotoShop C34 $699.00 - Gimp FREE
PhotoShop C34 Extended $999.00 - GimpShop FREE
AutoCAD $723.99 - QCAD FREE
Plus there are over 25,000 more FREE programs in Synaptic!

Just take your time to LEARN how things in Linux work, it really IS much more logical and SAFER!

If you are used to a program like msWORD, it was VERY HARD to learn.  Why is it so hard to learn, because it's NOT LOGICAL.
Let's say you want to do a Formatting job of changing the page margins.  WHERE is the command to do this in msWord?  Under FILE, where one would expect to find FILE operations, NOT Formatting operations.  So you HAD to HUNT to find it.  Over time you just remembered where it was.
In Open Office, Page margin settings are located under FORMAT/Page, right where it belongs.
Most things in Ubuntu and Linux are that way.  Stop and think WHERE is the most LOGICAL Place to look for something, and you will find it, RIGHT Where you EXPECT it to be!

But, to avoid Clutter, a lot of things are not loaded yet.  When the time comes you may want to use that feature, don't assume because you don't see it, it's not there.  It just was not loaded yet and you can load it yourself later as you become more proficient with using Linux and Ubuntu.  One learns by doing!

If you get stuck, don't hesitate to ask questions!

Good Luck and Enjoy!

TTUL
Gary

---

### Post by S0m3th1ngw13rd on 2009-01-19
> **illurim said:**
> I'm no expert, so please don't take my words as gospel. But, you can check what user you're running things as by opening up the System Monitor - I'm not at home, so can't give you accurate directions - and it will show the user.


Looked at System monitor and everything running there has my username under user. So good to go there. 

I'm a Linux newbie as I have deleted my windows installation entirely. Tired of the your AV solution will expire in 7 days, etc. And install this from MS update so you don't get comprimised by an unknown threat this, that, blah, blah, blah.

So thanks for the help all, I'll keep posting and learning.

---

### Post by 73ckn797 on 2009-01-19
> **Kellemora said:**
> I feel Ubuntu is much more LOGICAL than many other Distro's, easier to learn (although it may seem strange at first).  The more you learn, the more you will appreciate the CONTROL you have over your own system.


This is most certainly true. As you get into the system and learn your way around, you will really appreciate what you have before you.

Welcome to Ubuntu.

---

