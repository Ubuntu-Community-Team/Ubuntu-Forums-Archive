---
title: "is there a way to transfer settings to new 10.10"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by kapi on 2010-10-12
Am currently using Ubuntu 9.10 Karmic Koala and it's been brilliant for the past year, I run Lamp and do web design solely with Ubuntu. My query is that I want all my settings and aps to be ghosted if you like to the meerkat.

Anyone have any suggestions, all comments welcome is it even possible

---

### Post by davidmohammed on 2010-10-12
the easiest way is to upgrade first to lucid and then to meerkat via the upgrade-manager.

---

### Post by fatality_uk on 2010-10-12
Do you have a seperate home partition?

---

### Post by kapi on 2010-10-12
no I usually do a fresh install each time and allocate all the drive space to the install.

---

### Post by t0p on 2010-10-12
I *believe* (though I haven't tried it myself yet) that if you back-up your home directory to an external drive, install the new version of Ubuntu then copy your old home directory to your new home directory, your configurations will be passed to the new install; as most config files are in your home directory, mostly as so-called "hidden" files, ie files whose names begin with a ".".

---

### Post by sandyd on 2010-10-12
> **kapi said:**
> Am currently using Ubuntu 9.10 Karmic Koala and it's been brilliant for the past year, I run Lamp and do web design solely with Ubuntu. My query is that I want all my settings and aps to be ghosted if you like to the meerkat.

Anyone have any suggestions, all comments welcome is it even possible
settings are in /etc, you will have to backup these manually.

You mentioned you run LAMP, so heres how you back it up

You need to make a copy of 
/etc/apache2
and backup (export) your SQL databases using phpmyadmin.
Your websites, you will have to back them up yourself.

As for the apps, 
```

dpkg --get-selections > ~/Desktop/bkuppackages
```
will output your installed apps into the file. Save it to a USB drive or something.

```

dpkg --set-selections /path/to/file
```
will get your packages back

---

### Post by t0p on 2010-10-12
> **sandyd said:**
> 
As for the apps, 
```

dpkg --get-selections > ~/Desktop/bkuppackages
```will output your installed apps into the file. Save it to a USB drive or something.

```

dpkg --set-selections /path/to/file
```will get your packages back

When you run the command 
```
dpkg --get-selections > ~/Desktop/bkuppackages
```you get a file looking something like this:

> 
<snip>
bogofilter                install
bogofilter-bdb                             install
bogofilter-common                  install
boxee                                            install
brasero                                         deinstall
brltty                                            deinstall
brltty-x11                                 deinstall
bsdmainutils                             install
<snip>
Will the command

```

dpkg --set-selections /path/to/file

```will dpkg install the packages regardless of the "install/deinstall" column?  Or do you need to remove that column first?

---

### Post by kapi on 2010-10-13
Thanks very much for your replies, I'll try them tonight

---

### Post by petronell on 2010-10-13
I would recommend doing the upgrade via update manager. The upgrade to 10.04 and then to 10.10 has worked flawlessly for me.

I do take a backup of my home folder before doing it, and allow a couple of hours for it to complete.

daveR

---

### Post by kapi on 2010-10-14
is the dragging of the home folder to an external hard drive just as good as a backup?

---

### Post by DouglasAdams on 2010-10-15
> **petronell said:**
> I would recommend doing the upgrade via update manager. The upgrade to 10.04 and then to 10.10 has worked flawlessly for me.

I do take a backup of my home folder before doing it, and allow a couple of hours for it to complete.

daveR
i would certainly NOT recommend doing this!
when i did this from 9.10 to 10.04 i had all sorts of problems.
i'm not saying that everyone had problems
but i'm certainly not the only one who did - by a long way!
read the thread about peoples experiences of moving from from 9.10 to 10.04

my advice, as a pretty basic user, is:

save your /home (to pen or ...)
save your "markings" in Synaptic Package manager (to pen or ...)
maybe save some or all of your /etc (see my post below)
boot a live disk
make a separate /home and copy your saved /home files to it
do a "clean" install of the version you want to use
reload your "markings"  (from pen or ...)
maybe reload some or all of your /etc (see my post below)
award yourself a prize for being practically perfect  :)

---

### Post by DouglasAdams on 2010-10-15
> **sandyd said:**
> settings are in /etc, you will have to backup these manually.

which part, or parts, of the /etc directory should be copied from one release to the next?
all of it?
just some bits?
if the later, which bits?

---

