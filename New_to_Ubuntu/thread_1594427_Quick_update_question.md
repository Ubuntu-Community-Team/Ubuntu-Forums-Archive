---
title: "Quick update question"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by h8uthemost on 2010-10-12
Everytime a new release comes out I always do a fresh install. Download the update, burn it to disc, format my drive and install.

But everytime I do I have to reprogram my browser. Mainly the most annoying part is putting in all my passwords/form info for the first time.

So my question is, take Chromium for example. If I backup my chromium folder that is located in my home/.config directory, and use that on my fresh install, would I get a browser that still has all my passwords and cookies that I was using before I updated?

Just wanted to make sure about this before I go ahead and update.

Thanks for any help.

---

### Post by migs73 on 2010-10-12
Next time you re-install, set /home on its own partition, then you only need to reinstall the / partition for the new OS. This will also mean all your settings are retained.

---

### Post by h8uthemost on 2010-10-12
Well, the thing is, I liked wiping my hard drive and installing clean. Everything just seems so extremely fast again when I do it that way. So that's why I like to do it clean rather than updating through the OS.

Actually, when I used to use Ubuntu, the OS would slow down pretty dramatically within a couple weeks of install. Now that I use Lubuntu(and I've been using it for I think a couple months now, or maybe a little less) I haven't noticed any slow down at all. So I guess I really don't have to update like this anymore. But still, I'll do a fresh install one more time. If I don't notice Lubuntu to be any faster, then I'll just update through the OS from now on(well, as long as I stick with Lubuntu, which I think I will indefinitely, the *distro* is just that good).

So anyways, I'm guessing as long as I backup my browsers profile folder and use it on the fresh install I'll retain all my settings?

Thanks.

---

### Post by pricetech on 2010-10-12
> **h8uthemost said:**
> So anyways, I'm guessing as long as I backup my browsers profile folder and use it on the fresh install I'll retain all my settings?

Thanks.

That's the way it's supposed to work.  You might want to back up any folders the browser creates before you overwrite just in case.

---

### Post by h8uthemost on 2010-10-13
^ Yep, I just tried it on my current install. I backed up the chromium to my desktop, uninstalled then reinstalled chromium(also deleted the chromium folder from .config), then placed the backed up folder back into .config, and all my settings are still there.

Can't believe I didn't think of this sooner. With each clean install I had to reprogram my browser.

---

### Post by HermanAB on 2010-10-13
As remarked above already, make a /home partition.  It also makes it a snap to do backups if /home is separate.

---

### Post by h8uthemost on 2010-10-13
I'm not exactly sure what that means, making a /home partition. I thought he was talking about just updating through the OS. But the more I thought about it, that's not what he meant.

So I'm not exactly sure what that is.

---

### Post by migs73 on 2010-10-13
> **h8uthemost said:**
> I'm not exactly sure what that means, making a /home partition. I thought he was talking about just updating through the OS. But the more I thought about it, that's not what he meant.

So I'm not exactly sure what that is.

I'll try to clarify;
When you do an install, if you use the advanced option, instead of the 'use the entire drive', you can then set up different partitions. The option I am talking about would be to have a swap partition (about 1.5 times the size of your RAM), a root partition for the OS (size dependant on the amount of programs you will install, but 20GB should suffice), and a home partition (the rest of the drive).
This way when you want to upgrade the OS you can wipe the root partition and reinstall to it without touching your settings in the home partition.
Hope this helps.

EDIT see my HDD set up below. NB I have two 30GB root partitions, one for Lucid and one for Maverick.

---

### Post by h8uthemost on 2010-10-14
Ah, I never thought about something like that. That's pretty cool, migs73. Thanks for explaining it to me. When I do my reinstall I'll set my HD up like you said(I only have a 80GB internal, so I hope that will suffice).

So after I set up a /home partition on this next install, the *next* time I would do a reinstall, how exactly would I do it? On the installer, instead of using entire disc, pick the partitioning method, and just reinstall to the root partition? I won't have to do anything to the home /home partition?

Thanks for the help.

---

### Post by migs73 on 2010-10-14
> **h8uthemost said:**
> On the installer, instead of using entire disc, pick the partitioning method, and just reinstall to the root partition? I won't have to do anything to the home /home partition?


Yes! You tell it where the /home partition is but tell it NOT TO FORMAT it.

---

