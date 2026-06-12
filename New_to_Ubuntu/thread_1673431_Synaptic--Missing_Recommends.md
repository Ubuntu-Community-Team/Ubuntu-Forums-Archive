---
title: "Synaptic--Missing Recommends"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by Wheel on 2011-01-22
Hi,
I have recently clean installed Maverick, done a little tweaking, and have been looking over everything.
Into Synaptic--Custom Filters--Missing Recommends, I see a list of 7 files.
Looks like I need to install these, but I'm not sure.

This file shows what Synaptic lists under missing Recommends:

[ATTACH]181734[/ATTACH]

Some of these I understand, some I don't.    What I'm thinking:

apt-doc seems useful.  Documentation is always good.

aptitude is likely a good idea, although most of my installs/removals I do in Synaptic, sometimes through the Software Center, and sometimes with apt-get via termial.  
(I have also read that switching back and forth between package management systems can cause some problems.)

manpages-pl seems useless to me since I don't speak Polish.

w32 codecs has something to do with multimedia audio and/or video codecs.  Is likely useful.

As to the other 3, I have no idea whatsoever.

Does anyone have a suggestion as to which of these I should install?
Which to ignore?
What's the down-side of NOT installing a "recommend"?

---

### Post by Frogs Hair on 2011-01-22
The list may vary depending on what you have installed . Aptitude was replaced by apt-get so there is no need to install it unless you need it.

I have a printer so there are packages unrelated to  my HP printer just because I have a printer , also no codecs are on my list due to having  gstreamer plug-ins installed .

If those packages turn out to be dependencies for something you may install in the future they will  be installed at that time.

---

### Post by Wheel on 2011-01-23
> Aptitude was replaced by apt-get so there is no need to install it unless you need it.OK.   I didn't realize that apt-get was a newer version of this tool.  As I'm  just learning my way through terminal work, this is helpful.  Thanks.

> If  those packages turn out to be dependencies for something you may  install in the future they will  be installed at that time.     That seems about right, but what I am concerned about is  that I may have installed something (via terminal) while forgetting to  also install the recommended additional files--and something** currently** installed does** not** have the required dependencies. 
If  I understand the difference between how Synaptic and terminal handle  packages, Synaptic makes it simple to mark those "recommends" and get  them safely installed, while terminal requires the user to manually  install these.  
Do I have that right?   
I may have forgotten to go back and install those afterwards.  

As near as I can remember, I have only used terminal to install 2 things since my recent install:
1)medibuntu repository
2)cli companion
and I can't remember if either of these suggested that I should install other files.

Does  anyone know if there is a connection between either of these 2 items  and the files listed as "Missing Recommends" (from the link in my  original post)?
Any comments about any of those 7 files would be appreciated.

---

### Post by Frogs Hair on 2011-01-23
When you install a package Ubuntu automatically builds the dependency tree , if there are missing dependencies or the packages are incompatible you will receive an error message.

---

### Post by JKyleOKC on 2011-01-23
> **Wheel said:**
> what I am concerned about is  that I may have installed something (via terminal) while forgetting to  also install the recommended additional files--and something** currently** installed does** not** have the required dependencies. 
If  I understand the difference between how Synaptic and terminal handle  packages, Synaptic makes it simple to mark those "recommends" and get  them safely installed, while terminal requires the user to manually  install these.  
Do I have that right?Not quite. All of these packages are "front ends" for the actual installer, which is "dpkg." Consequently all of them will automagically install any mandatory dependencies, or will not install the package at all if they cannot get them.

The differences between the various front ends are mostly cosmetic, and are to provide different amounts of information for different users. For example, Synaptic can show much more detail about a package than you see when using the Software Center, and both of those show more detail than you get from a simple terminal use of apt-get or dpkg. It's all part of giving you plenty of choices in the way you get something done.

---

### Post by matt_symes on 2011-01-23
Hi

Maybe this will clarify.

[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)

Kind regards

---

### Post by oldos2er on 2011-01-23
> **Wheel said:**
> OK.   I didn't realize that apt-get was a newer version of this tool.  As I'm  just learning my way through terminal work, this is helpful.  Thanks.


apt-get and aptitude are two different programs; but they are both front-ends to Ubuntu's APT system. aptitude is no longer installed by default but it's still available in the repositories. It was dropped from the install CD because of space considerations, nothing more.

---

### Post by Wheel on 2011-01-24
> When you install a package Ubuntu automatically builds the dependency  tree , if there are missing dependencies or the packages are  incompatible you will receive an error message. > All of these packages are "front ends" for the actual installer, which  is "dpkg." Consequently all of them will automagically install any  mandatory dependencies, or will not install the package at all if they  cannot get them.Thanks Frog's Hair & JKyleOKC.  
So I guess I won't be concerned about overlooking the recommends on install since APT is smart enough to prevent that.
Very nice!

> Maybe this will clarify.

[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)
Good info therein.  Thanks for that, matt_symes.

And thanks oldos2er.  It all boils down to having multiple choices for a given operation.

All in all,  this has left me feeling a bit more confident.  Even though there are a couple of files on my original list that I still don't understand, I'm not going to be losing any sleep stressing over them.

---

### Post by duanedesign on 2011-02-02
@wheel,
CLI Companion only has one dependency, the package **most**.

---

### Post by Wheel on 2011-02-03
> **duanedesign said:**
> @wheel,
CLI Companion only has one dependency, the package **most**.

Thanks.  That's good to know.

---

