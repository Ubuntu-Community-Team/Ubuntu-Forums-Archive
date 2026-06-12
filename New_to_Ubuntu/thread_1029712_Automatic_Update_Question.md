---
title: "Automatic Update Question"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by -kg- on 2009-01-03
Considering the number of issues I have read over time concerning this issue, I thought the Beginner's forum the appropriate place to post this question.

Over and over I have read posts that concerned people's installations being "broken" after applying some update or another, and replies basically saying that just because updates are offered (from the icon on the top launch bar in Gnome; from KDE and the others, I don't know where) that one should be wary and not just "apply them because they were offered."

Today, I noticed that I had updates available, so I launched Update Manager and read what they were.  I am completely unsure whether to install them or not, though I can well guess.  Screen shots of the Update Manager screen follow:

[ATTACH]98596[/ATTACH]

Notice from the screen shot that it is an AMD Video update to "help(s) users of the existing AMD driver to update their X.org setup."

[ATTACH]98597[/ATTACH]

Notice that the Geode Update is also for "AMD Geode GX2/LX video chipsets."

Instead of posting another screen shot of the description of the update, I'll just copy and paste them:

> Version 2.9.0-1ubuntu2.5: 

  * Stripped duplicated lines in debian/rules.
  * Enabled simple-patchsys.mk CDBS include in debian/rules.
  * Backported CS5535/GX2 and OLPC hardware support from 2.10.0 release.
    + Added to debian/patches/ and applied with simple-patchsys.mk
    Thanks to Bryce Harrington for thining the patch to the essentials!
    (LP: #255991)


Finally, [the bug issue.]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-geode/+bug/255991")

Now on my desktop, I could understand this patch.  It is an AMD64 3200+ Processor on an ASUS A8V Deluxe Motherboard (though I'm using an nVidea Video Card and have no idea if it uses a "Geode platform that use a CS5535 companion chip.").

But I have received this upgrade to my Toshiba Satellite A135-S4487 laptop, with an Intel Centrino processor with, I assume, an Intel Video chipset.

Now, I *do* have a slight issue with "monitor resolutions" on this laptop.  The maximum monitor resolution available on this laptop is 1280 X 800, while under Vista it was approximately 1280 X 1024 (if I remember correctly...it was definitely finer than 1280 X 800, and my desktop and windows are noticeably coarser than in Vista).

I wonder if I should apply these updates, and whether it might correct my monitor resolution issue?  I notice in the "xserver-xorg-video-AMD" Description it states:

> This transitional package helps users of the existing AMD driver to update their X.org setup. It can safely be removed after the upgrade is completed.
If you are using a static xorg.conf, edit the Device section and change the Driver value from "amd" to "geode" before purging this package.
In all other cases, you can safely purge this package immediately. 

Is this particular upgrade meant to be applied Universally to all who receive them, or only those who are or might be affected?  I have read many "Update-generated" problems in the Forums, and as such am reticent to apply this particular update until I know.

If these updates are specific to certain platforms, how does one go about determining whether they apply to one's system?  The messages usually supplied are deficient in this area, especially to a "Linux newbie," of which I readily admit I am one.

If some Automatic Updates are not meant to be Universally applied to all computers that receive them, it seems to me that there needs to be a better way to differentiate between what are critical, global updates that need to be applied by all and those that are specific to a platform, or to several (but not all) platforms.

Considering that Ubuntu tries to appeal to Windows users who would like to switch from Windows to Linux and is seemingly high in popularity for those doing so, there will naturally be a large number of us who will be in the "newby" category, at least for a time.  There will also be a large number who will never reach the level of "Master Linux Guru," desiring instead to just "run Linux as an OS" and have the OS be as transparent as possible.

While the above is not entirely possible (and I suspect that is why so many Windows installations suffer, as well...I personally can keep a Windows installation relatively healthy for a long time, but it takes attention and knowledge), there needs to be some notation, education, or process in place that will enable users to make informed decisions when applying non-critical, platform-specific updates to their systems.

As a side note: I also realize that Ubuntu is developed and maintained largely by unpaid volunteers and those in the community at large who have the knowledge and ability.  I also realize that implementation of my ideas might be more work-intensive than I might realize.  I appreciate everyone's efforts, and will volunteer some of my time, as time and my (ever-increasing) knowledge permits.

Thanks all!! =D>

Now, should I apply these updates or not, and how can I determine this in the future (if answerable!)?

---

### Post by Michael.Godawski on 2009-01-03
hi,

concerning if you should install the updates no idea:P
but concerning your idea:

You might post it on ubuntu brainstorm. The chances are greater there that you cry is heard by the developers. :D

[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by -kg- on 2009-01-03
> You might post it on ubuntu brainstorm. The chances are greater there that you cry is heard by the developers.

It is done, and thanks for the suggestion.  I didn't know that particular subsection of the site existed.  I made a short proposal in my suggestion and linked it to this thread.

---

### Post by laceration on 2009-01-04
Good questions that I have often wondered about.  Like why do I need this? and I am just loading dead weight?  What it always comes down to is if I didn't install I would still have that pesky icon in my notification area:P.

Another suggestion--you might take this to the community cafe forum and ask people what they do with updates and why.  That would be interesting and this might get more traction there.

---

### Post by -kg- on 2009-01-12
Bump.

The aforementioned updates are still sitting up in the notification area, and though I haven't installed them yet, I have installed other updates that have come down the pipeline since then.

I'm still not sure whether to install them and what the installation would entail.  Of particular concern is the following:

> This transitional package helps users of the existing AMD driver to update their X.org setup. It can safely be removed after the upgrade is completed.
If you are using a static xorg.conf, edit the Device section and change the Driver value from "amd" to "geode" before purging this package.
In all other cases, you can safely purge this package immediately. 

Why would one need to purge this package, and how is it done?  How can I tell whether I am using a static xorg.conf, and where is this setting for the "Driver value" that I would need to change?  Obviously, it isn't in my path, because I can't pull a "cat" command on it directly.  I assume I would have to know it's path.

And as an update...this patch *was not* sent to my AMD 64 desktop computer.  I will assume that this is because I'm running the 64-bit version of Ubuntu, but why would that have anything to do with these packages or xorg?

I don't mind applying these packages as long as I know if and what I need to do after applying them (and knowing *if* I even need to apply them would be nice).

Thanks in advance for any help.

---

