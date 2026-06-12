---
title: "How do I download and install the VLC player"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Amockineuropa on 2009-10-08
I would like to download/install the VLC player onto my Ubuntu setup. How is this done. Also like to install Mozilla Thunderbird.

---

### Post by wojox on 2009-10-08
Go to System > Admin > Synaptic Package Manager and search for both of them. Their in there.

---

### Post by Amockineuropa on 2009-10-08
Will this permit me to play my mp3?

---

### Post by halitech on 2009-10-08
VLC should play them as it includes most codecs you will need. If you want to install the codecs so most players will play them, install the Ubuntu restricted package
```
sudo apt-get install ubuntu-restricted-extras
```
there is also info here on multimedia

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by jeremyswalker on 2009-10-08
I'm not sure about mp3's. However, even if it doesn't, install the package 'ubuntu-restricted-extras'. That should get you playing mp3's. If that doesn't work, might I suggest the package 'gstreamer0.10-fluendo-mp3'.

---

### Post by arochester on 2009-10-08
To play an MP3 install: ubuntu-restricted-extras

---

### Post by Viva on 2009-10-08
Just install ubuntu-restricted-extras to play mp3s. I have never been a big fan of VLC for playing music.

---

### Post by OlsenCNC on 2009-10-08
Or

Go into Add/Remove Applications, switch "Show" to "All Available Applications", Type VLC in the Search Box and Seclect VLC to install VLC Media Player.

---

### Post by nhasian on 2009-10-08
vlc has all the codecs built in, so you dont need to install anything else.  in a terminal type:

```
sudo apt-get install vlc
```

however, I do also recommend you run these other two commands so that you get codecs and dvd playback for other stuff:

```
sudo apt-get install ubuntu-restricted-extras
```

and

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

that should do it.

---

### Post by Amockineuropa on 2009-10-08
Thanks that worked

---

### Post by Garrettheif on 2010-05-09
Hey guys im too having the same problem........i want a vlc setup which can be downloaded and later installed and iam using ubuntu 9.04 .................................pls.help me to solve out the problem

---

### Post by Garrettheif on 2010-05-09
Hey guys im too having the same problem........i want a vlc setup which can be downloaded and later installed and iam using ubuntu 9.04 .................................pls.help me to solve out the problem

---

