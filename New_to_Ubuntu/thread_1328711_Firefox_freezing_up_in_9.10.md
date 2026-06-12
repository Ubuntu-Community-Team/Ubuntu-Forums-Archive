---
title: "Firefox freezing up in 9.10"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by pelee98 on 2009-11-16
My machine is locking up a hell of a lot more than any windows machine ever did.

Every time I use Firefox 3.5 everything except the pointer on the screen locks up within a short time.  No key board.  No mouse buttons.  Nothing.

It is not related to the site.  It will happen at any site I visit.  The time it takes till lock-up will vary from 2 minutes to 90 minutes.

It will stay locked for hours if I walk away.  The only fix is to force the power off and restart.  NOT COOL!!

I have tried un-installing Firefox and re-installing.  Made it worse.

Anyone else having this problem?  This is maddening.  If I could afford another copy of windows right now, I would walk away from Ubuntu today!

Do I need to wipe the hard drive and start over?

Help!

---

### Post by Jon Monreal on 2009-11-16
> **pelee98 said:**
> My machine is locking up a hell of a lot more than any windows machine ever did.

Every time I use Firefox 3.5 everything except the pointer on the screen locks up within a short time.  No key board.  No mouse buttons.  Nothing.

It is not related to the site.  It will happen at any site I visit.  The time it takes till lock-up will vary from 2 minutes to 90 minutes.

It will stay locked for hours if I walk away.  The only fix is to force the power off and restart.  NOT COOL!!

I have tried un-installing Firefox and re-installing.  Made it worse.

Anyone else having this problem?  This is maddening.  If I could afford another copy of windows right now, I would walk away from Ubuntu today!

Do I need to wipe the hard drive and start over?

Help!

Sounds very odd.

Try going to a terminal, typing in "firefox -safe-mode" and when the next window comes up, click "Continue in Safe Mode". Then, see how Firefox works in Safe Mode.[LEFT][/LEFT]

---

### Post by kansasnoob on 2009-11-16
Random hard-freezes have always been on par for me with Karmic:

