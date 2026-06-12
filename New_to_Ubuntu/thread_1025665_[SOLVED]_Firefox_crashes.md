---
title: "[SOLVED] Firefox crashes"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by mancroft on 2008-12-30
Using Interpid.

Firefox has suddenly started crashing over the last few days. There appears to be no particular reason but it may have something to do with Flash as it sometimes happens when I run a Flash movie.

Any ideas?

Thank you.

---

### Post by Michael.Godawski on 2008-12-30
hi,

can you please run firefox via the terminal and post any error messages?

```
firefox
```

---

### Post by mancroft on 2008-12-30
Thank you for your help, Michael.

No errors.

john@john-desktop:~$ firefox
john@john-desktop:~$

---

### Post by Connyank on 2008-12-30
> **mancroft said:**
> Using Interpid.

Firefox has suddenly started crashing over the last few days. There appears to be no particular reason but it may have something to do with Flash as it sometimes happens when I run a Flash movie.

Any ideas?

Thank you.


Have you updated the flash plugin via the Adobe site?
check your flash vers by typing "about:plugins" in the location bar (without the paren).
No joy, visit [http://kb.mozillazine.org/Firefox_crashes](http://kb.mozillazine.org/Firefox_crashes) to see other possible causes.
My guess would be a bad plugin or extension.

---

### Post by mancroft on 2008-12-30
Am using Shockwave Flash 10.0 r12 which is up to date.

---

### Post by kansasnoob on 2008-12-30
A few things come to mind. Other than the crashes are both sound & video good in flash?

---

### Post by mancroft on 2008-12-30
> **kansasnoob said:**
> A few things come to mind. Other than the crashes are both sound & video good in flash?

Yep they work OK. Firefox worked OK until a few days ago when the crashes suddenly started happening. There appears to be no pattern to or obvious reason for the crashes.

---

### Post by Frank_F on 2008-12-30
I had identical issues a few weeks ago using 7.1...I updated to 8.10 and issue resolved....may be an update that you require...I have installed all updates ?

---

### Post by mancroft on 2008-12-30
> **Frank_F said:**
> I had identical issues a few weeks ago using 7.1...I updated to 8.10 and issue resolved....may be an update that you require...I have installed all updates ?

Yep. Am using 8.10. All updates installed. 

Strange.

---

### Post by kansasnoob on 2008-12-30
> **mancroft said:**
> Yep they work OK. Firefox worked OK until a few days ago when the crashes suddenly started happening. There appears to be no pattern to or obvious reason for the crashes.

I asked because:

(1)There have been some PulseAudio problems related to flash, but that doesn't appear to your problem:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

(2)I've always had poor flash video performance (including crashes) without "Flashblock" installed. After recent updates Flashblock quit working and therefore Flash stunk for me again. After trying many things I made the jump to the Ubuntuzilla version of Firefox and I've been very pleased:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

They also have a forum on this site:

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

But also be certain you DO NOT have "gnash" installed.

```
sudo apt-get --purge remove gnash
```

Then install restricted-extras:

```
sudo apt-get install ubuntu-restricted-extras
```

And install the current version of flashblock by searching add-ons in Firefox.

---

### Post by linux_tech on 2008-12-30
check flash plugins-
In your browser enter the following command, press enter
```

    about:plugins

```
If plugins are there and flash still causes crash then you may consider 
re-installing flash10. This may article may be helpful-
[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.htm](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.htm)

---

### Post by mancroft on 2008-12-30
> **linux_tech said:**
> check flash plugins-
In your browser enter the following command, press enter
```

    about:plugins

```
If plugins are there and flash still causes crash then you may consider 
re-installing flash10. This may article may be helpful-
[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.htm](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.htm)

Thanks

Should be .html

[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html)

I'll try that.

---

### Post by mancroft on 2009-01-04
Thanks, linux_tech. I reinstalled the Flash plugin and that appears to have worked.

---

### Post by albinootje on 2009-01-04
> **mancroft said:**
> Using Interpid.

Firefox has suddenly started crashing over the last few days. There appears to be no particular reason but it may have something to do with Flash as it sometimes happens when I run a Flash movie.

Any ideas?

Thank you.

Does it also crash with :
```

firefox -safe-mode

```

---

### Post by mancroft on 2009-01-04
> **albinootje said:**
> Does it also crash with :
```

firefox -safe-mode

```

I've got it working OK now, albinootje, and I am not going to tempt fate.

---

### Post by albinootje on 2009-01-04
> **mancroft said:**
> I've got it working OK now, albinootje, and I am not going to tempt fate.

Good. Can you mark this thread as SOLVED ? Thanks.

---

