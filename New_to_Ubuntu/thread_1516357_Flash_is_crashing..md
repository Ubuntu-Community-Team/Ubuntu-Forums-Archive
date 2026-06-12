---
title: "Flash is crashing."
date: 2010-06-23
forum: New to Ubuntu
---

### Post by zer010 on 2010-06-23
I've already had firefox crashing on me whenever i run into a flash-heavy site. so i shopped around for a new browser. i never touched FF, just left it as is. after a couple different tries i've kinda settled on Chromium. now i'm getting that just Flash is crashing and not the browser. as shown in the attch:
 how would i go about installing one of the open source plugins?

---

### Post by lovinglinux on 2010-06-23
IMO, it will be a waste of time. Just stick with the latest adobe version.

---

### Post by no2498 on 2010-06-23
greasemonkey and i do think something else i had to install to help firefox and opera

id look for greasemonkey firefox 

to find the other 1 i installed

hope it helps you too

---

### Post by lovinglinux on 2010-06-23
> **no2498 said:**
> greasemonkey and i do think something else i had to install to help firefox and opera

id look for greasemonkey firefox 

to find the other 1 i installed

hope it helps you too

????

---

### Post by zer010 on 2010-06-23
how is greasemonkey gonna help with my situation? i've heard that there's a compatibility problem between 10.04 and Flash in FF, but it seems it also affects other browsers too. is there any info on a patch or update to fix this?

---

### Post by zer010 on 2010-06-23
i just gave FF another go with Flash plug-in enabled, trying to crash it. i was successful! :( had one tab playing a vid from youtube, and the other was on ubuntuforums. all of a sudden FF just closed. this was what was in the terminal:

(firefox-bin:5109): Gdk-WARNING **: XID collision, trouble ahead
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 123813 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

any ideas?

---

### Post by Jackattak on 2010-06-24
I think flash sites are cool but I am running a simple website for a [Denver HVAC]("http://www.denverheating.org") company using Joomla. Would Ubuntu still be a more stable platform for simple programs?

---

### Post by Windows Nerd on 2010-06-24
> **zer010 said:**
> i just gave FF another go with Flash plug-in enabled, trying to crash it. i was successful! :( had one tab playing a vid from youtube, and the other was on ubuntuforums. all of a sudden FF just closed. this was what was in the terminal:

(firefox-bin:5109): Gdk-WARNING **: XID collision, trouble ahead
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 123813 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

any ideas?
It's odd that it crashed, because the newest version of Firefox (provided that you are using it) has crash protection, meaning if a Flash applet or something crashes the whole browser will not crash.

Maybe try upgrading your version of FF will help?

Scott

---

### Post by lovinglinux on 2010-06-24
> **zer010 said:**
> i just gave FF another go with Flash plug-in enabled, trying to crash it. i was successful! :( had one tab playing a vid from youtube, and the other was on ubuntuforums. all of a sudden FF just closed. this was what was in the terminal:

(firefox-bin:5109): Gdk-WARNING **: XID collision, trouble ahead
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 123813 error_code 2 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

any ideas?

See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

> **Windows Nerd said:**
> It's odd that it crashed, because the newest version of Firefox (provided that you are using it) has crash protection, meaning if a Flash applet or something crashes the whole browser will not crash.

Maybe try upgrading your version of FF will help?

Scott

The OP is probably not using Firefox 3.6.4, because this version will not be in the repositories until tomorrow.

---

### Post by zer010 on 2010-06-24
i guess i'm still using 3.6.3, but if the new one will hit the repos tomorrow... i guess i'll see if it helps. will that affect the flash plugin from crashing though? there is one site that is almost always a problem. [http://www.mocospace.com]("http://www.mocospace.com")

A little time spent in there invariably crashes the flash plugin in just about every browser i've tried. FF is about the only one that actually crashes itself.

---

### Post by lovinglinux on 2010-06-24
> **zer010 said:**
> i guess i'm still using 3.6.3, but if the new one will hit the repos tomorrow... i guess i'll see if it helps. will that affect the flash plugin from crashing though? there is one site that is almost always a problem. [http://www.mocospace.com]("http://www.mocospace.com")

A little time spent in there invariably crashes the flash plugin in just about every browser i've tried. FF is about the only one that actually crashes itself.

Firefox 3.6.4 has plugin isolation, so if flash crashes, you just receive a warning where the content should be displayed. The browser itself doesn't crash. It is a awesome feature.

You can get it now using the ubuntu-mozilla-security ppa or downloading it from Mozilla or by installing Ubuntuzilla (32bit). See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by philinux on 2010-06-24
Try running in safe mode.

```
firefox -safe-mode
```

It could be an addon causing the trouble.

---

### Post by lovinglinux on 2010-06-24
EDIT: wrong info

---

### Post by philinux on 2010-06-24
> **lovinglinux said:**
> In safe mode flash will be disabled, so it won't crash, but the OP already knows it is a flash problem.

I just tried this before posting and flash was still working. :p

---

### Post by lovinglinux on 2010-06-24
> **philinux said:**
> I just tried this before posting and flash was still working. :p

You are right. I just tested it and check it at Mozilla. Plugins are not disabled in safe mode, only extensions and themes ](*,) 

I could swear they were disabled too :)

---

### Post by Windows Nerd on 2010-06-24
> **lovinglinux said:**
> The OP is probably not using Firefox 3.6.4, because this version will not be in the repositories until tomorrow.

Oh, I have 3.6.6 becuase I use the pre-release versions. My bad :oops:

And also, all the other browsers (Chrome, for example) have (and have had it for awhile) crash protection support. FF just implemented it.

---

### Post by lovinglinux on 2010-06-24
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by zer010 on 2010-06-24
^ as requested:
    File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

ok, so after upgrading to the new FF version tomorrow, Flash will still crash, but not the browser itself? WhooHoo! \\:D/ :rolleyes: ](*,)

No answer as to why flash is crashing in the first place? Is it normal for flash to crash? Is it just a crappy media format, that has been adopted dang near everywhere?

---

### Post by lovinglinux on 2010-06-25
> **zer010 said:**
> ^ as requested:
    File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

You have the latest version.

> **zer010 said:**
> ok, so after upgrading to the new FF version tomorrow, Flash will still crash, but not the browser itself? WhooHoo! \\:D/ :rolleyes: ](*,)

Yes.

> **zer010 said:**
> No answer as to why flash is crashing in the first place? Is it normal for flash to crash? Is it just a crappy media format, that has been adopted dang near everywhere?

Lots of users have flash issues and could be due to several reasons, but flash is indeed a crap plugin in Linux.

Have you tried to start Firefox in safe mode as suggested by philinux?

Have you tried my Flash Optimization tutorial?

---

### Post by zer010 on 2010-06-27
i think in my case it mustve been a hardware issue. although FF is still a dud, so ive switched to chromium. thanks to everyone thats helped, i greatly appreciate it!

---

