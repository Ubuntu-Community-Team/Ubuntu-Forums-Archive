---
title: "How to show Ubuntu on a Projector?"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by ngubk on 2011-05-24
Hi! i'm using a projector to present my slideshow a lot. Each time, i need to restart Ubuntu for it to show on a projector. When i restart my lap, the resolution automatically changes to 1024*768, too.
I've tried some ways include changing laptop's screen resolution, but it doesn't work.
If you know of a way, please help me since i don't want my audience to wait 1 min for me to set up everything.
I'm using 11.04, it's the same in 10.04 and 10.10 too. My HP4410s has Intel onboard Graphic Card.

---

### Post by webofunni on 2011-05-24
What happens when you connect to the projector ? There is no video at all or just resolution problem ?

---

### Post by dwhite on 2011-05-24
when i connect my laptop to a projector it doesn't automatically detect the projector I go to:

System Settings-->Monitors

and then select the projector (i forget without having it right in front of me but maybe i have to click "detect monitors" but in any case it's pretty obvious once you open the Monitor Preferences app.)

---

### Post by ngubk on 2011-05-24
There'no reaction on the projector at all when i connect it. It only show up from the logon screen if i restart my laptop. 
I haven't try pressing 'Detect Monitor' yet. I'll try it when i have chance. Thank you

---

### Post by decoherence on 2011-05-24
> **ngubk said:**
> There'no reaction on the projector at all when i connect it. It only show up from the logon screen if i restart my laptop. 
I haven't try pressing 'Detect Monitor' yet. I'll try it when i have chance. Thank you

Hi!

Some projectors have a sort of 'auto configure' button. Sometimes that's all you need to press. Good luck!

---

### Post by webofunni on 2011-05-25
What interface u r using to connect the projector ?

---

### Post by ngubk on 2011-05-25
What do you mean 'interface'? Sorry i'm a noob when it comes to projectors. I only do the same as what i did in Windows. plug in, wait a bit, and then if it doesn't show up, i get panicked :>

---

### Post by tmette on 2011-05-25
By interface, I believe he means what type of connection are you using?  VGA, DVI, HDMI?

---

### Post by webofunni on 2011-05-25
yes, correct.

---

### Post by JustinR on 2011-05-25
Sometimes computer graphics cards don't come with automatic hardware detection - so they haven't noticed you have plugged in a projector.

On some computers, there's a function key (Not F keys but the FN + a key) called 'CRT/LCD'. Press FN + CRT/LCD and the video card will switch to different ports, vga/hdmi etc. Make sure the projector is plugged in and on.

---

### Post by abottrill on 2011-05-25
On mine I press Fn +F5 i think and it scrolls through the different set-ups eg mirrored or presentation on external. Also set the projector to scan all inputs helps

---

### Post by m_duck on 2011-05-25
Give ***lxrandr*** (graphical front-end to xrandr) a go - it should be in the repos. It's similar to the monitor settings screen of which you spoke earlier, but it seems to work well, and without a reboot required on my netbook.

I don't know if GNOME will take issue to using a second tool to configure the monitors, but I guess it's worth a try?

---

### Post by ngubk on 2011-05-25
> **webofunni said:**
> What interface u r using to connect the projector ?
I read my HP user guide and it said the socket i often use to plug the projector in is VGA.

According to [abottrill]("http://ubuntuforums.org/member.php?u=1285545"), i think i need to press Fn+ F4( has a screen symbol). Thanks!

---

### Post by ngubk on 2011-05-25
> **m_duck said:**
> Give ***lxrandr*** (graphical front-end to xrandr) a go - it should be in the repos. It's similar to the monitor settings screen of which you spoke earlier, but it seems to work well, and without a reboot required on my netbook.

I don't know if GNOME will take issue to using a second tool to configure the monitors, but I guess it's worth a try?
I've installed Lxrandr. Then i just need to change the resolution setting when connecting to a projector, right?

Thanks to all the advices you mentioned above. I'll try each one as soon as possible and return the result.

---

### Post by m_duck on 2011-05-25
> **ngubk said:**
> I've installed Lxrandr. Then i just need to change the resolution setting when connecting to a projector, right?

I don't have a Linux box for checking atm (it's getting annoying, but not long now... sorry, back on topic...) but IIRC when you plug in the projector as well, there will be two lines of settings on LXRandR for your monitor/PJ along with whether you want to activate the outputs or not. So as well as being able to toggle the PJ on/off, you should also be able to run it as 1024x768 (or whatever) and run your main monitor at 1280x800 (or whatever).

There is also the option to run both screens at the lower resolution, duplicating the display.

[LXRandR on LXDE Wiki](http://wiki.lxde.org/en/LXRandr)

---

### Post by Pfoeh on 2011-08-25
Are you using compiz?
My projector is working fine with all netbooks I have.
I've worked with it on 9.04 and 10.04.
I've also tried _U_buntu 11.04 and unfortunately it didn't work properly.
Then I installed _X_ubuntu 11.04 and it worked without a problem.
On the Dutch Ubuntu forum I've read Compiz is causing the problem.
Instead of installing Xubuntu now, you might consider try to work with "Classic mode" in 11.04. or ```
metacity --replace
```I hope this will help you for 11.04.

For 10.04 and 10.10 you can switch of compiz via tab "visual effects".

Source: [http://forum.ubuntu-nl.org/hardware-en-drivers/beamer-aansluiten-lukt-niet/msg735961/](http://forum.ubuntu-nl.org/hardware-en-drivers/beamer-aansluiten-lukt-niet/msg735961/)

Best regards,
Jeroen

---

### Post by UncleOwl on 2011-10-13
Hi,

With lecturing as a big part of my job in academy and being a full-time Linux user since 2000, I moved to Ubuntu at 5.04 and went gradually through all releases on my laptops - up to Natty. Then after a brief period I went back to Lucid (10.04), with issues with projectors as the No 1 reason. 

With Lucid, everything works with my current Dell laptop (with nVidia graphics): I typically have to adjust the resolution from the ordinary 1280x800 to 1024x768 (as this is what most projectors support without distorting the image), then connect the projector's VGA cable, press Fn-F8 (NB! different at other brands of laptops) and here we go. In Natty, the Fn combo didn't work and occasional successes were mixed with lots of failure.

I haven't tried Oneiric with projectors yet, but the still scarce sources suggest that the problem persists. So right now, I suggest downgrading to Lucid, the difference is great.

---

