---
title: "gnome-look - why doesn't it work?"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by zcacogp on 2010-02-06
Chaps, 

This is the 'Absolute Beginner' forum, and I think this is probably a really stupid question. But I'll try ... 

I have never (well, really rarely) managed to install anything I have downloaded from gnome-look. I can go to the website, see something I like, download it and .... can't install it. 

I have struggled before, but ignored it. Now I am playing with cairo-dock, and apparently there are some great themes for this on gnome-look. I have a look, but still can't install what I download. 

Sequence goes like this: 

I download the package (for instance, 114880-plain-black.zip). I open cairo-dock, go to 'Manage Themes', and drag and drop the downloaded file (from my desktop, where I saved it) into the area which says "... or drag and drop a theme package here". The icon is dropped, but moves straight back onto the desktop from whence it came, and is not installed (at least, there are no new themes for me to see.) 

I can try unzipping the theme, which gives me a folder called "plain-black" on the desktop. Installing this has exactly the same effect - it won't install, and moves straight back to the desktop. 

The folder contains individual files, all of the form "*.svg". These won't install either. 

Am I being really thick? Am I missing a crucial step? What am I doing wrong? 

All help welcomed - thanks. 


Oli.

---

### Post by thunk77 on 2010-02-06
Hello,

I don't wanna sound patronizing or anything, but maybe the next time you seek help you should try a more descriptive thread title like "need help installing cairo dock themes" or sth..

This way people who know something about your issue are drawn to your thread, since the title is a bit more eye-catching. ;)

That said, maybe you'll find this interesting and enlightening (hopefully)

[HTML]http://maketecheasier.com/how-to-install-and-configure-cairo-dock-in-ubuntu-intrepid/2009/01/20 [/HTML]

Regards.

---

### Post by Orion8 on 2010-02-06
I don't know anything about Cairo dock, but I want to say I've often had trouble with gnome-look themes and icons as well.  What has worked most reliably for me is to unzip the downloaded file, then copy the resulting folder to ~/.themes or (~/.icons depending on which it is).  If your user does not have these folders you can make them using nautilus or the terminal.  Anyway, once this is done you can reopen the theme manager and the theme should be there.  Not always, but more often than anything else I have tried.  I know this should be the same as dragging the expanded folder into the theme manager but for me it seems to work better. On the other hand, I sometimes wonder if some of the themes on gnome-look are for other systems or somehow deficient -- quite often I can't get them to work...  When this happens too much, I give up and just use the themes and icons I can find in the repositories.  Good luck!

---

### Post by fabounet on 2010-02-06
Most of the Cairo-Dock themes I've seen on gnome-look were either for the 1.x version or poorly configured, except some, that have been integrated in the official list of themes.
So if you want themes for Cairo-Dock you coud just look in the Themes Manager, there are more than 30 themes available.
(jus in case, the current stable version is 2.1.3)

PS : if you can install the zipped theme from the Themes Manager for some reason, you can unzip it in ~/.config/cairo-dock/themes, and then open the Themes Manager and select this theme.

---

### Post by zcacogp on 2010-02-07
Chaps, 

Thanks for your answers. 

Thunk - fair point, but the problem is wider than just cairo-dock themes, hence the slightly less-precise title. But you're right, it was a lousy thread title (written late at night, in slight frustration!) However, it did produce the desired result ... 


... 'cos fabounet's answer was very helpful! Thanks. That worked. It turns out that the themes I downloaded weren't that great, but your instructions did allow me to install them. Thank you. As it was, I didn't have any themes in the list of themes which were there when I installed cairo-dock - I don't know why. I am wondering whether I didn't install something correctly. 

Orion8 - good to know that I am not the only one who struggled. I'll try your instructions next time I find a theme in gnome-look which I like the look of. 


Oli.

---

### Post by fabounet on 2010-02-07
you need the 2.1.3 version available on Launchpad since the domain name cairo-dock.org is temporarilly unavailable, so previous versions don't have themes.

---

### Post by zcacogp on 2010-02-08
fabounet, 

Ah. now that **IS **helpful - thanks. I've updated Cairo-dock to the version you mentioned (2.1.3), and it looks significantly better bolted-together than the version I was using before (2.0, I think.) With lots of themes! And, critically, a workspace switcher. 

I think I now need to go and play around with it a little and see whether I can configure it to do exactly what I want. (Sadly I can't do that at the moment - this is being written on a particularly vile WinXP laptop provided at a client site ... and I am rembering afresh how much I dislike MS products.) 

Thanks for your help, both on this and my other thread (about rebuilding Gnome panels).  


Oli.

---

