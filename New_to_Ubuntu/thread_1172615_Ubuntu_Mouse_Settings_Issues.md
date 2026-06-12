---
title: "Ubuntu Mouse Settings Issues"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by Andy06 on 2009-05-28
Does anyone else feel that using the trackpad on laptops with Ubuntu running is a lot less smooth than windows? The cursor speed sort of ebbs and flows and changes its smoothness constantly, sort of like randomly throwing a car in the wrong gear.

External/USB mice work perfectly, problem is just with the trackpads.
Also my trackpad seems to be ultra sensitive on Ubuntu. If my palm so much as comes close to it while typing (say in the URL bar), it throws the focus elsewhere and I end up typing the rest elsewhere. Very annoying. Is this specific to me and (more than a dozen) laptops I'm seeing this on? The laptops are mostly Dells and HPs.

Also in the Ubuntu mouse settings, acceleration clearly controls the speed of the cursor but what does sensitivity control? Seems to make no difference at all. I tested it with min and then max n slightly nudged my mouse, but no difference whatsoever.

Help please:D

---

### Post by fatality_uk on 2009-05-28
I assume you have tried changing the values in **System->preferences->mouse**?

---

### Post by SunnyRabbiera on 2009-05-28
I dunno, the trackpad feels the same in any OS, I never liked them.

---

### Post by LowSky on 2009-05-28
go to trackpad settings, under system on the top panel

My opinion is that trackpads suck, pointer sticks (aka eraser head pointer), like the ones on Lenovo/IBM thinkpads are so much better.

---

### Post by freeman2000 on 2009-05-28
> **SunnyRabbiera said:**
> I dunno, the trackpad feels the same in any OS, I never liked them.

Maybe I'm lucky, but my trackpad works great, especially in Ubuntu.  I can do a 2-finger scroll from anywhere on the trackpad, which can't be done in Windows.  In Windows I must be in the "scroll" area at the extreme right of the trackpad.  

Anyway, go to System --> Preferences --> Mouse to make any changes necessary, as has been stated above.  Good luck.

---

### Post by Andy06 on 2009-05-29
> I assume you have tried changing the values in System->preferences->mouse? 

Yep. Those are the ones I am talking about.

> I dunno, the trackpad feels the same in any OS, I never liked them. 

For me it's a lot smoother in windows, reeks of a driver issue right?

> go to trackpad settings, under system on the top panel

Unfortunately, there really aren't any "settings" there. Just the enable/disable and the tap to click option. No options for controlling smoothness and sensitivity.


> Anyway, go to System --> Preferences --> Mouse to make any changes necessary, as has been stated above. Good luck. 

Yea about that....

In the Ubuntu mouse settings, acceleration clearly controls the speed of the cursor but what does sensitivity control? Seems to make no difference at all. I tested it with min and then max n slightly nudged my mouse, but no difference whatsoever. The help file helpfully states that acceleration is the speed of your mouse pointer and sensitivity is how sensitive it is to movements of your mouse, but it isn't.....

---

### Post by shaoxiao on 2009-05-29
for me, i would like not to use the trackpad!

---

### Post by gabdullah on 2009-06-16
I have the same issue as OP. On my windoze partition, my trackpad runs smooth. In Ubuntu, despite tons of tweaking in system/preferences/mouse, it still sucks. It's ultra-sensitive (to the point that hovering my palms over it seems to engage it... super-annoying when I'm typing). It "ebbs and flows" as OP mentioned (meaning: there tends to be a bit of lag when you move it or slow it down... so, crappy precision). 

It's not enough to make me use vista unless I need it, but it's still really annoying. Better trackpad settings would be ideal. 
I'm using a fully updated Jaunty install, btw, on a Sony Vaio.

Any thoughts??

---

### Post by LowSky on 2009-06-16
buy a travel size mouse???

---

### Post by Andy06 on 2009-06-16
Unfortunately that's not a satisfactory solutions. I have full sized mice to use everywhere I normally use the laptop, but I still often find myself using the trackpad in places where I don't usually use the computer (like on the go, friends place etc).

Once again, what's the difference between the acceleration ans sensitivity settings? The sensitivity setting seems to change absolutely nothing for me. Acceleration changes the speed. What combination (of sensitivity and acceleration) should I enable for it to be smooth and consistent rather than jerky and unpredictable.

---

### Post by gabdullah on 2009-06-16
[IMG]http://i136.photobucket.com/albums/q186/gabbyresch/Screenshot-1.png[/IMG]

