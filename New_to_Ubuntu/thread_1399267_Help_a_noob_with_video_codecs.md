---
title: "Help a noob with video codecs"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by mairuzu on 2010-02-05
Hi I'm a total Ubuntu noob.

I have Ubuntu9.10 and have installed MPlayer, VLC Player and Miro, but as soon as I open any AVI file they just close and disappear without a word!

I have had a look to see how to install codecs, but to no avail.

Please could someone give me a complete dummy's step by step guide to resolving this problem?

FYI - I'm using a laptop on which I had no problem playing everything through VLC on XP, but have ended up using exclusively Ubuntu after the first attempt at installing a dual boot completely fried my version of XP and now I can't go back! Which I'm kind of happy about if I can get things working in Ubuntu.

---

### Post by Glenn nl on 2010-02-05
Did you try installing the ubuntu-restricted-extras package?

---

### Post by mairuzu on 2010-02-05
I did - but to be honest, I don't really understand what it is or does...

---

### Post by mairuzu on 2010-02-05
Just had a look and I'm assuming that it's something I wouldn't necessarily see or be aware of once it's installed? Am I right?

---

### Post by Cabs21 on 2010-02-05
did you install cairo dock?  I have had an issue with VLC and cairo dock before.  try opening VLC alone without a video, go to preferences in the options, tools, or edit tab.  on the left in the preferences window there should be a video tab.  Under that tab find the output bar and change it to GNOME or GLopen or something like that. Close VLC and try opening a video file again.  If no luck try a different format.  If still no luck then I cant help you.  This issue happened to me while cairo dock was installed.  When I reinstalled a fresh 9.10 and VLC the issue did not happen and has not happened yet.  I have not installed cairo dock yet.  Good luck.  Let us know if it worked or not.

---

### Post by lisati on 2010-02-05
Maybe FF&H isn't the best place for this discussion.....

---

### Post by Elfy on 2010-02-05
moved to ABT

---

### Post by nhasian on 2010-02-05
VLC doesnt need codecs installed.  it plays all the video formats natively.  If VLC fails to play your video file there is probably something wrong with your video file.

open up a terminal from Applications->Accessories and try to play the video file with vlc from there.  then if it crashes you can see what the output message is.

> **mairuzu said:**
> I have Ubuntu9.10 and have installed MPlayer, VLC Player and Miro, but as soon as I open any AVI file they just close and disappear without a word!

---

### Post by andrew.46 on 2010-02-05
Hi mairuzu,

> **mairuzu said:**
> I have Ubuntu9.10 and have installed MPlayer, VLC Player and Miro, but as soon as I open any AVI file they just close and disappear without a word!

This is often a sign that your media players are asking for a default video mode that is not suitable for your system. To test this try altering the 'video out' setting in vlc to something like x11. This setting can be found in vlc by following:

Tools --> Preferences --> Video --> Output

and altering the settings in the dropdown box.

All the best,

Andrew

---

### Post by mairuzu on 2010-02-05
Fantastic! thank you - seems to work a treat!

---

### Post by andrew.46 on 2010-02-05
Hi mairuzu,

> **mairuzu said:**
> Fantastic! thank you - seems to work a treat!

Excellent news :). If you are also a keen MPlayer user the same trick will work there but I would advise you to think about using the gui SMPlayer rather than the default gui (gmplayer) that normally comes with MPlayer. This can be loaded from the developer's PPA as follows, in a *single* command:

```

sudo add-apt-repository ppa:rvm/smplayer && \
sudo apt-get update && \
sudo apt-get install smplayer

```

and then the video out can be altered in a similar fashion:

Options --> Preferences --> General --> Video --> Output Driver

All the best,

Andrew

---

