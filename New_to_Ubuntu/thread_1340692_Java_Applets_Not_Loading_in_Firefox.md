---
title: "Java Applets Not Loading in Firefox"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by naiku on 2009-11-28
I am using Ubuntu 9.10, and Firefox 3.5.5 and for some reason Java applets do not appear to be starting automatically. Take for example if I go to [http://store.nike.com/](http://store.nike.com/) the menu loads on the left side of the page, but nothing loads on the rest of the page, regardless of the options that I click on. This happens on various websites, for example yesterday going to [www.bobthebuilder.com](www.bobthebuilder.com) the whole animation in the middle of the page would not load, but today it loads fine.

I also get a problem with Facebook videos, which I am not sure if it related to the same issue as with various websites. If I click to watch a video in Facebook, I can watch it once, but then the Play Again link does nothing. If I want to watch the video again, I have to re-load the page.

The other problem I am currently having is with the latest update of Ubuntu, I am currently using Wubi as a dual boot with Windows Vista. After an update I had a new option appear in the boot up menu (I believe it went from a 2.6.31-14 to a 2.6.31-15 version) however this version does not boot and gives me an error "VFS unable to mount root FS on unknown block (8,2)" and will not boot. I can still get into and use 2.6.31-14 though.

Any help on the above issues is appreciated, I am trying to decide whether to ditch Vista and move over to using Ubuntu full time. But some of these issues while fine for me, are not acceptable to my wife who wants the laptop to just work.

Thanks.

---

### Post by marshmallow1304 on 2009-11-29
For Java try installing the [Java Plugin]("apt://sun-java6-plugin").

---

### Post by egwest on 2009-11-29
I am having the same problem. I already have the JAVA plugin, but no applets are loading. I have tried nearly everything I can find, I have uninstalled java and reinstalled it following every instruction I can find on the matter, but it never seems to work.

Anyone got any ideas?

---

### Post by Virtual Liberty on 2009-11-29
Both websites are based on Flash, not Java.

---

### Post by egwest on 2009-11-29
No...not really. If you try to upload pictures to your facebook page you get the option of using a java applet interface so you can upload more picture files then only 5 at a time, which is the simple interface.
The java applet page has been coming up a blank box on me.

Solved this for now.
I uninstalled the Java Plugin via synaptic, then went to facebook and to the picture upload page, and told I was missing the plugin, it gave me the option of the Icetea Java plugin or the regular java plugin, I chose the icetea this time, now the java applets are loading as they should.

---

### Post by naiku on 2009-11-30
> **Virtual Liberty said:**
> Both websites are based on Flash, not Java.

I have both installed, Flash and Java (Icedtea and Sun Java) the Facebook photo loading piece works fine for me, You Tube videos work fine, its only certain websites the content does not load and I am left with a big empty box. 

Actually, when I say You Tube videos work fine, they work fine, but if I click on one of the previews that appears when the video has finished, nothing happens, same as if I click Play Again on a Facebook video, nothing happens.

Will try the solution egwest posted and see if that works.

---

### Post by sez56 on 2010-02-22
I upgraded to Firefox 3.5 (running on Ubuntu 9.10 AMD64)and my trading platform advanced charts wouldn't load - said I needed the 'latest java'.  Went through all the instructions to purge old java and install new but to no avail.  So I abandoned Firefox and loaded Swiftfox which worked fine - for a time..until it upgraded too and we were back at square one!  Now I have installed Google Chrome - it has no problems with this at all.  So guys at Firefox - whatever you just did that moved through to Swiftfox - there is your problem.  As for the newbies out there all I can say is I've learn't an awful lot about terminal commands and nautilus in the last couple of months.  Please fix Firefox - I like it!

---

### Post by wojox on 2010-02-22
Swiftfox is proprietary. Firefox is open source. Try installing Java through here: [http://sites.google.com/site/easylinuxtipsproject/java#TOC-Get-JRE](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Get-JRE)

---

