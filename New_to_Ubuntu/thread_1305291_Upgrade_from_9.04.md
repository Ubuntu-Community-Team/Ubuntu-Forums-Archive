---
title: "Upgrade from 9.04"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by bigal1932flying on 2009-10-29
I have downloaded "karmic-desktop-i386.iso" to my Desktop.
How do I upgrade from 9.04 without harming my system?
When I upgraded from 8.10 to 9.04 I was able to do so using the command line "sudo mount -o loop ~/Desktop/" plus name of iso file. But I don't seem to be able to do this now. 
Can anyone tell me how to upgrade from the .iso I have?

---

### Post by Rocket2DMn on 2009-10-29
You don't need the .iso image to upgrade, you only need it for a clean install.  If you go to System->Administration->Update Manager and click "Check", it should prompt you at the top of the window that a new release is available.  You can click Upgrade to get it.

---

### Post by paynek716 on 2009-10-29
In my short time on the forum, I have seen conflicting opinions, update vs. backup /home and install new version. Moving from 9.04 to 9.10 will be my first Ubuntu upgrade. What say ye?

---

### Post by LowSky on 2009-10-29
upgrade works fine for most users, the ones who get left in the cols are people who rely on odd technology or proprietary drivers.

I've upgraded and it works fine in every version I've used.

---

### Post by MrWES on 2009-10-29
> **paynek716 said:**
> In my short time on the forum, I have seen conflicting opinions, update vs. backup /home and install new version. Moving from 9.04 to 9.10 will be my first Ubuntu upgrade. What say ye?


I have a separate /home partition and the first few versions I only did a fresh installation. However, I figured since there was an 'upgrade' option, why not give it a try? So the last couple of versions I've done just that; upgraded and skipped the fresh install -- I haven't had any issues. 

Bill

---

### Post by Xero Xenith on 2009-10-29
I upgraded, and had only one issue - my Japanese keyboard input is no longer available on my English install.

However, something tells me this is a minority issue... :P

---

### Post by dummy910 on 2009-10-29
I've completed several 9.10 upgrades already here today, _all with out a single hiccup_(as usual, it's Ubuntu after all).

I downloaded the 9.10 **Alternative** .iso, burned it out to both a cd-r and a thumb-drive. Mounted either of these mediums, and ran the following right from the 9.04 desktops.

I opened a terminal to where I mounted the medium and typed:
> gksudo ./cdromupgrade_and every machine upgraded with a problem_. 

Some machines will probably have to download some extra files, depending on how much extra software(ubuntu-studio etc).

In short, _upgrading is painless_. _I've been using the upgrade method in Ubuntu for years now, every single one with no problems_ outside of having to download a driver(hardly a problem) - it's simple stuff here folks.

My experience tells me that the folks who always have problems with their computer, because they bork settings, are always the one's who have problems upgrading, beit windows, ubuntu, mac etc. A lot of folks know just enough about computers to be dangerous ;)

[COLOR=red]Before Upgrading:[/COLOR]
Make sure your system is totally up to date, and of course use a thumb drive(or other medium) and back up your home directories before ever attempting any upgrade(you should be back this stuff up every-so-often anyway).

---

### Post by acreech on 2009-10-29
I have not upgraded yet, but I wondered if during the upgrade I could change from the ext3 partitions to the ext4 partitions or if I would have to do a clean install in order to change file formats.

---

### Post by &lt;NateTheGreat&gt; on 2009-10-29
When upgrading using the update manager, do you lose all your data on the current your Ubnuntu release? (9.04)

---

### Post by acreech on 2009-10-29
If it goes right you should not lose any files, but it is always best to backup anything that you would want if you do lose it.

---

### Post by humphreybc on 2009-10-29
Upgrade is designed to be a smooth process, if it wasn't, they wouldn't have the feature.

When upgrading, try to get a stable internet connection (such as a wired, not wireless), and if you have a laptop, make sure it's plugged in - so it doesn't run out of juice.

Upgrading is the way to go for most people, but a fresh install can be beneficial if you want new features, such as ext4 by default, grub2 and an encrypted home directory.

If you are going to upgrade, backup your home directory entirely (ie, press ctrl + h and highlight all the hidden files too). Then once you re-install, you can copy across your home directory to the fresh install. This won't save your installed programs, you'll have to download them again, but it will save the configuration files to your programs, and also should save your appearance settings for the desktop.

Either way, even a very complicated desktop setup with lots of programs only takes a couple of hours to set up from scratch again on Ubuntu, provided you know what you're doing :)

---

### Post by humphreybc on 2009-10-29
> **acreech said:**
> I have not upgraded yet, but I wondered if during the upgrade I could change from the ext3 partitions to the ext4 partitions or if I would have to do a clean install in order to change file formats.

It is possible to change your file system after install, but the only problem is that only things written to the disk **after** the time you switched to ext4, will actually be in ext4.

There are some tutorials around the internet on how to do this, do a google search. It's not that involved.

---

