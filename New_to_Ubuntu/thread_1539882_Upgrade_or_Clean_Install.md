---
title: "Upgrade or Clean Install"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by daniell59 on 2010-07-27
I am almost ready to install Ubuntu 10.04. At present, I am using 9.10. I seem to remember that a clean install is always better. Would appreciate advice in this matter.

Thanks

---

### Post by wojox on 2010-07-27
I always do a clean install. There's less junk taking up space.

---

### Post by k3lt01 on 2010-07-27
A clean install is better but not all systems will do a clean install. My laptop, admittedly a poverty pack with very little RAM, wouldn't install 10.04 off a cd so I had to do an upgrade via Update Manager.

---

### Post by Paqman on 2010-07-27
Upgrades used to be messy, but these days they work really well. It's largely a matter of preference and how your system is set up.

If your machine is set up so that a clean reinstall is no hassle, then definitely do that. Likewise if you have a very heavily modified or tweaked system, or sue a lot of non-standard or self-compiled apps. The more oddball your system is, the less likely it is to upgrade smoothly.

But if it's going to be a pain to reinstall then by all means give the upgrade a go. I've upgraded several systems to 10.04 without any problems at all.

---

### Post by VH-BIL on 2010-07-27
I always upgrade, why install all of your applications again and set up your desktop theme, icons, wallpaper, compiz settings, etc...

Even if there is left over files which I guess would only be settings in your home folder for uninstalled applications which happens when you uninstall applications anyway. These files are easy to remove anyway.

The only thing I don't like is cleaning up software sources after an upgrade.

---

### Post by scouser73 on 2010-07-27
I also suggest doing a clean installation.

---

### Post by rolnics on 2010-07-27
First things first....backup your data!

Now, do you have a separate /home partition? If you do then I'd give an upgrade a try, as long as everything is back up!

Yes, a clean install is better, because you have clean / un-modified config files.

---

### Post by daniell59 on 2010-07-27
Thanks to all for your informative suggestions. 
The only things that I am interested in saving is

Photos
Bookmarks
Address book

As I previously mentioned in another thread,
After some difficulties, I was able to get flash player 
working on 64 bits. I hope that I will be able to do it again.

---

### Post by VH-BIL on 2010-07-27
If you use chromium browser you can sync your bookmarks to your google account.

---

### Post by daniell59 on 2010-07-27
> **rolnics said:**
> First things first....backup your data!

Now, do you have a separate /home partition? If you do then I'd give an upgrade a try, as long as everything is back up!

Yes, a clean install is better, because you have clean / un-modified config files.

Can I backup the bookmarks on a flash drive?

---

### Post by k3lt01 on 2010-07-27
> **daniell59 said:**
> Can I backup the bookmarks on a flash drive?
In your /home folder there will be a hidden folder called mozilla all your mozilla stuff (firefox, thunderbird etc) will be stored in that. If you copy that folder to a flash drive or another disk of some sort you will be able to copy it back once the installation is finished.

---

### Post by Sir Jasper on 2010-07-27
Hi,

I think the latest version of 10.04 is due in two days time on 29th July 2010 - though I may have misremembered.

My regards

---

### Post by rolnics on 2010-07-27
> **daniell59 said:**
> Can I backup the bookmarks on a flash drive?

Or you could install xmarks in Firefox to sync your bookmarks.

---

### Post by k3lt01 on 2010-07-27
> **rolnics said:**
> Or you could install xmarks in Firefox to sync your bookmarks. Only problem with that is it wont save passwords etc!

---

### Post by ajgreeny on 2010-07-27
> **k3lt01 said:**
> In your /home folder there will be a hidden folder called mozilla all your mozilla stuff (firefox, thunderbird etc) will be stored in that. If you copy that folder to a flash drive or another disk of some sort you will be able to copy it back once the installation is finished.
Just to make sure you are not dismayed by the loss of any thunderbird profile and emails, note that in 10.04 the above is almost but not quite correct. 

The thunderbird profile and configuration is in a separate hidden folder called ~/.mozilla-thunderbird which in 10.04 with Thunderbird 3, is a link to the real folder simply called ~/.thunderbird.  The thunderbird config was never in a folder called just ~/.mozilla in ubuntu.

---

### Post by k3lt01 on 2010-07-27
> **ajgreeny said:**
> Just to make sure you are not dismayed by the loss of any thunderbird profile and emails, note that in 10.04 the above is almost but not quite correct. 

The thunderbird profile and configuration is in a separate hidden folder called ~/.mozilla-thunderbird which in 10.04 with Thunderbird 3, is a link to the real folder simply called ~/.thunderbird.  The thunderbird config was never in a folder called just ~/.mozilla in ubuntu.Not arguing what is evidently a moot point but when I was using thunderbird I never saved anything but mozilla (and pidgin but thats another story anyway) and it was always restored when I put mozilla back. A symlink maybe?

---

### Post by CharlesA on 2010-07-27
> **Sir Jasper said:**
> Hi,

I think the latest version of 10.04 is due in two days time on 29th July 2010 - though I may have misremembered.

My regards

Check the [release schedule]("https://wiki.ubuntu.com/LucidReleaseSchedule"). Looks like 10.04.1 will be out Mid-August

> **k3lt01 said:**
> Not arguing what is evidently a moot point but when I was using thunderbird I never saved anything but mozilla (and pidgin but thats another story anyway) and it was always restored when I put mozilla back. A symlink maybe?

It's probably a symlink.

I always -try- to do clean installs when a new version is out. I have had a couple problems with doing upgrades, but they work for the most part.

However a clean install is easier for me to troubleshoot if I have problems.

---

### Post by k3lt01 on 2010-07-27
> **CharlesA said:**
> It's probably a symlink.Interesting, learn something new everyday.

---

### Post by Anuovis on 2010-07-27
> **daniell59 said:**
> Can I backup the bookmarks on a flash drive?
If you need bookmarks or address book *only*, there is an easy option to export them as .html and .csv files in Mozilla apps. Just look in their respective menus inside the application, there will be an export option. These can then be copied to the flash drive and imported back later. This will not save other settings and preferences, however.

---

### Post by CharlesA on 2010-07-27
> **k3lt01 said:**
> Interesting, learn something new everyday.

You can always double-check by running: ```
ls -ld ~/.mozilla-thunderbird
```

If it's a symlink, the permissions will look something like this:

```
lrwxrwxrwx
```

EDIT: Checked it and it is a symlink:

```
ls -ld .mozilla-thunderbird
lrwxrwxrwx 1 ubuntu ubuntu 25 2010-07-27 03:19 .mozilla-thunderbird -> /home/ubuntu/.thunderbird

```

---

### Post by k3lt01 on 2010-07-27
I don;t use thunderbird anymore but it is good to know so thanks for that.

---

### Post by Jkwc on 2010-07-27
Upgrade is more easier I think, less hassle

---

