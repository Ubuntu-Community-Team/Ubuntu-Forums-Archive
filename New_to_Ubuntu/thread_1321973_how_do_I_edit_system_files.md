---
title: "how do I edit system files ?"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by KarenAK on 2009-11-10
Ubuntu doesn't recognize my creative Zen x-fi mp3-player. 

So, following the advise on a blog [http://www.mossroot.com/worlds/2008/11/22/connecting-the-creative-zen-x-fi-to-linux/](http://www.mossroot.com/worlds/2008/11/22/connecting-the-creative-zen-x-fi-to-linux/) I tried to edit the files as instructed - but it wouldn't let me save the file.

Ok, I seem to remember something about having to give myself administrator rights - but I don't know how. I have used sudo in a terminal window - but how do I use it in Nautilus when opening a file ?

Any help is much appreciated - thanks in advance

---

### Post by philinux on 2009-11-10
Either

gksudo nautilus

or install nautilus-gksu then from the right click there is open as administrator

or 

gksudo gedit file

---

### Post by Merk42 on 2009-11-10
You can run Nautilus with gksudo nautilus, but what specific step are you having issues with?

---

### Post by KarenAK on 2009-11-10
hm..... does that mean I have to start Nautilus from the terminal window  ? Or start gedit there ? 

I see... ok, I thought I could just select the file in the browser and then somehow, somewhere open it as administrator.

So, whenever I need administrator rights I have to do things via the terminal window ?

(And while we're at it: what's the difference between sudo and gksudo ?)

Thank you for your quick replies :-)

---

### Post by philinux on 2009-11-10
> **KarenAK said:**
> hm..... does that mean I have to start Nautilus from the terminal window  ? Or start gedit there ? 

I see... ok, I thought I could just select the file in the browser and then somehow, somewhere open it as administrator.

So, whenever I need administrator rights I have to do things via the terminal window ?

(And while we're at it: what's the difference between sudo and gksudo ?)

Thank you for your quick replies :-)
Your choice really. Since i installed nautilus-gksu I've solved my problem.

You dont have to use the terminal. nautilus-gksu is what I use.

sudo or gksudo see here
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Really good resource.

---

### Post by KarenAK on 2009-11-11
That was very helpful - thank you :-)

I installed the nautilus-gksu package as you recommended but had to use the workaround

$ sudo cp /usr/lib/nautilus/extensions-1.0/libnautilus-gksu.so /usr/lib/nautilus/extensions-2.0/
$ killall nautilus


to get it working, but now it does !


(though my mp3 player still doesn't connect *sigh)

.....I wonder, will I have to do all these fine-tuning things again when I update to Karmic Koala ?

---

