---
title: "what's wrong with sound stuff?"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by maikal_0011 on 2008-12-25
i already posted this question on this website but i didn't get right answers.....

i am using this website to watch indian news:
**[http://idesitv.com/starnews.php](http://idesitv.com/starnews.php)  **


and my sound only works on that website and playing music on my computer ( they are already downloaded on my computer) that's it

it doesn't work on any other website including Youtube.com and other websites...

so please HELP ME  i don't know what the hell is going on...
...
i can't watch any videos or anything...i starting to regret that i shouldn't have switch to ubuntu...please help

---

### Post by the.phantom on 2008-12-25
it would be nice to put a link to that other post so you don't get any more wrong answers???

have you installed the codex for streaming video and such yet?
add/remove
sound video
gstreamer?

---

### Post by RomeReactor on 2008-12-25
Hi. Besides not having any audio, do the flash videos play properly? If so, try going to 'System->Preferences->Sound' and on the first tab ('Devices') set all dropdown menus to **PulseAudio Sound Server**. Then restart Firefox and see if the videos on YouTube play audio now.

Are you using the latest version of Ubuntu (8.10)?

---

### Post by linux_tech on 2008-12-25
you are using intrepid and havn't already installed these, they are recommended:
```


sudo apt-get install gnome-alsamixer
sudo apt-get install alsa-oss
sudo apt-get install libasound2
sudo apt-get install libasound2-plugins

```
To open volume control type:

```

gnome-volume-control

```
To open gnome-alsamixer type
```

gnome-alsamixer

```

---

### Post by maikal_0011 on 2008-12-25
putting other links include everything except that website i gave you....


and gsteamer or something video whateever, i already installed on the computer long time ago and it was working until this tuesday and i haven't made any changes at all...

and yes video is working fine but no sound..

and i tried pulse audio and other terminal codes to use but nothing..

anything else or whom should i contact for this problm?

---

### Post by RomeReactor on 2008-12-25
Which version of Ubuntu are you running? Is the audio problem only on Flash videos?

---

### Post by maikal_0011 on 2008-12-27
i am running on 8.10 Ubuntu......


and it works only the website i posted before and only on music on my pc 

so

---

### Post by voodoowizard on 2009-02-23
I am having similar problems. Everything seemed to work a few days ago, so I don't know if a new update did something. Movie trailer from apple's quicktime work the link([http://idesitv.com/starnews.php)](http://idesitv.com/starnews.php)) above works but no flash/flv or java games have sound. All system sounds and local movies and mp3's work. 

Just downloaded an flv file and it played fine locally.
I Just downloaded Opera browser and it played youtube files fine where firefox had no sound.

Ubuntu 8.10 (all available updates installed) 
Firefox 3.0.6

---

