---
title: "Desktop not functioning on 10.04.1"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by Kellemora on 2011-01-21
Hi Gang

I'm in the process of installing version 10.04.1 32 bit on my computers.

Hit a snag on my newest computer.

Nothing appears ON the Desktop and Right Click does not function ON the Desktop....

Both of these functions work perfectly and as expected on an identical computer, both are Asus MoBo's only difference between the two computers is the Dual Core CPU, Both are Athlon X2, but one is 2.5 gig, the other is 3.0 gig.  Other than that, they are supposed to be identical.

If I open a remote folder on the other 10.04.1 it appears ON the Desktop and requires being Unmounted after I've finished.

On this newest computer, if I open a remote folder, it does NOT appear on the Desktop and I must go to PLACES to Unmount it.

I can't find a setting anywhere that would control this?????
And since I installed 10.04.1 to both computers from the same CD and updated everything, seems they should work the same.

Summary:
Folders DO NOT appear on the Desktop, although they do appear in the Folder named Desktop.....
Right Click does NOTHING when performed ON the Desktop itself.....

Any Ideas Gang?????

TTUL
Gary

---

### Post by JKyleOKC on 2011-01-21
This may or may not be any help; I'm using Xubuntu rather than Ubuntu, and the menus are rather different.

However on my settings menu there's an option for configuring the desktop, and it offers two possibilities. One is to show currently running processes and the other is to show selected devices. My file manager is Thunar while yours is probably Nautilus. If yours has similar configuration possibilities, compare them between the two machines. From your description I'd bet that they are set to different choices, and making them the same would solve the problem.

---

### Post by Kellemora on 2011-01-21
Thanks for the reply JKyle!

I've tried ALL the meager suggestions I could find on LaunchPad between 2008 and 2010.....

I've deleted Nautilus and Gnome and reinstalled.
Cleared several files that were suggested to clear.

This is a clean fresh install, I've not fiddled with anything yet!
And as I said, on two identical computers.....
There is supposed to be a GConf file somewhere, which checkboxes to show Desktop on the Desktop, but if so, I've not been able to find it.

But, installing from the same CD on two virtually identical computers, should NOT produce two so drastically different installs.  There are considerable differences besides this one I must get resolved.

As an aside:  Version 8.04 64 bit & 32 bit, install perfectly and work perfectly right out of the box.
I've spent hundreds of hours TRYING to get version 10.04 to work, to no avail.  Waited until 10.04.1 came out.  Same problems!  We finally got it partially working on only the latest computers, but it was crashing every half hour or so.  After weeks of research, I finally ran across a couple of work around bug fixes and got it running without crashing.

So, I decided, before 8.04 runs out of time, to get 10.04.1 going on as many computers as I could to make an attempt at getting at least a small percentage of the vast amount of BUGS in this version worked out.

I've said this from the beginning, when version 10.04 first released.
They NEED to dump it in the TRASH CAN and improve 8.04 which is almost near perfect and always has been.

Ubuntu is what brought me back to Linux, besides Vista driving me away from the Doze of course.....

Now Ubuntu is DRIVING me away from them because they can't seem to produce a functional OS since 8.04.....

On ALL of the machines where 8.04 runs perfectly, 10.04 runs on NONE OF THEM, yet Debian 5 installs and runs perfectly....
All I can say is what did Ubuntu DO to louse up such a good OS?????

Of all of the problems with 10.04 and 10.04.1 I've asked about solutions for, to date, maybe only one has been forthcoming that worked to solve a problem.

Sad, really sad!!!!!

I can see the headlines now, once 8.04 is no longer supported.
The Late Great Ubuntu OS bit the dust!

Since April of 2010, we have yet to get 10.04 working here on ANY of our machines properly.  Whereas 8.04 runs perfectly on all of them, right out of the box!

WHAT WENT WRONG WITH UBUNTU?????

TTUL
Gary

---

### Post by JKyleOKC on 2011-01-21
I also found 8.04 much more to my liking, but after getting invaded (through a series of stupid mistakes on my part that let the invader gain root access) and consequently having to nuke and pave my whole LAN decided to come on to Lucid to get an additional 3 years of support. Like your case, it has never worked perfectly but with a few weeks of intense tweaking I got it to function close enough to be usable. I still have a couple of issues (mentioned on another thread in General Help that I just started today) but no deal-killers any more.

I agree that two installs on absolutely identical boxes from the same CD should not have any configuration differences, but if the boxes have any hardware differences at all this may no longer be true. The reason is the automatic configuration that they add more of with every upgrade. Their goal is to totally remove the need for any manual tweaking -- but that also makes it almost impossible to do any tweaking that might be required! For example, it took me nearly a week of trying to get my 1440x900 LCD display to operate at any resolution above 800x600. The automatic stuff would override my manual tweaks! Fortunately, Lucid can still override the automatic stuff if you manually create an /etc/X11/xorg.conf file -- but I understand that this is going away before long.

And I still cannot get a full scrolling report of what's going on during boot time. Only a few lines show, then the screen goes black for a while, then a few more lines, and the GDM background pops into view.

If Debian works properly for you, why don't you switch over and let Ubuntu continue to appeal to what seems to be their target audience? I'm seriously considering doing so myself, now that Ubuntu has taught me how to live in the Debian-based world (I started with Slackware 2, moved to Mandrake at its 8.1 version, and came to Xubuntu at Fiesty 7.04)...

---

### Post by Kellemora on 2011-01-21
I hear ya JK!

I forget all the various Linux distro's I tried way back when they first came on the scene.
I was (and still am) a far cry from a computer buff, even if I have several of them in use right here in front of me.
Once I get them humming properly, I forget how to do things, so have LOTS and Lots of notes I keep on things.

I was messing around with CentOS because I was around RedHat a little bit.  Not enough to learn anything useful, but I figured some help was just down the hall, at the time.  That didn't pan out as they only handled server chores and that was about it.

I heard some good things about Ubuntu and gave it a whirl.
Took a few days to even figure out which one to download and try.
I lucked out I guess and chose 8.04 64 bit and it worked perfectly, only a few new user questions and some minor problems I probably caused.
And then there is the Hardware Issue, which has NOTHING to do with Ubuntu!

I have convinced at least 25 to 30 friends to switch to Ubuntu and they in turn probably convinced just as many if not more themselves.  Thanks to how GREAT version 8.04 really was.

I just don't understand at all why they would keep going down different avenues when they had such a good thing going.

I always thought the in-between releases were like tests of new things they were going to add to the main package after the bugs were worked out.
But now that I've been around awhile, it appears its just the Ubuntu way to keep coming up with something different.

But to call 10.04 an LTS Stable Release when it's probably their worst disgrace of an OS program yet, just boggles my mind!

If it were not for these Forums, and 8.04 being such an awesome OS, I would probably not have finally deleted all or most of my XP programs.

I even tried Edubuntu to see how servers work and some of their lighter distro's, but nothing holds a candle to 8.04.....

You have a nice evening!

TTUL
Gary

---

### Post by NightwishFan on 2011-01-22
More often than not issues with hardware have to do with the upstream projects and not just Ubuntu. Why not research the individual projects you have problems with?

---

