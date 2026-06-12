---
title: "movie player not playing movies (avi, mpeg, mov)"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by mjp29 on 2009-09-20
Perplexed

Movieplayer is suppose to be pretty darn good at playing files that are .avi, .mpg, or .mov   (right?)

However, any of those files I email to my Ubuntu box (from my Mac os x box where they do play) won't play.

Movie player quickly opens and for a split second I think it's going to play the little movie (be it .avi, .mpg, or .mov  i've tested all 3) for a split second it opens and then just quits (vanishes).

?

---

### Post by AMDBuntu on 2009-09-21
Here's how I setup Totem (movie player)...

Go to the package manager and remove totem-gstreamer. Install totem-xine.
You should have the non-free repository turned on as well. 
Goto: system>administration>software sources>third party software - then check box

Next go to the Ubuntu Restricted formats page and follow the instructions. You should be able to play anything after this. Here's the link:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Reboot after installing these codecs.

Note: When you enter a DVD, you may automatically be offered Totem, which may be the wrong version and not work. Select Totem (xine) instead.

Totem, codecs, DVD, Won't play, restricted formats, plugins, movies, install

---

### Post by mjp29 on 2009-09-21
ok thanks - i'll try that this evening when i get back to the ubuntu machine

---

### Post by kevdog on 2009-09-21
You may also have to install the gstreamer good, bad, ugly plugins or libs.

---

### Post by mjp29 on 2009-09-21
> **AMDBuntu said:**
> Here's how I setup Totem (movie player)...

Go to the package manager and remove totem-gstreamer. Install totem-xine.
You should have the non-free repository turned on as well. 
Goto: system>administration>software sources>third party software - then check box

Next go to the Ubuntu Restricted formats page and follow the instructions. You should be able to play anything after this. Here's the link:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Reboot after installing these codecs.

Note: When you enter a DVD, you may automatically be offered Totem, which may be the wrong version and not work. Select Totem (xine) instead.

Totem, codecs, DVD, Won't play, restricted formats, plugins, movies, install


When trying to turn on non free repository, I get to "Third-Party Software" and 2 files (one ends with ubuntu jaunty & other file ends with ubuntu jaunty too) appear.  when i click to add both of those i get a message asking for an APT line (to enter)  - ?

---

### Post by jmszr on 2009-09-21
mjp29,

You need to install:```
sudo apt-get install ubuntu-restricted-extras
```

And then you need to install Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) .

Then make sure you install:```
sudo apt-get install libdvdcss2
```

And if you have the 32-bit version of Ubuntu:```
sudo apt-get install w32codecs
```  

If you have the 64-bit version of Ubuntu:```
sudo apt-get install w64codecs
``` 

Then install the VLC media player:```
sudo apt-get install vlc
```

VLC will play almost any format.

---

### Post by mjp29 on 2009-09-21
Thanks for the code but this time I'm going to try to fix it without using Terminal.

I'm sure your code is correct, but the other day I entered so much code into terminal that I screwed something up on the cache.  I'm only testing this box, so I did a full reinstall of Ubuntu and this time trying to find solutions without code initially.

Thanks for your post reply.

---

### Post by jmszr on 2009-09-21
mjp29,

You can install both "ubuntu-restricted-extras" and"VLC" in either Applications > Add/Remove or System > Administration > Synaptic Package Manager .

Edit: I'm thinking that perhaps AMDBuntu was actually referring to System > Software Sources > Ubuntu Software > Proprietary drivers for devices (restricted) and Software restricted by copyright or legal issues (multiverse). The boxes in front of those need to be checked. Or perhaps I'm mistaken as to what he meant.

---

