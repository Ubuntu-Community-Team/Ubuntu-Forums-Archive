---
title: "How do i open a music file with XMMS?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by jmedoro on 2009-04-19
ok, finally getting the ball rolling with integrating ubuntu into my everyday life.

I download some mp3's, and i'm trying to open them with XMMS (which i just downloaded). The songs are set to open with Totem by default, and when i right click to 'open with another application,' i'm not seeing xmms as a choice (only Rhythmbox, among others).

I'm sure XMMS is downloaded, b/c i am looking at the folder. what do i do next?

---

### Post by mprince on 2009-04-19
One thing you could try is see if XMMS shows up as a choice under:
 

System > Preferences > Preferred Applications > Media tab


If it does, you could make it your default player.

---

### Post by halitech on 2009-04-19
did you download it and install it or just download it and how?

---

### Post by mprince on 2009-04-19
OK... I think this is what you are looking for. Open a terminal and type:

```
sudo gedit /usr/share/applications/defaults.list
```

Point the *audio/x-mp3=totem.desktop *to XMMS instead of totem.

---

### Post by jmedoro on 2009-04-21
> **halitech said:**
> did you download it and install it or just download it and how?

(sorry for the delay) Ok, so i downloaded it only, looks like i didnt install. I have it in my home folder, and its just sitting there.

Hate to be naive, but what do i do next? this is the first program i am downloading/using.

---

### Post by halitech on 2009-04-21
there's info here for 8.04 but should be the same for 8.10

[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)

---

### Post by jmedoro on 2009-04-22
thanks...i tried downloading the package they had listed, and got:

'Couldn't find package libxml-dev"

either way, when i first tried downloading xmms, it was much like any download with Windows (i.e, no terminal window)...then i just extracted the program (again, as i would with a .zip or .rar in windows) but that was the end of it.

i guess i just have a fundamental flaw in my understanding for how to download and install programs in Linux, so i'm off to google some more and will return.

---

