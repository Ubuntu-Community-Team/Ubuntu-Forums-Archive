---
title: "Play MP3 and VOB"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by Somecuitears on 2010-07-19
i m new to ubuntu n i dont know anything about ubuntu.
i m using ubuntu 9.10.. i want to instal mp3 plugin.. how do do tht??? i cannot play my mp3 files...

---

### Post by Jazzy_Jeff on 2010-07-19
Go to the Ubuntu Software Center and search for Ubuntu restricted extras.

---

### Post by Somecuitears on 2010-07-19
but how do i play mp3 files from Rthymbox??? and also video files from Movie Player.. every time i try to play either of them "Search for suitable plugin" dialog box is displayed. if i click search it shows no pugins.. do we have to download plugin from web site( if yes which one is it) or can we install from the Ubuntu cd???
i tried downloading few plugins from google .deb files n every time i try to run it an error is displayed saying wrong architecture... help :(

---

### Post by Jazzy_Jeff on 2010-07-19
> **Somecuitears said:**
> but how do i play mp3 files from Rthymbox??? and also video files from Movie Player.. every time i try to play either of them "Search for suitable plugin" dialog box is displayed. if i click search it shows no pugins.. do we have to download plugin from web site( if yes which one is it) or can we install from the Ubuntu cd???
i tried downloading few plugins from google .deb files n every time i try to run it an error is displayed saying wrong architecture... help :(

If you install the Ubuntu restricted extras that will give you all the plugins. For video I would install VLC. Both are in the Ubuntu Software Center.

---

### Post by Somecuitears on 2010-07-19
my ubuntu software center doesnot allow me to install restricted extras... i hav attached picture of wht it is like in my copy of ubuntu... can u tell me why it is saying so???

---

### Post by BigMeanMikeRich on 2010-07-19
Well there's your problem ;)

The name of the package is hyphenated, so it should show up if you search
for ubuntu-restricted-extras

If it refuses to come up in Software Center or Synaptic Package Manager,
you can try opening a terminal (Applications > Accessories > Terminal)
and typing the following:
```
sudo apt-get install ubuntu-restricted-extras
```
This will give you support for mp3s, DVD playback, the Flash plugin for your
browser, some Microsoft fonts, and a whole bunch of codecs for video and
audio playback. It is definitely a must-have package for a standard desktop
user.

---

### Post by BigMeanMikeRich on 2010-07-20
If the method above did not work, Ubuntu may not be recognizing the need to
enable the Multiverse repository (where ubuntu-restricted-extras is stored).

You can verify that the Multiverse repository is enabled (and if not, enable
it) by going to System > Administration > Software Sources.  On the primary
tab, 'Ubuntu Software,' look down the list for 'Software restricted by
copyright or legal issues (multiverse).' Make sure there is a check in the
box next to this item, then click the Close button on the bottom right. 

You may be asked to update package information at this time; do so. This 
will update the list of installable software to include results from the
Multiverse repository.  After your system as finished refreshing package
info, ubuntu-restricted-extras should appear in both the Software Center and
Synaptic Package Manager, so my previous advice should now work.

---

### Post by Somecuitears on 2010-07-20
> **BigMeanMikeRich said:**
> Well there's your problem ;)

The name of the package is hyphenated, so it should show up if you search
for ubuntu-restricted-extras

If it refuses to come up in Software Center or Synaptic Package Manager,
you can try opening a terminal (Applications > Accessories > Terminal)
and typing the following:
```
sudo apt-get install ubuntu-restricted-extras
```
This will give you support for mp3s, DVD playback, the Flash plugin for your
browser, some Microsoft fonts, and a whole bunch of codecs for video and
audio playback. It is definitely a must-have package for a standard desktop
user.

i m now able to see install button but now when i click install it doesnot download and shows waiting for other software manager to quit. wht is this now...

---

### Post by BigMeanMikeRich on 2010-07-20
The fact that you can now see restricted extras as installable is a 
good sign. You're almost there! :D Now to answer your question.

As a safety feature, Ubuntu only lets you use one package management
tool at a time. For example, if you have Synaptic open, you cannot
use Software Center to install anything, or vice-versa. This is to
prevent you from accidentally installing multiple copies of a 
package, or conflicting versions, etc.  Use either one you'd like,
but one at a time.

I would close all windows and open up Software Center, then install
from there.  If it still acts funny or in unexpected ways, you could
try restarting, then *without opening anything else* open up a
terminal (Applications > Accessories > Terminal) and type (or paste)
in the following code:
```
sudo apt-get install ubuntu-restricted-extras
```

---

