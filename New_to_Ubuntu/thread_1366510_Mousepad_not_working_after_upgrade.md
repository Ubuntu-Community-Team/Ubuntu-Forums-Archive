---
title: "Mousepad not working after upgrade"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by ahajou on 2009-12-28
I installed Ubuntu 9.10 through the upgrade manager and the mouse pad is not working, Please help
I'm using an HP pavilion zt3000 please consider the case that i have to use only the keboard. Regards.

---

### Post by jfbooth on 2009-12-28
just had to reply to this one.  Mouse .. the thing you move around in order to select things on your screen.  MousPAD .. the 'rubber' mat your mouse moves around ON (not usually needed if you have a hard, smooth surface table top).

---

### Post by jfbooth on 2009-12-28
If you are using a notebook computer, you are probably using the TOUCHPAD which is an alternative to a desktop mouse.

---

### Post by 5BallJuggler on 2009-12-28
jfbooth - It doesn't matter what he is using, it's broken, he has come here to ask for help not to be ridiculed.

ahajou - I had the same issue when I upgraded to karmic, do you know what linux kernel you are using, the latest one should fix it.

if you open "system monitor" it will tell you. post back with the info.

to open system monitor with out the mouse -

Press Alt + F2
type gnome-system-monitor
use left and right arrow keys to navigate between tabs.

Phil

---

### Post by jfbooth on 2009-12-28
I wasn't ridiculing anyone.  A search on 'touchpad does not work' gets more hits than 'mousepad does not work'.

Aside from that, here is a link to others who have had the same problem:

[http://ubuntuforums.org/showthread.php?t=1306864&highlight=touchpad](http://ubuntuforums.org/showthread.php?t=1306864&highlight=touchpad)

and a quote from the original post (which sounds like your problem):

"I seem to be missing a tab under System -> Preferences -> Mouse. 

My mouse preferences window shows only two tabs: General and Accessibility. 

However, there should be one more tab called "Touchpad" that seems to be missing. 

It was there before I upgraded to 9.10 (I was running 9.04)"

and it appears it happens as the result of upgrading.  I am sure 5Ball or someone can help you .. but if not, it is advised in that thread to do a full reinstall.  Keyword here being TOUCHPAD.

---

### Post by ahajou on 2009-12-28
Im sorry for the misconception, please keep im mind that im not an native english speaking person.

Regarding the "Touchpad" error, 
Im using:

Release 9.10 (Karmic)
Kernel Linux 2.6.28-17-generic
GNOME 2.28.1

Processor: Intel(R) Pentium(R) M Processor 1.60GHz

Thanks for the concern

---

### Post by jfbooth on 2009-12-28
I am obviously no Linux expert.  The link to that thread will indicate advice to reinstall .. as if there is no easy way to correct the problem.

THIS thread indicates a couple of possible solutions though .. I recommend you read it carefully:

[http://ubuntuforums.org/showthread.php?t=1298644](http://ubuntuforums.org/showthread.php?t=1298644)

The problem seems to happen to people UPGRADING from 9.04 to 9.10 as you did.  I am sure you will find the solution in the link above.

---

### Post by jfbooth on 2009-12-28
then, there is this:

[http://www.polochen.com/wordpress/2009/09/clicking-on-touchpad-not-working-ubuntu-9-04-9-10/](http://www.polochen.com/wordpress/2009/09/clicking-on-touchpad-not-working-ubuntu-9-04-9-10/)

---

### Post by 5BallJuggler on 2009-12-29
> **ahajou said:**
> Im sorry for the misconception, please keep im mind that im not an native english speaking person.

Regarding the "Touchpad" error, 
Im using:

Release 9.10 (Karmic)
Kernel Linux 2.6.28-17-generic
GNOME 2.28.1

Processor: Intel(R) Pentium(R) M Processor 1.60GHz

Thanks for the concern

OK, this is how I fixed it on my system

[http://ubuntuforums.org/showthread.php?t=1306012](http://ubuntuforums.org/showthread.php?t=1306012)

Hope this helps

Phil

---

