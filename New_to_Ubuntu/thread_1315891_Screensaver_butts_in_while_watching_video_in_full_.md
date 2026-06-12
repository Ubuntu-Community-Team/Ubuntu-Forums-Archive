---
title: "Screensaver butts in while watching video in full screen"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by infestor on 2009-11-05
what bothers me in karmic is that the screensaver butts in while i watch movies (vlc or smplayer) in full screen. is there a way to fix this?

---

### Post by travmanx on 2009-11-05
> **infestor said:**
> what bothers me in karmic is that the screensaver butts in while i watch movies (vlc or smplayer) in full screen. is there a way to fix this?
Preferences -> Select 'All' under settings rather than simple... -> Choose Video tab -> Check disable screensaver

---

### Post by infestor on 2009-11-05
> **travmanx said:**
> Preferences -> Select 'All' under settings rather than simple... -> Choose Video tab -> Check disable screensaver

for smplayer already checked...doesnt work...for vlc couldnt find such option

---

### Post by philinux on 2009-11-05
I've been down this road. Dead end.

Just disable the screensaver.

---

### Post by travmanx on 2009-11-05
> **infestor said:**
> for smplayer already checked...doesnt work...for vlc couldnt find such option

Uploaded attachment of a screenshot for you.

I honestly just disable screensaver, as I have no real point for it.

---

### Post by rvm4000 on 2009-11-05
For smplayer, first install the mplayer package from this PPA:
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

Then add this line to your $HOME/.mplayer/config:
heartbeat-cmd="gnome-screensaver-command -p &>/dev/null"

---

### Post by falconindy on 2009-11-05
> **philinux said:**
> I've been down this road. Dead end.

Just disable the screensaver.
The issue is that the function that VLC happily used in gnome-screensaver-2.20 now only exists as a "to do" in the source code of 2.28. There's a [patch]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/428884") floating around Launchpad, along with a lengthy discussion as to whether the fault lies with gnome-screensaver-2.28 or vlc (for using an "outdated" poke function). I don't run Ubuntu anymore, but I *am* running gnome-screensaver-2.28 with this patch and it works as expected.

I don't think it would be **too** difficult to `apt-get source gnome-screensaver`, apply the patch and rebuild the .deb package.

---

### Post by laceration on 2009-11-05
I disabled gnome-screensaver a long time ago and I have much derision for it.  Is there a good reason why gnome-screensaver puts a burden on video programs?  The coding + config has to be done in the video player so that the screensaver is not activated!  Is this not bassakwards? Is it the center of the world that we need to build our systems around? Why can't gnome-screensaver look for a video process and then not activate? What narcism.

---

### Post by falconindy on 2009-11-05
> **laceration said:**
> I disabled gnome-screensaver a long time ago and I have much derision for it.  Is there a good reason why gnome-screensaver puts a burden on video programs?  The coding + config has to be done in the video player so that the screensaver is not activated!  Is this not bassakwards? Is it the center of the world that we need to build our systems around? Why can't gnome-screensaver look for a video process and then not activate? What narcism.
I doubt you'll get along with **any** screensavers then. Putting the onus on the screensaver to probe for any number of possible processes would take up far more CPU time than it would for the interrupt-style wakeup calls that have been going on since before the creation of the x86 architecture.

---

### Post by jomex on 2009-11-08
i have the same issue while watching Flash videos with Firefox in fullscreen

---

### Post by kenox on 2010-01-08
I am having the same problem with the screensaver

I submitted a feature request here please vote-
[http://brainstorm.ubuntu.com/idea/23268](http://brainstorm.ubuntu.com/idea/23268)

---

### Post by costre on 2010-01-21
I have a related problem.

The thing is, I want my screensaver to kick in when video isn't playing. But mplayer seem to diable the screensaver while it's running, regardless if a video is playing or not.

Is it a settings issue, or do I have to manipulate something outside mplayer?

---

