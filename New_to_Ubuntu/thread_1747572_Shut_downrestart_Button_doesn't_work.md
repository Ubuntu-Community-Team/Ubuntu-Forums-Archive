---
title: "Shut down/restart Button doesn't work"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by donnagarnet on 2011-05-02
Since I've upgraded to 11.04, I can't shut down my computer using the shut down/restart button.

I know just flipping the switch on the surge protector all components are plugged into isn't good for the computer, but I can't shut it off any other way.

Poking at the shut down button does absolutely nothing.

What am I doing wrong/what have I screwed up?

Thanks, kids.

---

### Post by KL_72_TR on 2011-05-02
Open the Command line and type:
```
sudo reboot
```
for rebooting or
```
sudo halt
```
to shut down the PC
Remember you will be prompted to give your password

---

### Post by laidback on 2011-05-02
Check that you have Quickstarter disabled in Open Office or Open Libre. To find out open Writer, choose Tools>Options>Memory, uncheck the "Enable Systray Quickstarter" option. 

I found this worked for me in 10.x and just the other day in 11.04. I'm not sure whether you need to repeat the operation if you use various desktop views, i.e. Classic, Safe etc.

Hope this helps.

Laidback

---

### Post by beew on 2011-05-02
> **laidback said:**
> Check that you have Quickstarter disabled in Open Office or Open Libre. To find out open Writer, choose Tools>Options>Memory, uncheck the "Enable Systray Quickstarter" option. 

I found this worked for me in 10.x and just the other day in 11.04. I'm not sure whether you need to repeat the operation if you use various desktop views, i.e. Classic, Safe etc.

Hope this helps.

Laidback

That was my guess too! In Ubuntu 10.xx it is ok because the quick starter has a tray icon so I can shut down and reboot by right clicking and quit the quick starter but Unity has no tray icon so it means you can't use the quick starter or have to manually disable it before shut down or reboot by opening a LO document and disable it from options > memory.

---

### Post by laidback on 2011-05-03
beew,

I agree, so why isn't there a system tray in Unity I wonder? So you have to disable quickstarter permanently really otherwise it's just a pain in the **** to keep doing it manually. I guess it's a small issue really but certainly one that had me going when I first came across it.

I don't think it affects all pc's, but I'm sure that new users will be very upset if they can't shutdown and may well move on!

---

### Post by beew on 2011-05-03
But comparing to LO opening in full screen with no max/min/move/restore buttons this is only a small thing. :)

(The work around for the no button problem is to switch to another desktop and then switch back then the buttons would show up) New users would be very upset if they actually try to use Unity rather than just looking at it, at this stage I think it is beta software at best.

---

