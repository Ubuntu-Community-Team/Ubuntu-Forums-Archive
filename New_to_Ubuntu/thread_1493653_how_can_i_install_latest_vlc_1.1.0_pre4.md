---
title: "how can i install latest vlc 1.1.0 pre4?"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by human75 on 2010-05-26
hi there.everytime when i tried to install latest version of vlc 1.1.0pre4, ubuntu installs vlc 1.0.6...i google it but i couldnt find soulution.can anybody provide me a solution?many thanks in advance

---

### Post by superdupont on 2010-05-26
add this PPA ?
[https://launchpad.net/~webupd8team/+archive/vlc](https://launchpad.net/~webupd8team/+archive/vlc)

---

### Post by human75 on 2010-05-26
> **superdupont said:**
> add this PPA ?
[https://launchpad.net/~webupd8team/+archive/vlc]("https://launchpad.net/%7Ewebupd8team/+archive/vlc")
how can add this to PPA?i am typing this link to PPA line under the system sources and it does not allow me to add?:(

---

### Post by Zemblan on 2010-05-26
Open a terminal. Run the commands:

```
sudo add-apt-repository ppa:webupd8team/vlc
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by human75 on 2010-05-26
> **Zemblan said:**
> Open a terminal. Run the commands:

```
sudo add-apt-repository ppa:webupd8team/vlc
sudo apt-get update
sudo apt-get install vlc
```
thanks a lot in worked perfect:) i know i asked for a vlc 1.1.0pre4 and i got it...
i am being naughty little bit but they released [URL="http://www.videohelp.com/tools/VLC_media_player"]**V**[COLOR=Black]**LC** media player.so how can i get this version.this is release candidate version:).thanks a billion in advance.[/COLOR]
[/URL]

---

