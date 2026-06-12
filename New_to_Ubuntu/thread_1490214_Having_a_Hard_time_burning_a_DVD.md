---
title: "Having a Hard time burning a DVD"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by ChubbySauce on 2010-05-22
using k3b


cannot find disk volume




went into set up permissions under settings drop pane

clicked everything that didnt say burn cause it wouldnt let me, figured that might be the permission thing I have to click for it to find the volume didnt work


verrrry frustrated with this Ive been trying to burn a dvd in ubuntu forever, it really shouldnt be this difficult. I wish there was a decent youtube tutorial.

Ive checked forum questions on this, they always seem to end with someone still asking a question after trying to figure this out, can someone please solve this with me??

---

### Post by ubudog on 2010-05-22
Why don't you try Brasero that comes with Ubuntu?  I've never had a problem with that in my 4 years of using Ubuntu.

---

### Post by ChubbySauce on 2010-05-22
NOW brasero is giving me a problem, installing some plugin I just downloaded in synaptic


didnt work


ubuntu has such stability, but completely lacks when it comes to media functions.

ugh this is just horrible I am sorry for venting you dont know how much trouble Ive gone through trying to burn a simple DVD

---

### Post by ubudog on 2010-05-22
Try this:  Open a terminal (Applications>Accessories>Terminal) and type in the following ```
sudo apt-get install ubuntu-restricted-extras && killall gnome-terminal
``` press enter.  Type your password (you will not see it) and press enter.  When it is done installing, the terminal window will close.  Then, restart your computer and try to burn the DVD again.  This will install some media codecs and plugins, etc.

---

### Post by ChubbySauce on 2010-05-22
I can do something as intricate as installing and running windows in VMware just fine, yet when it comes to the simple process of burning a DVD in ubuntu it becomes an almost physically painful task.

There are all theses files and plugins you have to install to accomplish this feat, all this configuring and running through the terminal. YET all of that is just to taught you.

all of that is simply in vain.

is it so much to ask, so much to ask for a program that can accomplish video burning without having to do all theses fruitless life draining tasks that amount to nothing.

---

### Post by ubudog on 2010-05-22
I'm afraid you have to use the terminal a lot in Linux.  But it is a good tool.  Did you try it?

---

### Post by ChubbySauce on 2010-05-22
somewhat worked, played on my son's portable dvd player not on my sony DVD player however

let apologize for that, it's been a reoccurring problem until now to an extent.

I've just been able to count on ubuntu for anything but this but it did play on the portable dvd player, not the sony thats odd

---

### Post by ChubbySauce on 2010-05-22
also there was green squares of what appear to be encoding errors Im thinkint this is because I didnt click on north american format Im trying that now

---

### Post by ChubbySauce on 2010-05-22
worked thanks much

---

### Post by madmax75 on 2010-05-22
Yeah, I've found both K3B and Brasero to be abysmal. They just don't work. I believe they are supposed to be used to burn a CD/DVD, right? In my experience, they do everyhting but that - they keep checking and milling and churning the data and heat up the CPU into boiling points, but you never actually get to the burning part.  I prefer Xfburn. Simple, easy, straightforward, does the job.

---

### Post by ubudog on 2010-05-22
> **ChubbySauce said:**
> worked thanks much

You're welcome.  If you have any more questions about Ubuntu, just PM me or send me an email.

---

