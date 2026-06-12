---
title: "Newbie Here"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by boop18224 on 2008-12-14
i just purchased a dell mini and clicked wrong box and ended up with ubuntu on it. I am trying to figure out all the different features to use it. I am used to windows xp and this is all foriegn to me. Can someone tell me where to turn the sound up at. I turned it up at the top and still can't hear it well. Is there somewhere else I should go to do this?

---

### Post by northern lights on 2008-12-14
> **boop18224 said:**
> i just purchased a dell mini and clicked wrong box and ended up with ubuntu on it.This might just have been the best "mistake" of your life...

> **boop18224 said:**
> Can someone tell me where to turn the sound up at. I turned it up at the top and still can't hear it well. Is there somewhere else I should go to do this?
Three options:
- using VLC instead of Rhythmbox/Amarok/YouNameIt gives you up to 4 times amplification
- check whether everything's up by running *alsamixer* from a terminal (Applications > Accessories > Terminal)
- use external speakers / an external amp

P.S. It is highly recommendable to use a descriptive topic title, such as "how to increase volume?" / "how do i get my laptop speakers louder?" rather than "Noob here" or "A problem"...

---

### Post by ibizatunes on 2008-12-14
Welcome, 
+1 for this could be the best mistake of your life ;)

I would install resticted extras,
so you can play mp3, flash, java etc application

Now for installing codecs and some applications we need mediubuntu repository too which could be added by issuing the following command in the terminal window (Applications -> Accessories -> Terminal ):

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

and

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

then 

```
sudo apt-get install faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0
```

then

```
sudo apt-get install ubuntu-restricted-extras
```


This quite a good site 

[http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html](http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html)


If you go to sites like adobe or skype, make sure you install a .deb version of the software you require!

---

### Post by tuskenraider on 2008-12-14
hey newbie... 

welcome to the fantastic world of ubuntu.  i would also go to the add/remove section and download virtualbox.  then install a virtual windows xp, so you can use windows when you need it.  but ill go ahead and warn you... youll find yourself using it less and less and less. just so you know.  

again welcome. and enjoy your ubuntu!!!  :guitar:

tusken

p.s good call in coming to the forums for help.. we here will be glad to help you with just about anything you come across.

---

### Post by fooman on 2008-12-14
> **boop18224 said:**
> ...someone tell me where to turn the sound up at. I turned it up at the top and still can't hear it well. Is there somewhere else I should go to do this?

double-click on the speaker/volume icon in the top panel.  that will bring up the sound (alsa) mixer....check that the sliders are all turned up.

hope you enjoy ubuntu...may all your mistakes be that rewarding. :p

---

### Post by northern lights on 2008-12-14
> **fooman said:**
> double-click on the speaker/volume icon in the top panel.

> **boop18224 said:**
> ...I turned it up at the top and still can't hear it well...

You think the OP just moved the initial slider? I hadn't figured that.

---

### Post by Kellemora on 2008-12-14
Hi boop

Welcome to the Wonderful World of Ubuntu!

I'm new also, and in less than 1 month after discovering Ubuntu have converted my entire office over to it.

I'm chiming in here to Apologize for the responses you received to your first post.
I see how totally OVERWHELMING the responses given will seem to you right now!  I know they were to me and I came here on purpose, hi hi.

Ubuntu Geeks often forget that us noobs have no idea WHAT a terminal is, other than something that happens after a bout with cancer.

The post by Fooman will be more helpful to you right now!
If the sound is still not loud enough for you, there are methods to make it rattle your window panes.

I just don't want to see you scared away by all this techno-geek talk on your first post here.

You will LOVE Ubuntu once you get used to it.

The nicest part is that nearly everything in Linux is FREE.
If you are used to msOFFICE for example, you will find OpenOffice to be much more powerful, and more user friendly as well.  Things in Open Office Writer for example are where they should be.  Change page margins for example is under Format Page where it belongs, not under FILE as msWord has it located.  It's NOT a File function so why they put it there is beyond me.

There are a LOT of really NEAT things you can do in Ubuntu that you cannot do in Windows, but I don't want to dump them on you on day 1 of your journey!

Just look at it this way, for everything you can do on Windows and HAVE TO do it THEIR way, in Linux there are many ways to do the same thing and many programs you can choose from to do it YOUR WAY or the way you would have always loved to do it.

Again, Welcome to Ubuntu

TTUL
Gary

---

### Post by 73ckn797 on 2008-12-14
> **Kellemora said:**
> Hi boop

Welcome to the Wonderful World of Ubuntu!

I'm new also, and in less than 1 month after discovering Ubuntu have converted my entire office over to it.

I'm chiming in here to Apologize for the responses you received to your first post.
I see how totally OVERWHELMING the responses given will seem to you right now!  I know they were to me and I came here on purpose, hi hi.

Ubuntu Geeks often forget that us noobs have no idea WHAT a terminal is, other than something that happens after a bout with cancer.

The post by Fooman will be more helpful to you right now!
If the sound is still not loud enough for you, there are methods to make it rattle your window panes.

I just don't want to see you scared away by all this techno-geek talk on your first post here.

You will LOVE Ubuntu once you get used to it.

The nicest part is that nearly everything in Linux is FREE.
If you are used to msOFFICE for example, you will find OpenOffice to be much more powerful, and more user friendly as well.  Things in Open Office Writer for example are where they should be.  Change page margins for example is under Format Page where it belongs, not under FILE as msWord has it located.  It's NOT a File function so why they put it there is beyond me.

There are a LOT of really NEAT things you can do in Ubuntu that you cannot do in Windows, but I don't want to dump them on you on day 1 of your journey!

Just look at it this way, for everything you can do on Windows and HAVE TO do it THEIR way, in Linux there are many ways to do the same thing and many programs you can choose from to do it YOUR WAY or the way you would have always loved to do it.

Again, Welcome to Ubuntu

TTUL
Gary

+1 Great post. There are ways to accomplish some things without the need to become a quickly confused newbie by all the techno talk.

---

### Post by Shhnap on 2008-12-14
Unless you happen to have won a million dollars by mistake, I too believe that this is the best mistake of your life.

My advice would be to go swimming in the wonderful world of Ubuntu. Firstly, you are on a Linux operating system. SO go find out what linux is all about.

Install programs by searching through going Top Menu->Applications->Add/Remove...  
You will find everything you ever need.

Search these forums to learn how to play dvd's.

Start using the terminal, the most powerful thing on you new machine.

Install compiz so that your desktop becomes a cube and you can show off to all your windows friends. 

Once again: welcome to the world of Ubuntu!! ):P

---

