---
title: "Is it possible: Perfect Flash and Firefox?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by rage9 on 2009-04-14
Having installed Ubuntu on two systems, one major crappy, and one blazing I never have been able to get Flash to work perfectly.  Oh sure it works for the most part, but there are lots of time where you can't see the flash content.  It just doesn't show up.  Sometimes I can't see the video but know it's playing because the sound still comes out, how weird is that?  Every once and a while I have to completely restart Firefox because no videos or any flash is working.

You guys have any tips?  I have the flashplugin-installer package installed.

---

### Post by rage9 on 2009-04-14
Could a mod move this to the General Help section, posted this in the wrong section.

---

### Post by SunnyRabbiera on 2009-04-14
Flash has always been flaky in Linux, there is not a lot we can do about it as we are at the mercy of Adobe there...
But its gotten a lot better then it was, at least for me.

---

### Post by hyper_ch on 2009-04-14
are you using 64bit?

---

### Post by rage9 on 2009-04-14
> **hyper_ch said:**
> are you using 64bit?

Currently yes, but also ran the 32 bit on the old system and it did the same thing.

---

### Post by hyper_ch on 2009-04-14
use the 64bit flash plugin. It's much better.

[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

---

### Post by gandaran on 2009-04-14
> **rage9 said:**
> Having installed Ubuntu on two systems, one major crappy, and one blazing I never have been able to get Flash to work perfectly.  Oh sure it works for the most part, but there are lots of time where you can't see the flash content.  It just doesn't show up.  Sometimes I can't see the video but know it's playing because the sound still comes out, how weird is that?  Every once and a while I have to completely restart Firefox because no videos or any flash is working.

You guys have any tips?  I have the flashplugin-installer package installed.
yes it's possible, it's not that adobe linux flash is crapy, it's more of ubuntu's fault that flash has problems for some users, put flash on a perfect linux system and it will work prefect.
now about your problem
are you running ubuntu 64-bits with the system 32-bits flash package or have you tried the new 64-bits beta flash?
are you running ubuntu 32-bits and you only have the flashplugin-nonfree package installed or have you installed any other open source flash like gnash or swfdec flash too?
do you have the flashblock addon installed? 
the perfect set up is to have only one adobe flash plugin installed, the flashplugin-nonfree is good enough for 32-bits users, don't install any other crap if it doesn't work properly, keep your system fully updated and if sometimes it gives you problems you can do some system fixing like following this [guide]("http://ubuntuforums.org/showthread.php?t=789578") to have a perfect working ubuntu system

---

### Post by rage9 on 2009-04-14
> **hyper_ch said:**
> use the 64bit flash plugin. It's much better.

[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

Thanks man, just installed it hopefully it works out well.

---

### Post by baxna on 2009-04-14
I've got a related question to this. I visited a website that wants me to install Flash (of some sort). I'm using Firefox and Ubuntu 8.10 on a 32-bit system. The options Firefox gives me are:
[LIST=1]
[*]Adobe flash
[*]swfdec swf player
[*]Gnash swf player
[/LIST]
Is one of these better than another? Should I install all three?

---

### Post by WhiskyChris on 2009-04-14
Soon after installing ubuntu I couldn't get flash working for a long time. One thing I tried was installing everything in the repository that could help but I ended up with too much rubbish. You only want to have _one_ sort of flash installed at a time, if it doesn't work - remove it and try something else.

To eventually get flash to work all I had to do was remove some of the gunff, leaving only one flash and it was much better.

---

### Post by 3rdalbum on 2009-04-14
> **baxna said:**
> I've got a related question to this. I visited a website that wants me to install Flash (of some sort). I'm using Firefox and Ubuntu 8.10 on a 32-bit system. The options Firefox gives me are:
[LIST=1]
[*]Adobe flash
[*]swfdec swf player
[*]Gnash swf player
[/LIST]
Is one of these better than another? Should I install all three?

Adobe makes Flash, so the Adobe player will work the best. It is proprietary and closed-source.

If you disagree with proprietary software and want a completely open-source system, then you should choose either of the other two; if all you use Flash for is Youtube, then I think swfdec generally works better for Youtube.

---

### Post by Clancy_s on 2009-04-14
@ baxna - I'd for Adobe.  Obviously it's not open source but it's more secure than gnash and the most widely compatible.

---

