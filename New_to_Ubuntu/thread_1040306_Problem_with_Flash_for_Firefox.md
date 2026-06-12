---
title: "Problem with Flash for Firefox"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by rooski on 2009-01-15
Ok, so yesterday I installed Ubuntu 7.10 on my laptop because I managed to lock myself out of Windows. haha

Anyway, Once I installed it I couldn't see anything that needed Flash and I couldn't play mp3s.  I got the latter problem corrected thanks to a guy on another forum.  I had to go into the repositories and install a bunch of stuff then download and install a codec.

He thought that what I had done should fix the Flash problem, but it didn't.

Here's where I'm at.  When I would go to a website, other than YouTube, that had something using Flash it would tell me I was missing a plug-in. YouTube would give me a message where the video would normally be saying that I needed the latest version of Flash. The two options I was given on non-YouTube sites were flashplugin-onfree and swf gnash.  First I tried installing flashplugin-nonfree but it said it couldn't find the codec.  

So then I tried installing the gnash thing.  It said it installed but still nothing.  The only change was that now I no longer got messages telling me I needed to install flash.  Instead, anywhere something was using Flash I'd see a white box instead of whatever was supposed to be there.

The guy that helped with the mp3 thing told me I needed to unintall the swfdec stuff.  But when I went into Synaptic to do that it said none of the stuff was installed.  That's when we moved onto the mp3 thing and he said that it should've been fixed, but since it wasn't I should ask here.

I did a search and found this thread:
[http://ubuntuforums.org/showthread.php?t=1038983&highlight=Flash](http://ubuntuforums.org/showthread.php?t=1038983&highlight=Flash)

Now, the Ubuntu I installed was 7.10.  It told me I needed updates, though, and installed 256 updates.  I'm not sure if it's still 7.10 or if it updated to 8.04 (and I don't know how to check what version I'm running).  So, what I'm wondering is will the fix mentioned in the above thread work for me even if I'm on 7.10?  And if not, is there a fix I can use or do I need to update to 8.04 (and if so, where can I find that)?

---

### Post by Terl on 2009-01-15
Since it is such a fresh install, I would recommend you download 8.04 and do a clean install.  It would save potential upgrade headaches and be easier.

Once it is installed a nice ```
sudo apt-get install ubuntu-restricted-extras
``` will install flash for you as well as mp3 support and other codecs and fonts.

---

### Post by gettinoriginal on 2009-01-15
+1 for that idea, that way you will have the latest LTR (long term release), and all the video and sound codecs available.  :P

---

### Post by mapltux on 2009-01-15
if you're handy with the command line  (Applications -> Accessories -> Terminal) you might wanna try

lsb_release -a 

to know which ubuntu distro u have installed :)

cheers!

---

### Post by rooski on 2009-01-15
Thanks.  Quick question.  When I burn the disc, can I use a CD-R like I would to burn a CD or do I have to burn on a DVD (which I don't think my computer does)?

edit: I did the command line thing.  I'm still using 7.10.

---

### Post by mapltux on 2009-01-15
I guess burning a CD is just normal with ubuntu as with any other OS.. I am biased to think its better :)

Just insert the cd and there's an auto Disc Burning that works (Brasero for 8.10) which will let you search within the directory structure and choose what you wish to burn.

---

### Post by gettinoriginal on 2009-01-15
Just make sure you are getting the ISO, and burn it at a slow speed. :P

---

### Post by rooski on 2009-01-15
So, I got a Linux magazine that came with Ubuntu 8.10.  Is this, since it's not a LTR, going to quit getting updates on it eventually?  It says it has 600 packages on it, so I dont have to do a lot of downloading.  I'm tempted to use this to cut out the downloading, but if the 8.04 is decidedly better I'll go ahead and install it (assuming my burn goes ok).

---

### Post by rooski on 2009-01-15
Got 8.04 installed and updated.  Flash is finally working.  Thanks for all the help.

---

### Post by BertP on 2009-01-16
> **Terl said:**
> Since it is such a fresh install, I would recommend you download 8.04 and do a clean install.  It would save potential upgrade headaches and be easier.

Once it is installed a nice ```
sudo apt-get install ubuntu-restricted-extras
``` will install flash for you as well as mp3 support and other codecs and fonts.

I've just installed 8.04 bet when I execute ```
sudo apt-get install ubuntu-restricted-extras
```

I get
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

```

any idea what the problem could be?

---

### Post by kansasnoob on 2009-01-16
In what version of Ubuntu?

You need to have certain repositories enabled in different versions.

Like in 8.04.1 you need Hardy partner.

---

### Post by mrbiggbrain on 2009-01-16
> **rooski said:**
> So, I got a Linux magazine that came with Ubuntu 8.10.  Is this, since it's not a LTR, going to quit getting updates on it eventually?  It says it has 600 packages on it, so I dont have to do a lot of downloading.  I'm tempted to use this to cut out the downloading, but if the 8.04 is decidedly better I'll go ahead and install it (assuming my burn goes ok).


i dont really think that 8.04 is any better, its supported longer (3 years i belive)

8.04 was released in the 4th month of 2008, and 8.10 was released in the 10th month 0f 2008.

8.04 will be supported untill 11.04 comes out in the 4th month of 2011, well 8.10 will be supported till the 4th month of 2009, which just happens to be when 9.04 comes out :-) so you can keep updateing from one release to another every 6 months, becuse every 4th and 10th month of the year ubuntu gets a new version, once a year for a LTR, and once a year for a development release

---