[http://ubuntuforums.org/showthread.php?t=1276146](http://ubuntuforums.org/showthread.php?t=1276146)

It comes and goes!

---

### Post by winotree on 2009-11-16
I can't help with your current issue but would like to comment, if I may, on something you said.
> ....I have tried un-installing Firefox and re-installing.... Un-installing Firefox *does nothing at all* unless you remove its configuration files found in /home/user/.mozilla  

[Just saying...]

---

### Post by kansasnoob on 2009-11-16
Honestly, I'd install either 9.04 Jaunty or 8.04 Hardy!

Both are very stable!

---

### Post by pelee98 on 2009-11-16
> **kansasnoob said:**
> Honestly, I'd install either 9.04 Jaunty or 8.04 Hardy!

Both are very stable!

This problem started in 9.04.  I upgraded hoping it would solve the problem.

---

### Post by pelee98 on 2009-11-16
> **Jon Monreal said:**
> Sounds very odd.

Try going to a terminal, typing in "firefox -safe-mode" and when the next window comes up, click "Continue in Safe Mode". Then, see how Firefox works in Safe Mode.[LEFT][/LEFT]

OK did that.  Firefox opened.  Got the following message repeated in the terminal a whole bunch of times:

"(firefox:2839): Gdk-WARNING **: XID collision, trouble ahead".  Any thoughts on that?

---

### Post by Jon Monreal on 2009-11-16
> **pelee98 said:**
> OK did that.  Firefox opened.  Got the following message repeated in the terminal a whole bunch of times:

"(firefox:2839): Gdk-WARNING **: XID collision, trouble ahead".  Any thoughts on that?

Have you updated everything lately? Also, does Firefox still open despite that, and if it does, does it work well? It appears that this is a [bug]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823"), but I'm not convinced that it's related to your larger problems. Updating everything might help.

---

### Post by kansasnoob on 2009-11-16
Post the output from terminal of:

```
sudo firefox -v

```

---

### Post by pootan on 2009-11-16
There seems to be a fix coming for this error. From what I can gather the error message is what could be slowing you down. 

Take a read through here and in particular the most recent. 

[URL="https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823"]https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823
[/URL]

PS: also you might consider right clicking your panel add to panel>force quit then click add temporarily.

---

### Post by pelee98 on 2009-11-16
> **Jon Monreal said:**
> Have you updated everything lately? Also, does Firefox still open despite that, and if it does, does it work well? It appears that this is a [bug]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823"), but I'm not convinced that it's related to your larger problems. Updating everything might help.

Everything is updated.  I do so daily.

It opened but does not work well.  I've lost the use of my bookmarks.  I still see them, but can't use them.  Didn't leave it open long enough for a freeze-up.

---

### Post by pelee98 on 2009-11-17
[QUOTE=pootan;
PS: also you might consider right clicking your panel add to panel>force quit then click add temporarily.[/QUOTE]

I've already done this.  It doesn't work because everything is frozen.  I can move the arrow over it, but I can't click it.

---

### Post by Sir Jasper on 2009-11-17
Hi,

Have you tried, System Monitor > Processes > firefox > End Process

I just wonder if an add-on may be causing the problem.

I am using 3.0.15 in Xubuntu but 3.5.5 (portable and installed) versions work well in Wine 1.0.1. with Wine default configuration as XP. Just in case it may be a temporary solution.

My regards

PS I have not reread all of this thread, my memory is not great and I am no expert.

---

### Post by pelee98 on 2009-11-17
> **kansasnoob said:**
> Post the output from terminal of:

```
sudo firefox -v

```

------@Linux:~$ sudo firefox -v
[sudo] password for ------: 
Mozilla Firefox 3.5.5, Copyright (c) 1998 - 2009 mozilla.org
------@Linux:~$

---

### Post by pelee98 on 2009-11-17
> **Sir Jasper said:**
> Hi,

Have you tried, System Monitor > Processes > firefox > End Process

I just wonder if an add-on may be causing the problem.

I am using 3.0.15 in Xubuntu but 3.5.5 (portable and installed) versions work well in Wine 1.0.1. with Wine default configuration as XP. Just in case it may be a temporary solution.

My regards

PS I have not reread all of this thread, my memory is not great and I am no expert.

OK the freezing up prevents me from doing anything.  I have no keyboard control.  I have no ability to click on anything with the mouse.

---

### Post by d4ndy on 2009-11-17
I've been having the same problem since upgrading to 9.10 and FF 3.5. I almost think I can do something about it, because the pointer is still responsive, but everything else is frozen. I can't even change focus to another app.

(Possibly related: scrolling in Firefox 3.5 has become a nightmare: once I scroll past the initial display, the rendering becomes what you might call "smeared," and the only way to fix it is to skip over to another tab and then back.  But then, when I start to scroll again, it becomes smeared and illegible again.)

---

### Post by Jazzy_Jeff on 2009-11-17
You stated that you upgraded from 9.04. I would recommend backing up your important files and doing a clean install. That may fix all your problems. Just a thought.

---

### Post by pelee98 on 2009-11-17
> **Jazzy_Jeff said:**
> You stated that you upgraded from 9.04. I would recommend backing up your important files and doing a clean install. That may fix all your problems. Just a thought.

This is my last resort.  Will a clean install overwrite what I have now, or do I need to wipe everything off the hard drive?  How do I wipe out the hard drive.

I know that's a really noob question, but I'm barely literate with this stuff.  An out-of-town friend helped me with the initial install while visiting.

---

### Post by Jazzy_Jeff on 2009-11-17
When you go to do the install your harddrive will be wiped. Just install from the Live CD and choose your Ubuntu partition.

---

### Post by d4ndy on 2009-11-17
A little progress report: I tried installing Galeon, in hopes of riding out the storm for a week or two or three, till the bug was hunted down & squished. Seemed to be working okay -- it's a nice browser. Then everything froze but the cursor/pointer, exactly the same as with Firefox. Do Galeon and Firefox use the same engine?

On the other hand, right now I'm in Firefox, and that smear effect I mentioned earlier is not (yet) in evidence.

I'm thinking maybe a nice clean re-install of 9.10 onto a wiped HD might be just what I'm looking for. (Don't forget to back up all those deps you've downloaded since the upgrade!)

---

### Post by pelee98 on 2009-11-18
> **d4ndy said:**
> A little progress report: I tried installing Galeon, in hopes of riding out the storm for a week or two or three, till the bug was hunted down & squished. Seemed to be working okay -- it's a nice browser. Then everything froze but the cursor/pointer, exactly the same as with Firefox. Do Galeon and Firefox use the same engine?

On the other hand, right now I'm in Firefox, and that smear effect I mentioned earlier is not (yet) in evidence.

I'm thinking maybe a nice clean re-install of 9.10 onto a wiped HD might be just what I'm looking for. (Don't forget to back up all those deps you've downloaded since the upgrade!)

I've used firefox for a few hours without a freez-up today.  Anyone know if the bug has been squashed?  Did I download the fix with my daily updates without knowing it?

BTW d4andy, I've been using Opera without freez-ups all along.  I just don't like the fact that it won't work with xmarks so I can't keep it's bookmarks synchronized.  It also won't play some video.  Thus, it won't be my primary browser.


Update:  Frozen again.  Could it be scroll wheel related?  Strange that it only happens with firefox though.

---

### Post by d4ndy on 2009-11-18
I guess I've been trying to use the browsers available in the repositories, but I've used Opera before, and like it. However, like I said, I was just looking for a port in the storm when I installed Galeon.

As it turns out, Galeon does use the Gecko engine, same as Firefox.
Could this be the weak point in common? I'll try Midori (WebKit engine & XFCE goodie), and see how that works for me.

BTW, Galeon worked just fine for a few hours too, before it froze up. Seems to be an accumulative weakness. If I knew what I was talking about, I could start babbling about "overruns" and such.

(Below the surface, I'm thinking the long weekend coming would be a good time to re-install and troubleshoot, if things don't improve.)

---

### Post by ArinSky on 2009-11-18
This can also be caused by some of the open source flash players being installed like gnash or swfdec... try this:
```

sudo apt-get remove flashplugin-* --purge
sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
sudo apt-get install flashplugin-nonfree

```

---

### Post by pelee98 on 2009-11-19
> **ArinSky said:**
> This can also be caused by some of the open source flash players being installed like gnash or swfdec... try this:
```

sudo apt-get remove flashplugin-* --purge
sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
sudo apt-get install flashplugin-nonfree

```

Done.  Froze up watching Hulu.com this morning.

---

### Post by raublekick on 2009-11-29
Phew... haven't posted in a long time. Any more word on this? I have been intermittently been having these problems since I clean installed 9.10. 

Generally it seems to happen when trying to invoke the screensaver, or whatever the default behavior is because I haven't changed the default behavior. I keep the System Monitor applet on my panel. As an example, this is what I saw last night:

I came home after several hours to find my screen on, bright, and certainly not in a screensaver or with the screen turned off. One of my CPU cores was at 50 or 100% usage and both Firefox and Pidgen were in the grey locked up state. As usual nothing worked and I had to hard power off the machine. 

I have been noticing it unable to come out of a sleep state as well. Just a black screen that won't wake up. Very rarely has it happened while I am actively using the machine. 

The really scary thing is what sometimes happens after these lockups. It is rarely as simple as rebooting and being on my way. I get errors on disk checking at boot time and I have to run fsck to fix them. This machine is only a year old and I have had no issues until I installed Karmic. I would not rule out a hardware problem but given the amount of people experiencing similar things... I'm counting on something else.

Machine info:
Ubuntu Karmic
Lenovo Ideapad
Intel graphics (sorry not sure which right now)
Intel wireless
Intel core duo processor

---

### Post by Lyleb on 2009-11-29
I doubt it's a hardware problem. I also get frequent freezes since I installed 9.10. Mostly happens when running FireFox, but also with Thunderbird. Haven't used OpenOffice much yet so don't know if that will cause it too.

This computer has run Ubuntu 8.04, 8.10, 9.04 with absolutly no similar problems. I haven't found much in the way of a solution, just a lot of try this, try this, maybe this...

My plan is to re-install 9.04 when I get a chance and just wait for 10.04. Maybe give Fedora a try in the meantime. Been a while since I used that.

---

### Post by pelee98 on 2009-11-30
Hey everyone.  I started this post a while back.  I've had no solutions suggested yet.  

I had been convinced that this had something to do with the flash plugin, but I'm no longer convinced.  I did a complete reinstall of 9.10.  I started using Firefox and it just froze up again.  Flash based sites seem to make it happen more frequently.  Also, it does seem to be exacerbated by the scroll wheel, but I'm not sure of that either.

It has been suggested to me that I don't have the video card/driver configured right (another post).  I don't know if that's an issue for anyone else.  Anyone have thoughts on that?  I'm not sure how to go about that fix.  I don't even know what video card I have in this machine - it's 8 years old.

Verision 9.04 is where my problems started.  Anyone use Linux mint?  Does that have the same issues?  I'd really like to go to flash based web sites.  My kids use this machine to watch PBS shows and that is dependant on Adobe flash.

---

### Post by raublekick on 2009-12-03
I've been doing my own experiment. Haven't had my laptop freeze since I posted in this thread until last night. 

Since everyone seems to think Firefox and Flash have something to do with the problem, I stopped leaving Firefox open. Generally I leave Firefox and Pidgin open at all times. Keeping Firefox closed seemed to keep the freezing at bay, until last night.

The only variable with last night's instance is that I left Banshee open. And come to think of it, I probably had Banshee open every time it froze. Obviously this is not proof perfect but maybe it is a hint. I have Banshee set to monitor my files for new music, but it doesn't seem to really work, and maybe that is more of a hint.

Is anyone else using Banshee, Rhythmbox, or any other music player like that? Even more is anyone the app monitor their files?

---

### Post by Lawcheehung on 2009-12-03
man I'm not the only one experiencing these problems, I thought it my usb mouse at first, but I've ruled that out...I think the problem is dependent on your computer, there's always one little component that messes things up - but it also may be firefox's flash or java or something...:(

---

### Post by pelee98 on 2009-12-06
> **raublekick said:**
> I've been doing my own experiment. Haven't had my laptop freeze since I posted in this thread until last night. 

Is anyone else using Banshee, Rhythmbox, or any other music player like that? Even more is anyone the app monitor their files?

Rythmbox is installed, but it's almost never open during my crashes.  Had two crashes this morning so far with just gmail (or it's calender) open.  As far as I know, gmail doesn't use flash, so maybe it just firefox that sucks.

This is really horrible.  It's enough to make me think about going back to Windows - but I don't have the money.  I don't exactly have a speedy system (1.7 ghz with 1 gig ram), but Ubuntu should be able to cope.

Anyone here have any experience with other linux versions - Suse, redhat, etc?  Do they have the same problems?

---

### Post by ScottinSoCal on 2009-12-06
I've been having the same problem for a few days - I'd be browsing and everything would lock up. I'd have to fiddle with it for a while to get anything to respond again. Yesterday my HDD crapped out. Fortunately, I'd already bought a new one. Clean install of 9.10, and it's working 100% so far. No lock ups, and it's running a little faster. I guess the HDD was failing and giving me read errors.

The SMART HDD monitor was warning me that my hard drive was failing, but I chalked it up to the bug already discovered. It wasn't.

---

### Post by PinchedNerve on 2010-04-19
> **ArinSky said:**
> This can also be caused by some of the open source flash players being installed like gnash or swfdec... try this:
```

sudo apt-get remove flashplugin-* --purge
sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
sudo apt-get install flashplugin-nonfree

```
You have no idea how happy I am I found your post. Thank you sir!  I was having flash issue & this cured me.

---

### Post by pelee98 on 2010-05-15
Well, Here's what I think has happened.

This is a bad hard disk.  It just must have had a bad spot where firefox was installed.  

I did a full reinstall and now firefox works fine, but the screensaver now causes crashes.

This make sense to anyone else?

---

