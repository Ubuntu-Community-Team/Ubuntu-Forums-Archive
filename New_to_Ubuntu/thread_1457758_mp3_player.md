---
title: "mp3 player"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by 007casper on 2010-04-19
The mp3 file doesnt play on ubuntu.  When I tried to play it... system says

> 
The playback of this movie requires a MPEG-1 Layer 3 (MP3) decoder plugin which is not installed.


there are a lot of them in the synaptic package.  Which one is the right one?

thank you

---

### Post by friv_livs on 2010-04-19
Which media player are you using? (Rythmbox, totem, VLC, ...)?

---

### Post by zeroseven0183 on 2010-04-19
Please install the [Ubuntu Restricted Extras]("https://help.ubuntu.com/community/RestrictedFormats") by copy-pasting this command to a Terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

That includes the codecs necessary for playing .MP3 files on any (most of) music player.

---

### Post by Didius Falco on 2010-04-19
First, add the Medibuntu Repository to Update Manager by cut/pasting the following into the terminal:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Add to the Software Center Add/Remove listings and enable bug reporting:

```
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```

Then install the codecs package - if you are using a 64 bit version of ubuntu, it would be w64codecs instead:

```
sudo apt-get install w32codecs
```

Now your MP3's should play, along with quite a few other "flavors" of media

for playing encrypted DVDs you'll need libdvdcss2:

```
sudo apt-get install libdvdcss2
```

The above is a good starter kit - many people won't need anything more, other than flash and java.

---

