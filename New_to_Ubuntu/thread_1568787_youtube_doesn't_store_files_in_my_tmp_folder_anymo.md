---
title: "youtube doesn't store files in my tmp folder anymore! Is it the same with you?"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by Ubunser on 2010-09-05
Today I found I can't copy the files I want while using youtube from tmp folder. Has something changed or is it smth wrong with my Ubuntu?

---

### Post by Dies on 2010-09-05
Still works here, at least for the vid I tested. I don't have HTML5 enabled.

---

### Post by qyot27 on 2010-09-05
It's not necessary to do all that, anyway.  youtube-dl is in the Universe repository.  It'll let you download the stuff without your web browser even being open. 

You can also get it from here if you want to stay updated: [http://bitbucket.org/rg3/youtube-dl/wiki/Home](http://bitbucket.org/rg3/youtube-dl/wiki/Home) - just remember to give it execution permission and copy it to /usr/bin.

---

### Post by sandyd on 2010-09-05
use flashgot.
You don't need to even exit your browser to download youtube vids....

Just right click on the icon I indicated in the screenshot when your watching the youtube video.

---

### Post by Dies on 2010-09-05
> **qyot27 said:**
> It's not necessary to do all that, anyway.
...

All what? You mean open a folder?

:confused:

---

### Post by qyot27 on 2010-09-05
> **Dies said:**
> All what? You mean open a folder?

:confused:
Going into the temp cache while the video is open in the browser, identify the files you want, copy-paste/move them somewhere else, and then rename them to something intelligible.  Especially as seeing it's tied to the browser's cache limits (and thus may fail if the cache is set too low) and takes extra steps to complete, as opposed to a single command that downloads the video directly to a regular .flv/.mp4/.webm file without being tied to the browser at all.

---

### Post by gandaran on 2010-09-06
> **Ubunser said:**
> Today I found I can't copy the files I want while using youtube from tmp folder. Has something changed or is it smth wrong with my Ubuntu?
what browser are you using?

---

### Post by Ubunser on 2010-09-06
> **gandaran said:**
> what browser are you using?

I am using Firefox

---

### Post by AlexanderDGreat on 2011-02-13
Help! This also happened to me, anyone found a solution? But opening TMP is easier than installing another program.

Please help!

---

### Post by AlexanderDGreat on 2011-02-13
Found the solution:

[http://www.youtube.com/watch?v=X4YgAnYYGdk]("http://www.youtube.com/watch?v=X4YgAnYYGdk")

Back to normal watching tutorial videos. :)

---

### Post by AlexanderDGreat on 2011-02-13
Actually you can also downgrade your Adobe Flash to 10.1

[http://www.4shared.com/file/WpiWAXMr/install_flash_player_10_linux.html]("http://www.4shared.com/file/WpiWAXMr/install_flash_player_10_linux.html")

That's better. so it can be back in /tmp

---

### Post by Vaphell on 2011-02-13
> **AlexanderDGreat said:**
> Help! This also happened to me, anyone found a solution? But opening TMP is easier than installing another program.

Please help!

so bookmark ~/.mozilla/firefox/<profile>/Cache in file browser and you have direct access to a cache directory. Where is the problem?

- open file browser in your home dir
- ctrl+h to show hidden files
- bunch of previously unseen stuff shows up, choose .mozilla, inside there is firefox dir and inside that there is your user profile. Enter it, go to Cache, where the flash videos are stored
- in filebrowser menus choose add bookmark. Done

---

### Post by lisati on 2011-02-13
May this old thread rest in peace. Before you get too carried away looking for software to help you download Youtube videos as an alternative to playing them normally, please take a look at Youtube's terms of service. 

Youtube videos play satisfactorily here without the need for trickery........

---

