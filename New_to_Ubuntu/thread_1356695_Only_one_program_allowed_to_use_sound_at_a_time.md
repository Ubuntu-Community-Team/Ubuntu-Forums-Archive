---
title: "Only one program allowed to use sound at a time?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by frs1661 on 2009-12-16
Hello,

I've noticed some kind of conflict with sound ownership... If I, say, watch a video in VLC or Movie Player (sound works fine), then start firefox or chromium, I get no sound in the browser. If I do the reverse, sound works fine in the browser and I get no sound with the movie player. 

Running VLC, then 'sudo firefox' at the terminal, trying to play sounds in firfox gives me the following error:

```
ALSA lib ../../../src/pcm/pcm_dmix.c:1058:(snd_pcm_dmix_open) unable to open slave
```


Any tips for a linux novice on how to fix this?

TIA

---

### Post by rajeev1204 on 2009-12-16
> **frs1661 said:**
> Hello,

I've noticed some kind of conflict with sound ownership... If I, say, watch a video in VLC or Movie Player (sound works fine), then start firefox or chromium, I get no sound in the browser. If I do the reverse, sound works fine in the browser and I get no sound with the movie player. 

Running VLC, then 'sudo firefox' at the terminal, trying to play sounds in firfox gives me the following error:

```
ALSA lib ../../../src/pcm/pcm_dmix.c:1058:(snd_pcm_dmix_open) unable to open slave
```


Any tips for a linux novice on how to fix this?

TIA

Which version of ubuntu are you using?

---

### Post by frs1661 on 2009-12-16
Sorry, 9.10 64bit.

---

### Post by vvfrn on 2009-12-16
^bump^ same here
except I have 32 bit

---

### Post by llawwehttam on 2009-12-16
I have had this problem for years and am now using 8.10 32 bit and still have it. It seems to be mainly flash/java apps that conflict. It might just be sound drivers though.

EDIT: Found help article. [https://help.ubuntu.com/community/SoundTroubleshooting#head-882ddc981673f44656e4f791858e9a586a007705](https://help.ubuntu.com/community/SoundTroubleshooting#head-882ddc981673f44656e4f791858e9a586a007705)

---

### Post by joes7 on 2009-12-16
Enable your sound card.

---

### Post by llawwehttam on 2009-12-16
Right a quick update. I went to System>Preferences>sound and changed everything to ALSA. Some programs now play together . Might take a bit more work to get more working together. I will post if I have sucess.

---

### Post by frs1661 on 2009-12-18
> **joes7 said:**
> Enable your sound card.

Not sure what you mean. Everything in alsamixer is on and turned up... aplay returns the correct sound card. Sounds modules are installed. I've got ALSA 1.0.20 installed.

[quote=llawwehttam]I have had this problem for years and am now using 8.10 32 bit and still have it. It seems to be mainly flash/java apps that conflict. It might just be sound drivers though.

EDIT: Found help article. [https://help.ubuntu.com/community/So...8e9a586a007705](https://help.ubuntu.com/community/So...8e9a586a007705)[/quote]

Went through that article already... no joy :(


Also I can ONLY get sound in firefox if I sudo it. Chromium doesn't have sound if I run it as a user or superuser. Movieplayer and VLC both have sound as a regular user.

Edit: I also enabled software mixing with the following guide: [http://buglandia.blogspot.com/2007/08/howto-software-audio-mixing-in-ubuntu.html](http://buglandia.blogspot.com/2007/08/howto-software-audio-mixing-in-ubuntu.html)

---

### Post by frs1661 on 2009-12-21
Just an update... Seems to be a flash issue. I get sound on non-flash sites (i.e. ytmnd.com). I re-copied the Flash lib from the FF directory into the chrome extension directory and now flash sound works in Chrome, if run without movieplayer/vlc playing. If I'm playing a video when I start the browser, I have to pause VLC/movieplayer, kill the flash plugin in the chrome task manager, and reload the page to get sound in flash. Once the browser 'owns' flash I can't unpause the movie until I close the tab using flash.

Any thoughts? Since the seems to be a flash issue is there a better place to ask for support?

Thanks

---

