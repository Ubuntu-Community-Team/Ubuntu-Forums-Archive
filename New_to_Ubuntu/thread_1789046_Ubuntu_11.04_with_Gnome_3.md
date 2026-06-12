---
title: "Ubuntu 11.04 with Gnome 3"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by rebel01.nilesh on 2011-06-23
Hi,

i recently upgraded to natty (after a lot of apprehension) and surprisingly i find that though a bit tough to adjust to UNITY works like a charm. I havent had much problems with the UNITY inteface except that i miss my PANFLUTE APPLET on panel but rest of the applets i could still install and use.

Now the Big question. Can i install GNOME 3 over 11.04 without breaking UNITY? 

i have already tried this some times and although i installed and worked with gnome 3 i couldnt use untiy as smoothly as before. Many options such as APPEARANCE, Theme Changing, Backgrounds etc stopped working.

So help me guys please.

---

### Post by nothingspecial on 2011-06-23
> **rebel01.nilesh said:**
> Hi,

Now the Big question. Can i install GNOME 3 over 11.04 without breaking UNITY? 



The Big answer is not last time I checked. Unless you install the alpha version of the next version. But that'll probably break everything. :D

---

### Post by rebel01.nilesh on 2011-06-23
damn !! i thought by now they would have found a solution to this co-existence thing.

---

### Post by akand074 on 2011-06-23
Nope, no solution. There won't be for 11.04. I mean, it makes sense. Unity in 11.04 is running over gnome 2. Installing gnome 3 would overwrite gnome 2. i.e you can't have gnome 2 installed as well as gnome 3 it'll just upgrade everything. Same with anything else, you can't use VLC 1.1.5 and 1.1.10 at the same time. The OS won't allow it. The next version, 11.10, Unity is running over gnome 3, so installing gnome-shell is just a matter of sudo apt-get and done.

---

### Post by cbowman57 on 2011-06-23
Don't know what the official answer is but Unity & Gnome 3.0 shell coexist just fine, for now anyway, on my installation.

---

### Post by Elitenoname on 2011-06-23
Yes you can, you will either use gnome 3 or unity they do not work together you can google it and it is very simple to do.

```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell
sudo apt-get install gnome-session

sudo apt-get remove gnome-accessibility-themes
sudo apt-get install gnome-themes-standard

reboot

sudo apt-get purge unity
sudo apt-get purge scrollbar*
sudo apt-get install gnome-tweak-tool
apply adwaita themes

logout or reboot

```

I got that from gotbletu who posted a video on youtube how to do it. I have done this my self and it does work

---

### Post by wolfen69 on 2011-06-23
It *can* be done, but don't be surprised if an update breaks it. For this reason, I decided to go with Fedora that has Gnome 3 by default.

---

### Post by cbowman57 on 2011-06-23
> **wolfen69 said:**
> It *can* be done, but don't be surprised if an update breaks it. For this reason, I decided to go with Fedora that has Gnome 3 by default.

That may have been the case some time ago but it's not that fragile now, at least not on 11.04.  They have a lot of work left on 11.10, that I wouldn't recommend for anyone that wants to try gnome 3 shell.

---

### Post by bmbaker on 2011-06-28
just a little reminder that there is a difference between gnome3 and gnome-shell!
in 11.04 unity uses gnome2 and happily works with gnome-shell installed via ppa.

---

### Post by Crempel on 2011-06-29
Well, a few weeks ago I added the "gnome3-team" repository to my list of repos and forgot about it.

Today I ran an upgrade in synaptic and it installed almost all of Gnome 3. So I also installed the gnome-shell (it all came from the above repo); and the setup works! In GDM I can choose between Ubuntu (Unity) or Gnome (Gnome-Shell). Ok, the Gnome-Shell is not bullet-proof whereas Unity appears to behave like before - based on Gnome 3!

I'm still somewhat confused as to how this all came together: Has anybody out there experienced something similar?

---

### Post by LowSky on 2011-06-29
Tried this a few days ago. Gnome-shell wouldn't work but Unity worked pretty well. I was pretty annoyed.

---

### Post by cbowman57 on 2011-06-29
> **Crempel said:**
> Well, a few weeks ago I added the "gnome3-team" repository to my list of repos and forgot about it.

Today I ran an upgrade in synaptic and it installed almost all of Gnome 3. So I also installed the gnome-shell (it all came from the above repo); and the setup works! In GDM I can choose between Ubuntu (Unity) or Gnome (Gnome-Shell). Ok, the Gnome-Shell is not bullet-proof whereas Unity appears to behave like before - based on Gnome 3!

I'm still somewhat confused as to how this all came together: Has anybody out there experienced something similar?

Similar how?  I've been installing systems with Unity & Gnome shell coexisting for about 8-10 weeks.  If you want both Unity and a fully featured gnome shell you might want to look here [http://ubuntuforums.org/showthread.php?t=1754198](http://ubuntuforums.org/showthread.php?t=1754198)

---

