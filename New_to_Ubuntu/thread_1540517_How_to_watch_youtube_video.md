---
title: "How to watch youtube video"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by Godblessme on 2010-07-27
Every time I try to install Adobi flash software, so that I can watch youtube video, I always get en error message. Could someone tell me what to do? By the way, my ubuntu is inside my windows XP.:KS

---

### Post by Res2216firestar on 2010-07-27
Try flash-aid: [http://flash-aid-extension.blogspot.com/]("http://flash-aid-extension.blogspot.com/").

---

### Post by jtarin on 2010-07-27
Would you like to share the error message or is it confidential?
Open Synaptic package manager with the terminal ```
gksu synaptic
```and in the search box type flashplugin-installer. It will download and install the Adobe flash player.

---

### Post by timbuktoo on 2010-07-27
flash player is also from download off the the software center

---

### Post by Jarthur121 on 2010-07-27
Go to terminal and type:

```
sudo apt-get update
```That just updates your system, then type:

```
 sudo apt-get install ubuntu-restricted-extras
```Restart your browser.

OR

Go to Ubuntu Software Centre (Applications -> Ubuntu Software Centre)

In the search bar, search for Ubuntu Restricted Extras and install that package.

Restart your browser.

Edit: The above two instructions will also download mp3 support etc.

---

### Post by Godblessme on 2010-07-27
Thanks everybody, I have successfully installed Adobi flash player using firefox update. Thanks again for all the advices.

---

