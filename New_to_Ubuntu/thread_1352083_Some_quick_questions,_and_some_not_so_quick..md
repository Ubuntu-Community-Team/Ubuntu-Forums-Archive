---
title: "Some quick questions, and some not so quick."
date: 2009-12-11
forum: New to Ubuntu
---

### Post by sparky8251 on 2009-12-11
I’ve been working with Ubuntu since '08 and have recently moved to karmic form intrepid. In Karmic I found out that you can try the new gnome-shell. When I run “gnome-shell --replace”
I get an error along the lines of:

      JS LOG: Loading tweener.js
      JS LOG: Loading tweenlist.js
      JS LOG: Done loading tweenlist.js
      JS LOG: Done loading tweener.js
      JS LOG: Loading equations.js
      JS LOG: Done loading equations.js
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

I'm sorry that I could not get the exact error message and my computer is currently not connected to the internet due to my next problem, but this one is almost and exact copy, there is only more above the error I have shown but none of it deals with any type of error I know of. If Any one could tell me how to fix the gnome-shell error I would be thankful.

As stated earlier my next problem pertains to my internet connection. I still have dial-up and therefore need a modem but the only one I have is a lucentwin modem, which I have heard is full of problems. If anyone could suggest a proper modem for me to purchase that works with karmic I would be greatful.

Another problem is that I use a ATI video card and I can't install the propritary drivers. If this has changed recently let me know but if not could you tell me if nVidia drivers work on karmic and which card i should purchase.

And finally my last question is how do I get my multimedia function keys to work in KDE. They work fine in gnome which was installed by default in Ubuntu. When I change my session to KDE from gnome my volume up and down function keys no longer work along with mute, skip forward, skip back, play/pause, and stop. If someone could help me fix this issue I would appreciate it.

Also if this thread does not belong in this forum please tell me where to put it instead.

---

### Post by sparky8251 on 2009-12-11
bump. Anyone going to help me?

---

### Post by northern lights on 2009-12-11
As for the graphics issue - what exact ATI model do you own?

It should not be necessary to purchase a new graphics card, but if you were to look for a cheap compatible nvidia model the 7XXX series probably has the best price/value ratio currently on the market.

Further, it is advised to use a descriptive topic title. Titles along the lines of "Some questions" or "I have a problem" do not really tell anything about the content of the thread...

---

### Post by sparky8251 on 2009-12-13
Yeah, I probably should have had a better title, but I would not know what to call it. My graphics card model is the ATI Radeon x1250 of the ATI Radeon x1200 series. Thanks for the info on a compatible nVidia card, I'll look into it.

---

### Post by northern lights on 2009-12-14
The x1200 series has an R500 core and has been moved to legacy support by ATI. The new catalyst 9.4 does not support these models and the older catalyst 9.3, which does support them, does not work with the new xorg in Jaunty or newer. Hence while under Intrepid you could have 3D acceleration, under Jaunty or younger you won't with this model.

Sorry, mate.

---

### Post by clhsharky on 2009-12-14
HI

I have  a ATI R500 card, and 3D works very nice on radeon open source stack. Native games, google earth, compiz in Jaunty and Karmic. No propritary driver needed.

 Avoid win and soft modems, Hardware Based modems is the way to go.
Like this
[http://www.newegg.com/Product/Product.aspx?Item=N82E16825164005](http://www.newegg.com/Product/Product.aspx?Item=N82E16825164005)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16825104007](http://www.newegg.com/Product/Product.aspx?Item=N82E16825104007)

Sharky

---

### Post by m3wolf on 2009-12-14
> WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported! This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported! This is an application bug!
gnome-shell is not officially released yet so this is most likely just a straight up bug that will be fixed later.

---

### Post by sparky8251 on 2009-12-14
Thanks for the explanation on the ATI video card. I will do some studying on hard ware based modems, thanks for the tip. Finally thanks for the response on gnome-shell, I hope they do some work on it and get it working properly.

---

### Post by sparky8251 on 2009-12-15
I have one problem left, how do I get my multimedia keys to work in KDE such as volume up and down and mute, skip forward, skip back, play/pause, and stop. If anyone could help me with this I would be thankful.

---

### Post by northern lights on 2009-12-15
> **sparky8251 said:**
> I have one problem left, how do I get my multimedia keys to work in KDE such as volume up and down and mute, skip forward, skip back, play/pause, and stop. If anyone could help me with this I would be thankful.

Install *xbindkeys*.```
sudo aptitude install xbindkeys
```

---

### Post by sparky8251 on 2009-12-15
Thank you very much.

---

