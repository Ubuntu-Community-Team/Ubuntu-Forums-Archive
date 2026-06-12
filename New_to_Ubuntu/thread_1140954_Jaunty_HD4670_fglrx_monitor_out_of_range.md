---
title: "Jaunty HD4670 fglrx monitor out of range"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by isotonix on 2009-04-28
Hello Everyone

I have installed Ubuntu 9.04 (Jaunty Jackalope) using wubi. I can boot into ubuntu and everything is fine. 

However when I install the restricted driver *fglrx* when prompted by ubuntu itself, things change (my graphics card is a Radeon HD4670).

After the required reboot my monitor simply reports "out of range" but at the same time I can hear the log-in screen drum-roll. Even if I log in blind I can reach the desktop (judging by the music) but I cannot see it.

My monitor is a Digimate L-1715, it can do 1280x1024@75Hz. I have tried editing xorg.conf by adding the appropriate HorizSync and VertRefresh values in the appropriate section, but to no avail.

I have quickly learnt the value of: *sudo apt-get remove xorg-driver-fglrx* :)

Does anyone have any ideas on how to successfully implement this driver?

---

### Post by JamesBowen on 2009-05-08
I was reading in another thread about a similar experience back hardy or intrepid.

Use Alt + Ctrl + F1 to switch to console, then Alt + Ctrl + F7 to switch back to X and, with any luck, it should work.

After that, go to ATI's site and download and install their latest catalyst drivers.  Once you have those all set up, I'm pretty sure you won't have to do the toggle in/out of X when starting up anymore.  I can post more info later; I will actually be testing this shortly (On Fridays we play steam games via wine after work...I'm going to bring my 4670 in and get it all set up, for the higher reziness and all)

---

### Post by isotonix on 2009-05-10
Thanks for the suggestion. Unfortunately switching back (Ctrl+Alt+F7) gives the same "out of range" message.

This problem occurs when I install catalyst 9.4. I am told that Jaunty will not support earlier catalyst drivers so I shall wait for catalyst 9.5 and keep my fingers crossed.


Judging by the lack of posts on the subject, this problem could be unusual - perhaps due to an unlucky driver/hardware combination, so with a bit of luck you will be unaffected.

---

### Post by isotonix on 2009-05-19
I installed Catalyst 9.5 and got exactly the same problem as before.

On a brighter note Intrepid appears to work brilliantly - (apart from some odd flicker when I watch a video). I presume it is running Catalyst 9.4 (I installed it via 'Restrict Hardware Drivers') - I haven't tried Catalyst 9.5 yet.

I think I shall stick to Intrepid and mothball jaunty for a few months or wait for Ubuntu 9.10

---

