---
title: "Farm town not working?"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by kb010 on 2009-07-23
So this is probably a stupid question...
but.

My mom is trying to run the Facebook app Farm Town. I just installed Ubuntu 9.04 on her computer today (Windows crashed--imagine that.)

I am using Mozilla Firefox 3.0.12
I have downloaded Flash Player 10
...
and when I try to load the game, all it does is flash...
what am I doing wrong?
Any help would be appreciated. :D

---

### Post by AndThenWhat on 2009-07-23
Maybe try disabling Compiz. If you have an Intel video card then maybe you need to enable UXA. These are just suggestions.

---

### Post by kb010 on 2009-07-23
Okay, I searched exactly how to do that. What I found was this:

 [http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html)

when i type in the command: lspci -nn | grep VGA the output is as follows:

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]

There are no reports about the results of modifying the xorg.conf

regardless, when I open my xorg.conf and try to do what my link told me to do, it tells me I do not have the permissions necessary to save the file. :confused:
what now?

---

### Post by jimrz on 2009-07-23
first, backup your xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bak
```

which can then be used to restore your current situation if things go badly awry

then, using "sudo", make the changes you need

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by kb010 on 2009-07-23
jimrz, I just tried that, and there is no change when I tried to open Farm Town. errr :-k

---

### Post by zeroseven0183 on 2009-07-23
How about other Flash applications in Facebook? Are they running properly?

---

### Post by kb010 on 2009-07-24
I don't use any facebook appications with flash ( I just installed Farm town so I can try to get it right on my own lap top before fixing hers...) but when I open video (say on youtube, etc) they are really broken and jerky.

---

### Post by LookTJ on 2009-07-24
Are you using the open source or proprietory driver for ATI?

Did you try reconfiguring Xorg?(don't remember what the command is for this, sorry)

I have an ATI(Radeon 9000M) here and Farm Town works fine

it's a driver-related or X-related issue, though my best bet is drivers.

Those are the ideas I have so far.

Good luck :)

---

### Post by kb010 on 2009-07-24
the only proprietary drivers I use are for my wireless card and my software modem. So I assume this means I am using an open source driver for ATI.

---

### Post by LookTJ on 2009-07-24
> **kb010 said:**
> the only proprietary drivers I use are for my wireless card and my software modem. So I assume this means I am using an open source driver for ATI.
Another idea(the above posters mentioned this)

Did you try the 64bit flash plugin? I noticed you are running 64bit system.

---

### Post by kb010 on 2009-07-24
Okay, so things went badly awry. I am trying to revert back to the saved version of the xorg.conf and it's not going so well. When I start the compt, it is a really messed up screen. So i restart and put it into recovery mode and try to restore things, and its not going anywhere. will someone give me a step by step on what I am supposed to be doing? This issue is so irratating!

---

### Post by jonick on 2009-07-24
Hi KB010,

I have exactly the same issue in Ubuntu Jaunty (32 bit)using Flash 10, all of the known xorg & driver work arounds have been carried out. And all of the Flash un-install - re-install routines that I know of have been done.

My dirty fix is to run the Windows version of Seamonkey under Wine, which seems to run all of the Facebook apps.

Jonick.

---

### Post by LMelior on 2009-07-31
> **jonick said:**
> Hi KB010,

My dirty fix is to run the Windows version of Seamonkey under Wine, which seems to run all of the Facebook apps.

Jonick.

Thanks a ton!  My wife keeps poisoning my laptop (booting into Vista) just to play Farm Town.  It's not perfect, but it's much, much better than the alternative.

---

### Post by jonick on 2009-08-04
Hi Guys,

I also discovered that reverting to flash player version 9 akes all the facebook apps work in firefox.

First of all you need to un-install flash 10, and purge it from your system.
Can't remember the exact commands but just google un-installing flashplayer, you will get the method from there.

Once you have got rid of flash 10, do the following search on google:

"Flashplayer 9 for unsupported systems" This will show a link to Adobe's site, where you can download Flash nine. Install it and you should be in business.

---

