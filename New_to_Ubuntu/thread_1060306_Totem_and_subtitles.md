---
title: "Totem and subtitles"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by sdim on 2009-02-04
Hi,everyone.
I'm using Totem Xine 2.24.3 and I'd like to ask something about subtitles.
I have the .avi file in the same directory as the .srt files,and Totem loads the subs fine.
As I use Greek subs,I chose Greek ISO 8859-7 from the Preferences menu.
Nevertheless,they don't appear below the movie.Only the English words do.
Is it a matter of Microsoft Fonts (I haven't installed any) or is it another setting I don't know of?
Any idea would be appreciated.
Many thanks.

---

### Post by RomeReactor on 2009-02-04
Hi. Just a shot in the dark here, but I imagine you already have the Greek fonts metapackage installed? If not, [click here]("apt:language-support-fonts-el") to install them.

Not sure if this is what's missing, though.

---

### Post by sdim on 2009-02-05
Many thanks for the answer,RomeReactor,but the link doesn't lead anywhere.
Firefox cannot open it.

---

### Post by RomeReactor on 2009-02-05
> **sdim said:**
> Many thanks for the answer,RomeReactor,but the link doesn't lead anywhere.
Firefox cannot open it.

Odd; it should've opened an installer. Are you using the version from the repositories? And if so, do you have the UbuFox extension installed as well?

In any case, try searching for the package in Synaptic. Or, to install it from the terminal:
```
sudo aptitude install language-support-fonts-el
```

---

### Post by sdim on 2009-02-05
Many thanks but nothing happened.
I guess it can't play Greek subs.

---

### Post by RomeReactor on 2009-02-05
Have you tried with Totem-Gstreamer, Mplayer or VLC?

EDIT: Maybe the [top post here]("http://ubuntuforums.org/showthread.php?t=427202&page=2") can be of help.

---

### Post by duds2008 on 2009-02-06
VLC would probably be the way to go. I never could live with Totem. Mplayers also pretty good.

---

### Post by sdim on 2009-02-06
Thanks for the answers.I know for a fact that SMPlayer plays Greek subs.Nevertheless,I just wanted to know if Totem does that.

---

