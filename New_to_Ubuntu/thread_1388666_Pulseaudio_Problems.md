---
title: "Pulseaudio Problems"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by Bearly Able on 2010-01-23
Hi,

When I upgraded to Karmic, I had sound problems.  I found a [thread]("http://ubuntuforums.org/showthread.php?t=1327449") on the Forums suggesting I remove pulseaudio, which I did and it solved the problem.

Earlier today, I installed a couple of updates through the update manager (I believe they were both to do with Python) and when I tried to boot up just now, Ubuntu wouldn't load.  I tried recovery mode and chose "repair broken packages", which also installed some Python packages (sorry this is very vague), after which I was able to reboot normally.  However, it has also re-installed pulseaudio and all my sound problems have returned.  When I tried to remove pulseaudio with synaptic, listed among the packages which will also be removed is ubuntu-desktop.

While I freely admit to knowing nothing on the subject, I have a nasty feeling removing that package will only add to my woes, so now I'm stuck with pulseaudio and non-functioning sound.

Please can anybody help here?  Thanks in advance.

Lesley

---

### Post by ratcheer on 2010-01-23
It is known that removing PA also removes ubuntu-desktop. However, most people seem to say it is not really a problem. I don't really understand it, either. Personally, I decided to stick with PA and solve the problems. It wasn't easy, but once it is fixed, it is very usable.

Tim

---

### Post by Bearly Able on 2010-01-24
Thanks.  I had tried to find a fix before I posted, but got bogged down hunting for solutions.  I've finally got pulseaudio working, thanks to [this guide]("http://ubuntuforums.org/showthread.php?p=4928900") and the additional advice in [this thread]("http://ubuntuforums.org/showthread.php?p=7436370&mode=linear#post7436370").

---

### Post by Mariane on 2010-01-24
How can you tell whether you have pulse audio working or not? 

Mariane

---

### Post by Enigmapond on 2010-01-24
> **Mariane said:**
> How can you tell whether you have pulse audio working or not? 

Mariane

If you're having major sound issues, Pulse is active. If everything is working great then Pulse has stopped working...:biggrin:

---

### Post by Mariane on 2010-01-24
In this case I definitely have it :-({|= 
How can I get rid of it, please? 

Mariane

---

### Post by Bearly Able on 2010-01-25
Hi Mariane,

The guide I used to fix pulseaudio (see my earlier post) says it's not included in the Kubuntu distribution, so I'd guess something else is causing your problems.  I'm not a Kubuntu user, so I can't help you any further; hopefully someone else can.

Lesley

---

### Post by Mariane on 2010-01-25
Now I know:

To stop it until next reboot:
killall pulseaudio

To permanently remove it:
sudo apt-get purge pulseaudio

WARNING: This last is only good with KDE, in gnome it removes gnome-desktop. 

Mariane

---

