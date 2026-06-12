---
title: "Error Opening Trash/Unable to Unmount External Media"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by beanpop on 2009-06-22
Well, I really didn't want to resort to posting on this forum to try and find a resolution to my problems but I have spent hours upon hours searching Google for absolutely anything that would work and now I am completely burnt out and figure nothing can solve them.

First I will explain the two main problems that I am having, then I will attempt to recreate the long and drawn out series of events that possibly caused them and what I have done to try and fix them.

**Problem #1**: I am unable to unmount any external media. Every time I try to unmount my external hard drive or my different USB flash drives, I get the following error:

```
is not in the fstab (and you are not in root)
```I don't always get this error message, it is actually completely random as far as I know.  The last time that I was able to sort of recreate this problem was after I had been working on moving some files from my internal hard drive to my external.  After I was finished and needed to unmount the external, I got the error.  I ended up just shutting down and once everything was completely off, I unplugged it.  Right after that I booted my computer back up again and as soon as it was fully loaded I plugged in a USB drive in an attempt to get the error again.  This time it unmounted with no problems, even after the 4th or 5th time I tried it (and after deleting a few files and moving them back and forth).  I honestly don't think that I did anything different but for some reason it only happened with the first drive. 

**Problem #2**: I am unable to access my trash folder except when using Konqueror and even then all I am able to do is view the files that are currently in that folder.  The error that I get when trying to open the trash folder by using every method I know (the icon disappeared and won't show up when I attempt to re-add in the panel on the bottom right; using the file manager, Nautilus; using the terminal) is the following:

```
The folder contents could not be displayed.

Sorry, couldn't display all the contents of "trash": Operation not supported.
```[B]

What Originally Happened:[/B]  This part is where it gets a little hazy because I have done SO MUCH trying to fix so many different things in the last few days.  So, I am going to start from the beginning and do my best to not write a novel:

I was looking for a Twitter application that was supported by Ubuntu that would also allow me to update Facebook at the same time.  After doing a lot of research I was under the impression that Gwibber would be my best bet.

The problem is, as I am sure you all know, Gwibber is not supported by version 8.04/Hardy Heron.  I didn't want this to stop me so I dived into the world of Linux and learned how to use the terminal and install tarballs and what a package was and how to use Synaptic Package Manager etc etc etc.  I can't say that I know everything, but I learned enough to where I installed the Gwibber application far enough that it gave me an icon under my Applications drop down and only gave me the error:

```
ImportError: No module named webkit
```So then I googled webkit and realized that I just needed to install that package.  But that deb file wouldn't install because of my version...so I tried to manually install webkit.  I started trying and every time I got an error about a missing package after using ./configure I would search for the package in Synaptic and install it before running ./configure again.  This was a very long drawn out process and finally I got stuck with the following error:

```
Error: Package requirements not met (libsoup-2.4 >= 2.25.91)
Requested: 'libsoup-2.4 >= 2.25.91' but version of libsoup is 2.4.1

Consider adjusting PKG CONFIG PATH environment variable if you installed software in a non-standard prefix.

You may set environment variables LIBSOUP_CFLAGS and LIBSOUP_LIBS to avoid the need to call PKG_CONFIG.
```First I checked to see what version of libsoup I had installed, and it was the older version so I went ahead and marked the 2.4 to update.  Tried running ./configure again and I got the same error message.  This is when I think everything got messed up to begin with - I went back into Synaptic and marked the previous version of libsoup to UNINSTALL and it popped up asking me if it was okay to uninstall a list of all these other packages.  I really was not familiar enough to understand what it was asking so I just clicked yes like I had been and it took about 15 minutes to finish uninstalling everything.  After that I was unable to even access my files because (after doing even more google research) Natilus had been uninstalled in that long list of packages.  

I have since reinstalled BOTH versions of libsoup, but unfortunately that doesn't bring back everything that I accidentally uninstalled and/or possibly deleted.  And I still can't get webkit to install because I continue getting that stupid error about libsoup even though I have the version it is asking for...

So, in conclusion...I am still not able to install Gwibber because I can't install webkit because apparently my libsoup packages are not correct.  And because I tried to fix THAT problem, I can only unmount my removable media half of the time and I can't access my trash folder at all.  At least I think that is everything...if I find anything else I suppose I will edit this post or at least reply to the thread.

I hope that this is the correct section of these forums for my question. I am also very sorry that this problem is so in depth and ridiculously long. ANY help will be appreciated...

-----------

ETA: I also wanted to post the error message I just got when trying to open trash (in Natilius) which is different from before:

```
Sorry, couldn't display all the contents of "trash": Operation not supported
```

Also, I was able to access the Trash folder (located at "/home/beanpop/.local/share/Trash/files") but I have no way to 'empty trash' because when I right-click the Trash icon in Natilius the 'empty trash' selection is not available and I can't click it.  When I right click on any of the files in the above 'trash' location, the only option it gives me is to move to Trash.....which, yeah I did try that and it deleted all of the files and then they reappeared immediately.

---

### Post by beanpop on 2009-06-22
bump.

Guys, I realize that this post is incredibly long but are you really meaning to tell me that NO ONE has every had any of these problems? Please help...

---

### Post by utchanovsky on 2009-07-01
Sorry, couldn't display all the contents of "trash": Operation not supported
I'm facing same problem too. This is happen after upgrading my system (jaunty). Anyone can help for this? thx

---

### Post by utchanovsky on 2009-07-01
I'v tried this
[http://ubuntuforums.org/archive/index.php/t-906507.html](http://ubuntuforums.org/archive/index.php/t-906507.html)

But still have problem

---

