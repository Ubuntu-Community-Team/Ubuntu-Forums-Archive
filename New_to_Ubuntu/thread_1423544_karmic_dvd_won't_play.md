---
title: "karmic dvd won't play"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by DarinB on 2010-03-06
fresh install of karmic on an old p4 1.2gb ram
i installed the restricted codex from on line
please help i would love to go home from this install???


File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///media/L_APPARTEMENT/VIDEO_TS/'. Check the log for details.
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///media/L_APPARTEMENT/VIDEO_TS/'. Check the log for details.
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///media/L_APPARTEMENT/VIDEO_TS/'. Check the log for details.
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///media/L_APPARTEMENT/VIDEO_TS/'. Check the log for details.

---

### Post by XubuRoxMySox on 2010-03-06
With an active internet connection, open **Synaptic Package manager** and look for a package called "*ubuntu restricted extras*," and one called "*libdvdread*" and "*libdvdcss*"

If the little box next to them is unchecked, click in the box to **Mark for Installation**, then click **Apply** and give it a few secs to download and install.

That should do it for you.

-Robin

---

### Post by ajgreeny on 2010-03-06
You'll need to enable medibuntu repos to get libdvdcss2.
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by msendejas on 2010-03-06
I am having a similar problem What model and DVD drive do you have installed?

---

### Post by tekkidd on 2010-03-06
Well in order to be able to play DVD's you will need to install libdvdread

Do this with 

```
 sudo apt-get install libdvdread4

```

and then 

```
 sudo /usr/share/doc/libdvdread4/install-css.sh

```

---

### Post by DarinB on 2010-03-06
here is a screen shot of what i have installed
[ATTACH]149252[/ATTACH]

---

### Post by 3rdalbum on 2010-03-06
In the Open DVD window, specify the device file name (usually /dev/dvd or /dev/scd0) rather than the path to the VIDEO_TS folder.

---

