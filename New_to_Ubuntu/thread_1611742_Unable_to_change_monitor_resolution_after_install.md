---
title: "Unable to change monitor resolution after install"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by Peterfc on 2010-11-02
I have just installed 10.10 as a dual boot. 

The resolution is set at.

resolution  1280 X 1024  ( 5.4 )

Refresh    0 hz

Rotation   Normal

Every thing on screen is so small i need to change the resolution so i can see what i am doing.

Thanks for taking the time to read my post

---

### Post by lombaardcj on 2010-11-08
Ok,  If you haven't yet figured out how to change the resolution (the post is 5days old with no reply).

You go to System -> Preferences -> Monitors

Under the Resolution drop down box select the resolution you want and Hit the Apply button.

This should work for you.

If not, please shout or set this thread to SOLVED please.

---

### Post by Peterfc on 2010-11-08
Thanks for the reply.

There is a post by Skatergirl with this same problem. When i posted i was not aware of the Skatergirl post. 

My problem is that as you say Preferences and then Monitors. At this point nothing in Monitors can be changed. I am using a 32in TV as my monitor and the resolution is 1368 X 768 if i connect a 19in monitor the same happens.

The monitor section does not give me an option to make any changes.

Peter

---

### Post by P4man on 2010-11-08
then you probably installed proprietary drivers for either ati or nvidia, and you should change it in their app (system > prefences > catalyst for ati, system > administration > nvidia x server for nvidia).

---

### Post by lombaardcj on 2010-11-08
I agree to some extent.  When I try to follow my own instructions, the system warns me that I have to use the proprietary vendor software to maintain my monitor settings.  If I ignore this message, I still get the usual Monitor settings window to change my resolution, which has numerous options.

If you do not have any proprietary drivers installed which you know of, you might have to keep on searching for a solution.

P4man,
Is their is any other way to check if proprietary drivers other than going to System -> Administration -> Hardware Drivers?

It might well be that it is the LACK of a proper driver that is causing the unavailability to change screen resolution you know.

---

### Post by wojox on 2010-11-08
Open a terminal and run 

```
lspci | grep VGA
```

---

### Post by P4man on 2010-11-08
> **lombaardcj said:**
> 
P4man,
Is their is any other way to check if proprietary drivers other than going to System -> Administration -> Hardware Drivers?

try

```
jockey-text -l
```

For instance on my machine that gives:

$ jockey-text -l
xorg:fglrx - ATI/AMD proprietary FGLRX graphics driver (Proprietary, Enabled, In use)

---

### Post by godspeedmav on 2010-11-08
You could also give this a try according to this post: _[http://www.myokyawhtun.com/ubuntu-linux/how-to-change-custom-resolution-in-ubuntu-10.html](http://www.myokyawhtun.com/ubuntu-linux/how-to-change-custom-resolution-in-ubuntu-10.html)_

---

### Post by Peterfc on 2010-11-08
Thanks guys for your help and reading of my problem. 

peter@peter-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
peter@peter-desktop:~$ 

When i try jockey-text -l in a terminal the result i get is 

peter@peter-desktop:~$ jockey-text -l
peter@peter-desktop:~$ 

If i go into Additional Drivers the result i get is No proprietary drivers are in use on this system

---

### Post by P4man on 2010-11-08
Thats all correct. For intel graphics you dont need proprietary drivers (and there arent any). 

See godspeedmav's link if you want to add extra modes, xrandr should work.

---

