---
title: "Video drivers for an old Dell?"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by kenny2009 on 2010-01-30
I have a Dell Optiplex GX150 desktop computer that I'd like to put Ubunut 9.04 on for my mom to use. I boot up with the liveCD so she can play with it and the first thing she notices is how big it is. The resolution is at 800x600 and she does not like it. My guess is that it doesn't come with video drivers. 

What do I need to do in order to get the resolution fixed? It needs to be at least 1024x728 (I think).

Whoever helps me gets a gold star =D  :KS


EDIT 2012-10-12:
Using this approach I get a resolution of 1280*1024:
[http://ubuntuforums.org/showpost.php?p=12292664&postcount=828](http://ubuntuforums.org/showpost.php?p=12292664&postcount=828)

---

### Post by tom.swartz07 on 2010-01-30
> **kenny2009 said:**
> I have a Dell Optiplex GX150 desktop computer that I'd like to put Ubunut 9.04 on for my mom to use. I boot up with the liveCD so she can play with it and the first thing she notices is how big it is. The resolution is at 800x600 and she does not like it. My guess is that it doesn't come with video drivers. 

What do I need to do in order to get the resolution fixed? It needs to be at least 1024x728 (I think).

Whoever helps me gets a gold star =D  :KS

Hey Ken,

Try looking in the display settings first to see if its just randomly set at a low level. 

system>preferences>display

Also, could you post the output of these two commands:

```
sudo lspci
```
```
xrandr
```

---

### Post by Michael Dooley on 2010-01-30
You might also try downloading the Dell jaunty install iso that can be found [[COLOR="Red"]here[/COLOR]]("http://linux.dell.com/files/ubuntu/jaunty/iso-images/"). I'd bet that Dell has included a variety of drivers that could be useful in your machine. It appears as if Dell has made a good faith attempt to let its' customers install a customized version of ubuntu.

---

### Post by kenny2009 on 2010-01-30
Tom, I'm trying to get this website to load on the linux box so I can copy & paste the results for you.

Michael, that is great news! I didn't know there was an ISO for dell computers like that! When I get the chance I'll DL it just in case I can't get this to work with the regular ISO.

---

### Post by tom.swartz07 on 2010-01-30
> **kenny2009 said:**
> Tom, I'm trying to get this website to load on the linux box so I can copy & paste the results for you.

Michael, that is great news! I didn't know there was an ISO for dell computers like that! When I get the chance I'll DL it just in case I can't get this to work with the regular ISO.

Sure! no hurry!
Another method you could use is to save it to a .txt file and throw it on a usb key or something to post from a faster computer.

It might just be a matter of setting your display correctly.


I would def suggest using the dell iso! As a Dell user myself, I know that some of the hardware is a bit finicky. See if that works, and let us know!

---

### Post by kenny2009 on 2010-01-31
Well the Dell ISO on my mom's computer didn't even give us an option to try out the LiveCD first... It just wanted to automatically install the OS. So I don't know if that has the drivers I need or not. I'm going to load up my old LiveCD and input those commands into terminal and copy & paste the results here for you.

We're not ready to install it yet until we know for sure we can get the drivers we need. (Plus I still need to back up her documents and photos)

---

