---
title: "Still having problems with UTube"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by ECET on 2010-07-21
Hello all.....I am still having trouble getting utube to play on ubuntu.  I have the flash player installed, I have google chrome installed, and i even installed minitube and none of these things seem to work. I am using the lastest version of unbuntu, 10.04......any ideas?....thanks

---

### Post by mike555 on 2010-07-21
how fast is you internet connection? dialup doesn't play videos very well unless you pause it and let it load before trying to play it.

---

### Post by limestone on 2010-07-21
You can't watch youtube in your webbrowser?? Have you tried through totem?

---

### Post by lovinglinux on 2010-07-21
[http://flash-aid-extension.blogspot.com](http://flash-aid-extension.blogspot.com)

---

### Post by ECET on 2010-07-21
well, im on cable so dialup is not the problem....i have installed all updates required to watch video....and i can watch some videos...just not utube stuff. by other videos, i mean the adult version stuff. I get an error in the utube window saying source not found. But yet, when i go and log on with windows 7, everything plays then. So im obviously missing something or something is turned off. I am at my witts end.....

---

### Post by Jazzy_Jeff on 2010-07-21
You shouldn't be watching adult content....:D.

---

### Post by ECET on 2010-07-22
alright....nothing is working still........should i maybe delete/remove flash and then do a reinstall????.....anything constructive would be appreciated. Thanks......

---

### Post by Mick8882003 on 2010-07-22
Flash doesnt seem to work to well on 64 bit systems, at least it didnt for me, I am guessing that might be your problem, if not ignore.

---

### Post by lovinglinux on 2010-07-22
> **ECET said:**
> alright....nothing is working still........should i maybe delete/remove flash and then do a reinstall????.....anything constructive would be appreciated. Thanks......

Have you tried my extension? [http://flash-aid-extension.blogspot.com](http://flash-aid-extension.blogspot.com)

---

### Post by ECET on 2010-07-22
yes lovinglinux I went to site and nothing seems to be helping. I have buddies who just installed ubuntu and have no problems whatso ever playing utube vids. I dont have anything turned off that im aware of...ive followed all the advice here to no avail. So do you think maybe removing a package or something then reinstalling might help. I am running a 64bit system like someone else stated that flash seems to have problems with. so if you or anyone else knows of anything.....anything i can try, please advise. I appreciate all help. Thanks...

---

### Post by lovinglinux on 2010-07-22
What exactly is the error you get?

Create a new Firefox user profile and see if it works. Start Firefox with the profile manager to do that:

```
firefox -P
```

Then when can try to figure out what is the cause of your problem. 

Also type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by ECET on 2010-07-22
cool.....when i get off work, ill do this. I appreciate your help.....hopefully we/you can figure out what is going on. Again, thanks and I'll get back to you this evening.

---

### Post by Cavsfan on 2010-07-22
Also, have you tried the workaround?

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: "export GDK_NATIVE_WINDOWS=1" before the last line of text
(without the quotes)

Restart browser  and try it again.

I had to do this for any buttons to work on youtube.

This may or may not help. 

BTW thanks **lovinglinux** I installed your extension.

---

### Post by lovinglinux on 2010-07-22
> **Cavsfan said:**
> Also, have you tried the workaround?

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: "export GDK_NATIVE_WINDOWS=1" before the last line of text
(without the quotes)

Restart browser  and try it again.

I had to do this for any buttons to work on youtube.

This may or may not help. 

BTW thanks **lovinglinux** I installed your extension.

You are welcome. Also check [http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by Cavsfan on 2010-07-22
> **lovinglinux said:**
> You are welcome. Also check [http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)


Thanks! I bookmarked it! :D

---

### Post by noidian on 2010-07-22
If its your office, some have a proxy server. Do other streaming sites work. hulu, onlinetv..etc?

---

### Post by ECET on 2010-07-22
well....ive not tried hula.....the only videos i can play are a few "dirty" ones.....not all....I did this as a check to see if any vids would play and for some reason, some do play from these "dirty" websites.......im just interested in utube stuff......an if this means anything, i can play dvd movies on ubuntu....even downloaded ones.......thanks for any feedback

---

### Post by techunit on 2010-07-22
> **Mick8882003 said:**
> Flash doesnt seem to work to well on 64 bit systems, at least it didnt for me, I am guessing that might be your problem, if not ignore.

I agree with Mick8882003 entirely...

If you have a 64bit system you are bound to have problems... I don't agree with the reasons you are going to use flash video for but that isn't the point. purhaps installing the 32bit version will alleviate your problems. I have problems with flash all the time in 64bit but on my netbook no problems at all.

---

### Post by Cavsfan on 2010-07-22
> **techunit said:**
> I agree with Mick8882003 entirely...

If you have a 64bit system you are bound to have problems... I don't agree with the reasons you are going to use flash video for but that isn't the point. purhaps installing the 32bit version will alleviate your problems. I have problems with flash all the time in 64bit but on my netbook no problems at all.

I have a 64 bit system and I have never had any problem doing anything. Flash works great.
So, this problem has [COLOR=Red]nothing[/COLOR] to do with having a 64 bit system. Adobe temporarily 
suspended their development of Linux 64 bit flash, but the 32 bit flash works like a charm.

**lovinglinux** has a great FireFox plugin you can install (I did) and it works perfectly.
It is called FlashAid and it's on the very first post that **lovinglinux** put on this thread.
There is a place on the right side that page underneath **Stable Channel **that says "Automatic Install".
Just click on that if you haven't already. And if that doesn't fix it, there's something else wrong.

You should be using Shockwave Flash 10.1 r53 which is the latest version.
But, it's not because you have a 64 bit system...

And if you are using 64 bit flash 10.0 there is a _[huge security vulnerability.](http://harbhag.wordpress.com/2010/06/17/adobe-flash-player-10-1-64bit-beta-discontinued-for-linux/) _

---

### Post by lovinglinux on 2010-07-22
> **Cavsfan said:**
> I have a 64 bit system and I have never had any problem doing anything. Flash works great.
So, this problem has [COLOR=Red]nothing[/COLOR] to do with having a 64 bit system. Adobe temporarily 
suspended their development of Linux 64 bit flash, but the 32 bit flash works like a charm.

**lovinglinux** has a great FireFox plugin you can install (I did) and it works perfectly.
It is called FlashAid and it's on the very first post that **lovinglinux** put on this thread.
There is a place on the right side that page underneath **Stable Channel **that says "Automatic Install".
Just click on that if you haven't already. And if that doesn't fix it, there's something else wrong.

You should be using Shockwave Flash 10.1 r53 which is the latest version.
But, it's not because you have a 64 bit system...

And if you are using 64 bit flash 10.0 there is a _[huge security vulnerability.](http://harbhag.wordpress.com/2010/06/17/adobe-flash-player-10-1-64bit-beta-discontinued-for-linux/) _

I agree. Nevertheless, you might experience some issues with unresponsive controls in the 32bit that [can be easily fixed]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html").

About my extension, thanks for your comments.

---

### Post by DrDevice on 2010-07-22
Early on I stumbled upon this guide, really made getting multimedia set up easy.

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by Cavsfan on 2010-07-23
> **lovinglinux said:**
> I agree. Nevertheless, you might experience some issues with unresponsive controls in the 32bit that [can be easily fixed]("http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html").

About my extension, thanks for your comments.

You are welcome! You are definitely doing a lot of good work here!
I will always refer people to your plugin when I have a chance. :D

Hopefully Adobe will get their act together soon!

---

### Post by ECET on 2010-07-28
I truly apologize for not getting back sooner......Lovinglinux.....thank you very much, your link DID indeed help and now I am enjoying utube vids. I am glad there are so many helpful folks out there who enjoy freeing themselves from M$ and helping those of us who are attempting to do the same. Once again, thanks to all!

---

### Post by lovinglinux on 2010-07-29
> **ECET said:**
> I truly apologize for not getting back sooner......Lovinglinux.....thank you very much, your link DID indeed help and now I am enjoying utube vids. I am glad there are so many helpful folks out there who enjoy freeing themselves from M$ and helping those of us who are attempting to do the same. Once again, thanks to all!

You are welcome.

---

