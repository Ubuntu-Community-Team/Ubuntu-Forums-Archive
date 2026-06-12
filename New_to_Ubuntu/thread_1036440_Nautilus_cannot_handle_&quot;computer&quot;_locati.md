---
title: "Nautilus cannot handle &quot;computer&quot; locations."
date: 2009-01-10
forum: New to Ubuntu
---

### Post by JDuc on 2009-01-10
I've tried installing the latest version of gvfc from source per another thread, but it's sill not working....

Any other ideas?  What other information do I need to provide?

I cannot access my USB thumb drive.   When I click on Computer, I get this error: Nautilus cannot handle "computer" locations.

Any ideas?

---

### Post by oopsdude on 2009-01-10
You need to be more specific. Which thread? And what do you mean by "not working"? Is there an error message?

And is your question about your thumb drive related to gvfc? If you don't know, did this error only occur after trying to install gvfc? Please post the output of dmesg.

---

### Post by Partyboi2 on 2009-01-10
Have a look at [[COLOR=Blue]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233889") bug report and try what is mentioned.

---

### Post by JDuc on 2009-01-11
> **oopsdude said:**
> You need to be more specific. Which thread?

[http://ubuntuforums.org/showthread.php?t=801597](http://ubuntuforums.org/showthread.php?t=801597)

>  And what do you mean by "not working"? Is there an error message?Click on Computer and the thread title is the error message.

> And is your question about your thumb drive related to gvfc? If you don't know, did this error only occur after trying to install gvfc? Please post the output of dmesg.The thread indicates that this should be solved by installing GVFC from source.

---

### Post by JDuc on 2009-01-11
> **Partyboi2 said:**
> Have a look at [[COLOR=Blue]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233889") bug report and try what is mentioned.

Tried
```
sudo mv /usr/local /usr/local.old && sudo mkdir /usr/local
```

and now I do get a different error:

Previously I would get the following:

```
Could not display "computer:".

Nautilus cannot handle "computer" locations.
```Now I get the following:

```
Could not display "computer:///".

Nautilus cannot handle "computer" locations.
```Rather strange!

---

### Post by JDuc on 2009-01-11
Fixed by installing another file system and rebooting.

Now to determine what issues I'll run into by running this other file system.

---

### Post by jerkii on 2009-04-02
After I issue the following command, everything is okay now! but why? 
```

mv /usr/local /usr/local.old
mkdir /usr/local

```

currently, the following files live in my /usr/local, is the Nautilus was affected by these libs? if so, which lib does?:
```

drwxr-xr-x 3 root root       72 2009-03-29 18:22 gio
drwxr-xr-x 3 root root       72 2009-03-29 18:22 glib-2.0
-rwxr-xr-x 1 root root      890 2009-03-29 21:05 libatk-1.0.la
lrwxrwxrwx 1 root root       22 2009-03-29 21:05 libatk-1.0.so -> libatk-1.0.so.0.2609.1
lrwxrwxrwx 1 root root       22 2009-03-29 21:05 libatk-1.0.so.0 -> libatk-1.0.so.0.2609.1
-rwxr-xr-x 1 root root   381138 2009-03-29 21:05 libatk-1.0.so.0.2609.1
-rwxr-xr-x 1 root root     1038 2009-03-29 18:22 libgio-2.0.la
lrwxrwxrwx 1 root root       22 2009-03-29 18:22 libgio-2.0.so -> libgio-2.0.so.0.2000.0
lrwxrwxrwx 1 root root       22 2009-03-29 18:22 libgio-2.0.so.0 -> libgio-2.0.so.0.2000.0
-rwxr-xr-x 1 root root  1635253 2009-03-29 18:22 libgio-2.0.so.0.2000.0
-rwxr-xr-x 1 root root      943 2009-03-29 18:22 libglib-2.0.la
lrwxrwxrwx 1 root root       23 2009-03-29 18:22 libglib-2.0.so -> libglib-2.0.so.0.2000.0
lrwxrwxrwx 1 root root       23 2009-03-29 18:22 libglib-2.0.so.0 -> libglib-2.0.so.0.2000.0
-rwxr-xr-x 1 root root  2282537 2009-03-29 18:22 libglib-2.0.so.0.2000.0
-rwxr-xr-x 1 root root      996 2009-03-29 18:22 libgmodule-2.0.la
lrwxrwxrwx 1 root root       26 2009-03-29 18:22 libgmodule-2.0.so -> libgmodule-2.0.so.0.2000.0
lrwxrwxrwx 1 root root       26 2009-03-29 18:22 libgmodule-2.0.so.0 -> libgmodule-2.0.so.0.2000.0
-rwxr-xr-x 1 root root    33661 2009-03-29 18:22 libgmodule-2.0.so.0.2000.0
-rwxr-xr-x 1 root root      991 2009-03-29 18:22 libgobject-2.0.la
lrwxrwxrwx 1 root root       26 2009-03-29 18:22 libgobject-2.0.so -> libgobject-2.0.so.0.2000.0
lrwxrwxrwx 1 root root       26 2009-03-29 18:22 libgobject-2.0.so.0 -> libgobject-2.0.so.0.2000.0
-rwxr-xr-x 1 root root   778026 2009-03-29 18:22 libgobject-2.0.so.0.2000.0
-rwxr-xr-x 1 root root     1006 2009-03-29 18:22 libgthread-2.0.la
lrwxrwxrwx 1 root root       26 2009-03-29 18:22 libgthread-2.0.so -> libgthread-2.0.so.0.2000.0
lrwxrwxrwx 1 root root       26 2009-03-29 18:22 libgthread-2.0.so.0 -> libgthread-2.0.so.0.2000.0
-rwxr-xr-x 1 root root    44089 2009-03-29 18:22 libgthread-2.0.so.0.2000.0
-rwxr-xr-x 1 root root     1071 2009-03-29 21:32 libpango-1.0.la
lrwxrwxrwx 1 root root       24 2009-03-29 21:32 libpango-1.0.so -> libpango-1.0.so.0.2400.0
lrwxrwxrwx 1 root root       24 2009-03-29 21:32 libpango-1.0.so.0 -> libpango-1.0.so.0.2400.0
-rwxr-xr-x 1 root root   760744 2009-03-29 21:32 libpango-1.0.so.0.2400.0
-rwxr-xr-x 1 root root     1311 2009-03-29 21:32 libpangocairo-1.0.la
lrwxrwxrwx 1 root root       29 2009-03-29 21:32 libpangocairo-1.0.so -> libpangocairo-1.0.so.0.2400.0
lrwxrwxrwx 1 root root       29 2009-03-29 21:32 libpangocairo-1.0.so.0 -> libpangocairo-1.0.so.0.2400.0
-rwxr-xr-x 1 root root   153994 2009-03-29 21:32 libpangocairo-1.0.so.0.2400.0
-rw-r--r-- 1 root root      967 2009-03-29 21:32 libpangoft2-1.0.la
lrwxrwxrwx 1 root root       27 2009-03-29 21:32 libpangoft2-1.0.so -> libpangoft2-1.0.so.0.2400.0
lrwxrwxrwx 1 root root       27 2009-03-29 21:32 libpangoft2-1.0.so.0 -> libpangoft2-1.0.so.0.2400.0
-rwxr-xr-x 1 root root   567784 2009-03-29 21:32 libpangoft2-1.0.so.0.2400.0
-rw-r--r-- 1 root root      955 2009-03-29 21:32 libpangox-1.0.la
lrwxrwxrwx 1 root root       25 2009-03-29 21:32 libpangox-1.0.so -> libpangox-1.0.so.0.2400.0
lrwxrwxrwx 1 root root       25 2009-03-29 21:32 libpangox-1.0.so.0 -> libpangox-1.0.so.0.2400.0
-rwxr-xr-x 1 root root   169633 2009-03-29 21:32 libpangox-1.0.so.0.2400.0
drwxr-xr-x 3 root root       72 2009-03-29 21:32 pango
drwxr-xr-x 2 root root      464 2009-03-29 21:32 pkgconfig
drwxrwsr-x 3 root staff      80 2008-10-30 06:53 python2.5
drwxr-xr-x 3 root root       72 2009-03-23 22:01 site_ruby


```

---

### Post by larschristian on 2010-10-22
This is an old thread, but I ran into this problem recently and this thread was in the top google results. The problem was that I had compiled glib from source to solve a dependency for compiling gimp 2.7. That put a new version of libgio in /usr/local/lib

Solution was to remove all libglib and libgio files in /usr/local/lib. Then the libglib and libgio from /usr/lib are loaded.

.lars

---

### Post by c0rrupt0r on 2010-12-04
I just ran into this problem a few days ago and I just found a solution for me that works wonders on this thread below

[http://ubuntuforums.org/showthread.php?t=801597&page=8](http://ubuntuforums.org/showthread.php?t=801597&page=8)

Simply all I did was open a terminal and type in 

sudo aptitude install ubuntu-desktop

then Choose Yes.

---

### Post by GenericBox on 2011-03-26
> **larschristian said:**
> This is an old thread, but I ran into this problem recently and this thread was in the top google results. The problem was that I had compiled glib from source to solve a dependency for compiling gimp 2.7. That put a new version of libgio in /usr/local/lib

Solution was to remove all libglib and libgio files in /usr/local/lib. Then the libglib and libgio from /usr/lib are loaded.

.lars

I can confirm this solution works. Exactly the same issue. Removed these files, rebooted and it is fine once more.

---

### Post by pd12 on 2011-07-04
> **GenericBox said:**
> I can confirm this solution works. Exactly the same issue. Removed these files, rebooted and it is fine once more.

Same here, worked great, simple solution. 
Running Ubuntu 10.04

Edit: Also resolved dependencies with Pidgin Messenger so I could install it again. Am very happy my linux system is back up to full speed =)

---