I'm working with that, and it's alright. Still a little herky-jerky, and the pad is too sensitive. I haven't started playing around with any of the accessibility settings, but that'll be next.

---

### Post by LowSky on 2009-06-16
try this link I found using google

[http://ubuntuforums.org/showthread.php?t=218307](http://ubuntuforums.org/showthread.php?t=218307)

---

### Post by Andy06 on 2009-06-16
Gabdullah,

Nice theme. shiki?



Lowsky,

Thanks for the link but unfortunately that only enables you to disable the tap click feature. I guess its a really old thread because from 8.04 onwards, ubuntu offers that option in the mouse settings GUI itself. 

Thanks for the effort anyways guys but I guess this remains unsolved

---

### Post by Andy06 on 2009-06-22
What does the sensitivity setting do? Please anyone:-k 

P.S What theme and font is gabdullah using in the picture 2 posts up? :D

---

### Post by Andy06 on 2009-07-16
Ok I think I solved the mystery.

Windows helped hehe. Firstly the mysterious sensitivity slider does not control pointer sensitivity in terms of scale (how much the cursor moves for a given movement of the mouse), it is instead just a counterpart to the "Enhance pointer precision" checkbox of windows. Try it out. 
With the slider all the way to the left, the cursor will jump around your intended target, whereas it gets a lot more predictable and accurate with the slider to the right.

Logically, this should then be turned all the way up to the right as opposed to the acceleration tab which is based on user's own preference.

I reckon the wording should be clearer since windows makes it far more obvious and user friendly.

The other problem is with trackpads going wild on Ubuntu by inadvertently being triggered by the palm while tapping which leads to all sorts of unpredictable chaos. (typing in wrong place because cursor suddenly got re-inserted into wrong location, block of text moves off etc). This is due to the driver of the touchpad not being correctly used by Ubuntu (even windows can't without the help of the custom software which OEMs configure and ship). For example, my snaptics touchpad had all these hidden settings in the synaptic tap of mouse settings in windows and they revealed why it was better at everything in windows.

The custom software allows for enhancements and options like palmcheck protect, sensitivity, macros, touch zones, scrolling in any direction, sticky borders, edge motion, constrained motion within windows, tap zones etc. 
Since Ubuntu does not come WITH the notebook, hence it misses out. So just need to get this same software for your touchpad in Ubuntu (try Wine).

I doubt this will be fixed soon since open source development is so developer-driven ;) and no developer/techie/power user tends to go within 10 foot of a touchpad. They are universally despised :)

---

### Post by Andy06 on 2009-07-16
Found this on the Synaptics site.

[http://www.synaptics.com/sites/default/files/driverpb.pdf](http://www.synaptics.com/sites/default/files/driverpb.pdf)

Those are the sort of features available with the software/driver on windows that cause the performance difference.

I guess that is both good news and bad news. Good news because it wasn't something inherent in Ubuntu or the Linux Kernel which handled trackpads in a less than optimal way and bad news because this software/driver combo is pretty much windows only.

What puzzles me though is that Windows 7 also plays nice with most trackpads I have tried despite being clean installs and not having the benefit of this driver/software config.

---

### Post by Andy06 on 2009-07-19
Ok I think I sort of found the counterpart on Linux but I need help running it.

Firstly, going into Synaptic (the package manager, not touchpad) and typing touchpad brings up 3 packages amongst others that are relevant to synaptic (the touchpad).

First is xserver-xorg-input-synaptics which is the driver file. Is there a way to get a newer version?

Second is tpconfig which is to configure touchpads, but how do I run it? After I install it, where does it go? 

Third is gsynaptics which is a GUI config tool for the synaptic touchpad, probably what we need and the one that performs the same functions as the OEM software on windows. But this gives the following error on trying to run: 
> "GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

So where do I find xorg.conf and how do I edit it? Or is there another way to do this?

Thanks a lot

---

### Post by Andy06 on 2009-07-25
*bump*

---

### Post by jtc611 on 2009-07-28
I can answer the last 2 of your questions:
"Second is tpconfig which is to configure touchpads, but how do I run it? After I install it, where does it go?"  Right click on the package after it is installed and select properties to see where it went.

xorg.conf is located in /etc/X11/

Don't edit this file unless
1.  You make a backupfile  sudo cp xorg.conf xorg.conf-original
You don't have to call it xorg.conf-original.  You could call it these_are_the.daves_i_know if you wanted to

2. You know how to reboot to a terminal window (safe mode) and recover the original xorg.conf file if you screw something up.

---

