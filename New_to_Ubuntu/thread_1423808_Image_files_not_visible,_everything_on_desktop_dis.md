---
title: "Image files not visible, everything on desktop disappearing,."
date: 2010-03-07
forum: New to Ubuntu
---

### Post by pj_kare on 2010-03-07
Until now (over 2 months) Karmic has been running fine on my machine, I have a terribly slow and time-limited dial-up Internet connection which I share with my GF (she goes online for a while then I go on etc.) so don't really allow updates, apart from installing GnomePPP and its dependencies and Firefox updates, it's basically a clean install.

Now when I open "Pictures" folder I can't see the image files and the animated "busy" cursor sits there spinning indefinitely. It's not until I open a sub-folder (in which files are visible) and then navigating back that the image files become visible.

Also, I have had a couple of times when everything on the desktop disappears, Launchers, drive icons, and even wallpaper.

I am currently allowing GDM and Nautilus to update, but It's killing my attempt to post this message. (I mean I can barely use Firefox or do anything else online when updates are running). Hopefully the updates may fix my problem, otherwise I may have to resort to a format and re-install, which is no real biggie ( I have become quite proficient at it). I may even go back to Jaunty for now.

Otherwise, any immediate help would be greatly appreciated :).

---

### Post by ajgreeny on 2010-03-07
It could be a graphics card problem.  What hardware do you have?

I suspect that it may be an ATI card, which can have similar problems with display artifacts like this, depending on your settings.  A manual edit of xorg.conf may help, but let's know more about the problem.

---

### Post by pj_kare on 2010-03-07
> **ajgreeny said:**
> It could be a graphics card problem.  What hardware do you have?

I suspect that it may be an ATI card, which can have similar problems with display artifacts like this, depending on your settings.  A manual edit of xorg.conf may help, but let's know more about the problem.

Thanks for the reply **ajgreeny** hopefully it's not the graphics card or any other hardware problem, though anythings possible. Although in this instance graphics still fine on the darkside. (In Xp).

System is a non-brand build machine, 2.8 gig P4, 2gig ram, foxconn mobo, upgraded to a BenQ HD lcd monitor a while back and had to upgrade graphics card to Nvidia Geforce 6200, 512mb card, as previous card wouldn't support lcd's resolution, or HDMI.

---

### Post by NightwishFan on 2010-03-07
This happens to me on Karmic. At times a single folder will not open, but killing and restarting nautilus or logging out will work. Also, please ensure you have permissions on the directory. I assume you do but it never hurts to check.

---

### Post by pj_kare on 2010-03-08
> **NightwishFan said:**
> This happens to me on Karmic. At times a single folder will not open, but killing and restarting nautilus or logging out will work. Also, please ensure you have permissions on the directory. I assume you do but it never hurts to check.

Thankyou NightwishFan, I think permissions are all ok. Or at least I haven't tried to change any from their default.

After updating GDM and Nautilus, Pictures seem to be showing up ok for now, as for the desktop disappearing I just have to wait and see if it happens again.

---

### Post by Rasa1111 on 2010-03-08
wow, props to you for getting dial up going!! :lol:

i literally tried for a week straight. lol

i have also been on dial up for some time, 
but when i realized it would take more skills than what ive got to get it going, 
i ordered DSL.. just so i could use Ubuntu . lol

 sounds like your updates may have worked... 
here's hoping , anyway... 

cheers. :)

---

### Post by pj_kare on 2010-03-08
> **Rasa1111 said:**
> wow, props to you for getting dial up going!! :lol:

i literally tried for a week straight. lol

i have also been on dial up for some time, 
but when i realized it would take more skills than what ive got to get it going, 
i ordered DSL.. just so i could use Ubuntu . lol

 sounds like your updates may have worked... 
here's hoping , anyway... 

cheers. :)

Setting up dialup was a breeze (easy) on an external netcomm/banksia modem, at least after trying to get the internal motorola (winmodem) to work.(And after help from this forum). It was a case of have to.. as we live on a farm 13km from town and the phone lines are old and not capable of carrying broadband. There is only 1 (expensive) carrier that supplies wireless to our area, so dialup it is. Setting up modem can be done in a few minutes now I know what I'm doing.

On the original subject: System is still holding up OK after being on/used most of the day.

---

