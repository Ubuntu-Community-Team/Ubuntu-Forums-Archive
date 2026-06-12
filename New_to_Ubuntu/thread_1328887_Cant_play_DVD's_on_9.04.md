---
title: "Cant play DVD's on 9.04"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-11-16
I have been trying for the past hour to play a DVD on Ubuntu 9.04, i had folowed this [http://www.zolved.com/synapse/view_content/28220/How_to_play_DVDs_on_Ubuntu](http://www.zolved.com/synapse/view_content/28220/How_to_play_DVDs_on_Ubuntu)

Still nothing, i pop the DVD in and it asks if i would like to play in movie player, i click ok and it opens movie player for a split second then it shuts it down. Any ideas?

---

### Post by herbertportillo on 2009-11-16
Follow these instructions, and you should be able to watch DVD's.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Rave Gloves on 2009-11-16
I followed your instructions, and still nothing, Mplayer keeps closing down :/

---

### Post by 3rdalbum on 2009-11-16
Use VLC media player. If problems persist, try running VLC from the terminal and post any error messages you get in the terminal.

---

### Post by dillandriskell on 2009-11-16
Hmm, I'd recommend installing two things, let me know if it works.

Open up a terminal (**Applications > Accessories > Terminal**) and then type;

```
sudo aptitude install libdvdcss2 && sudo /usr/share/doc/libdvdread4/./install-css.sh
```

This is DVD support.  Then when it's done type this;

```
sudo apt-get install vlc mplayer
```

This will install VLC player and Mplayer.  Both have worked fine for me in DVD support.  I would recommend VLC as your default player by the way, as it plays virtually any kind of multimedia.

Then when you're playing a DVD make sure it opens with VLC.  If it opens automatically you might have to close it then go to **Places > Computer** and open it manually from there with VLC (right click > open with..., then find VLC)

---

### Post by Rave Gloves on 2009-11-16
Thank you so much you guys!. it worked (:

---

