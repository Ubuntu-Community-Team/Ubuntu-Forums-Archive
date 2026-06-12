---
title: "New sounds"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by johnnie1uk on 2010-11-30
Is it possible to add new sounds to be used as notifications. if so how do i go about it please.

---

### Post by Wobblybob on 2010-11-30
For Gnome desktop, the sounds for startup etc are stored here

/usr/share/sounds/ubuntu/stereo

you could just replace them with sound files of your own in .ogg format. If you want to do this via GUI interface open a root instance of the nautilus explorer by opening a Terminal [Applications], [Accessories], [Terminal] and  typing

gksudo nautilus

press enter and then enter your password, nautilus will open as root and you can navigate to the above folder to copy your new sound into it.

---

### Post by johnnie1uk on 2010-11-30
Thanks very much

---

### Post by Liverbones on 2010-11-30
Honestly, while that is a working solution, it's a bit clunky. It sounds like what you're wanting is a separate sound theme from the default Ubuntu sound theme, and this is almost as easy to do as simply replacing the sounds in the Ubuntu theme. Honestly, creating a new sound theme is remarkably easy.

To do it graphically, simply open Nautilus as root (gksudo nautilus) and go to /usr/share/sounds. From there, create a new directory for your sound theme and name it whatever you like (you could even copy the ubuntu/ directory as a template for your sound theme). Inside your new directory you will need a stereo/ directory and a plain-text file called index.theme. The index.theme file contains some information about your new sound theme, like so:

```
[Sound Theme]
Name=Theme Name Here
directories=stereo

[stereo]
OutputProfile=stereo
```

Save the index.theme file, then proceed adding your sound files to the stereo/ directory. The Ubuntu sound theme contains great examples of the name scheme for the files.

The only reason I'm suggesting this as opposed to the previous solution is because this one is rather bullet-proof: you're creating a brand new sound theme as opposed to overwriting one that's already there. This means that if, at any point in the future, the Ubuntu sound theme gets an update, your sound theme won't be overwritten by the update. When possible, I highly recommend keeping things separate as opposed to editing the themes that come with the system, just so you don't have to go back and redo anything.

Hope that was helpful. If you need me to explain anything further, just let me know. :)

---

### Post by johnnie1uk on 2010-12-02
Thanks again. very usefull information

---

### Post by johnnie1uk on 2010-12-09
Just put on some new sounds and all working great, thanks again.


A-Brit-in-spain.blogspot.com

---

### Post by hellblazer on 2010-12-09
whoops sorry! maybe I need glasses, or more sleep.

move along nothing to see here

---

