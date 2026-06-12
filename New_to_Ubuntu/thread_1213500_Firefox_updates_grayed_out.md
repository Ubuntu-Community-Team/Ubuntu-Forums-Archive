---
title: "Firefox updates grayed out?"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by RickyBobby on 2009-07-14
I have Firefox 3.0.11... I notice in the Help menu the "Check for updates" option is grayed out, and likewise in the update section in Preferences, everything is grayed out except for updates to Add ons and search engines.   Anyone know why this is, is it part of Ubuntu's customization of Firefox?  How is one supposed to upgrade to FF 3.5?  Come to think of it, I don't really know how you are supposed to upgrade packages in general, though I am aware you can do so through apt-get. Thanks for any ideas.

---

### Post by Chemical Imbalance on 2009-07-14
Because the version of Firefox you have is installed from the official Ubuntu Repositories.  It is maintained by Canonical and is updated only through your system updates, not individually by Mozilla like on Windows.

Firefox 3.5 is in the repos.  It is a rebranded version called Shiretoko.

to install 3.5:

```
sudo apt-get install firefox-3.5
```

Again, it is branded "Shiretoko" after install instead of "Firefox" but it is indeed firefox.  Don't know when the devs will rebrand it back to Firefox.

---

### Post by RickyBobby on 2009-07-14
Thanks; that makes a lot of sense, and I see it there in Synaptic.

---

### Post by lovinglinux on 2009-07-14
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by SirBismuth on 2009-07-15
> **Chemical Imbalance said:**
> Because the version of Firefox you have is installed from the official Ubuntu Repositories.  It is maintained by Canonical and is updated only through your system updates, not individually by Mozilla like on Windows.

Firefox 3.5 is in the repos.  It is a rebranded version called Shiretoko.

to install 3.5:

```
sudo apt-get install firefox-3.5
```

Again, it is branded "Shiretoko" after install instead of "Firefox" but it is indeed firefox.  Don't know when the devs will rebrand it back to Firefox.

I have read that 3.5 is branded "Shiretoko" so that it can run along side 3.0.xx, I guess as not to create confusion.  AFAIK, Shiretoko will be rebranded Firefox with Karmic.

B

---

### Post by Chemical Imbalance on 2009-07-15
> **SirBismuth said:**
> I have read that 3.5 is branded "Shiretoko" so that it can run along side 3.0.xx, I guess as not to create confusion.  AFAIK, Shiretoko will be rebranded Firefox with Karmic.

B

I see.  That's a good idea.

---

