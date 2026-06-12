---
title: "Latest software updates"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by jnmykn on 2009-12-15
Hi again

Presently using Ubuntu 8.04.  One of applications that I use is F-Spot, its version 0503.  Unfortunately it cannot handle Raw files for panasonic cameras.  However if I go to the F-Spot site it says the latest version is 0615, and that can handle Raw Panasonic files - just what I want.  

My problem is if I use the Synaptic Package Manager to upgrade to the latest version it tells me the latest F-Spot update is 0503?  Why is this?  Is there a "simple" workaround.  I have downloaded the 0615 package thinking to upgrade it myself but the generic installation instructions are way beyond my capabilities. Dont even understand them, never mind implement them!

Thanks  -  John

---

### Post by ibuclaw on 2009-12-15
> **jnmykn said:**
> Hi again

Presently using Ubuntu 8.04.  One of applications that I use is F-Spot, its version 0503.  Unfortunately it cannot handle Raw files for panasonic cameras.  However if I go to the F-Spot site it says the latest version is 0615, and that can handle Raw Panasonic files - just what I want.  

My problem is if I use the Synaptic Package Manager to upgrade to the latest version it tells me the latest F-Spot update is 0503?  Why is this?  Is there a "simple" workaround.  I have downloaded the 0615 package thinking to upgrade it myself but the generic installation instructions are way beyond my capabilities. Dont even understand them, never mind implement them!

Thanks  -  John

F-Spot 0.6.1.5 is in Ubuntu Lucid, the next system release planned for April 2010.


I've just had a look at the F-Spot site, and see that RAW images have been supported since 2006/2007. Which part were you looking at?

How exactly "doesn't it work"? Error messages?

Regards
Iain

---

### Post by synapsys on 2009-12-15
You are stuck with the version in the repositories unless you want to install it yourself. Installing from source isn't as hard as you think it is. You will have to use the command line (scary I know).

Here's a nice little tutorial to get you started:

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by jnmykn on 2009-12-15
Hello Again

Thanks for the replies.  

Tinivole - Nikon (and possibly others are supported) ie NEF files, but Panasonic RW2 (from memory) are not. Although I do have a Nikon, my fav camera is a Panasonic!

Synapsys - Thanks for the link, will give it a try.

Best Wishes  -  John

---

### Post by camporter1 on 2009-12-15
I believe the version of f-spot you're looking for might be in karmic-proposed, although that repo is used mainly for testing! You can follow the directions here: [https://wiki.ubuntu.com/Testing/EnableProposed]("https://wiki.ubuntu.com/Testing/EnableProposed") if you would like to add the version of f-spot you need. If you don't want any of the other updated packages in propsed, only update f-spot, and then disable the proposed repo again. I believe this will do what you need.

EDIT: Sorry, I didn't notice you were running 8.04. You can always upgrade to karmic, and then follow the steps above, otherwise you will have to build it yourself like others have mentioned.

---

### Post by ibuclaw on 2009-12-15
> **jnmykn said:**
> Hello Again

Thanks for the replies.  

Tinivole - Nikon (and possibly others are supported) ie NEF files, but Panasonic RW2 (from memory) are not. Although I do have a Nikon, my fav camera is a Panasonic!

Synapsys - Thanks for the link, will give it a try.

Best Wishes  -  John

Bah - IMO Nikon are much better quality =)

I'll see if f-spot can be backported. If not, you'll have to wait until April, if you choose to upgrade to the next Ubuntu LTS.

Regards
Iain

---

### Post by ibuclaw on 2009-12-16
@OP - and anyone who is still on Hardy and wants support for panasonic raw images in f-spot.

OK - I backported the rw2 patches, and uploaded it to my ppa.

[https://launchpad.net/~tinivole/+archive/ppa?field.series_filter=hardy](https://launchpad.net/~tinivole/+archive/ppa?field.series_filter=hardy)

Add the Hardy deb lines to your sources.list file and update.
Fingers crossed, touch wood, you should be able to use your panasonic camera now. :)

Regards
Iain

---

