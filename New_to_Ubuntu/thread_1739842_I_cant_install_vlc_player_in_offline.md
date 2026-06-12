---
title: "I cant install vlc player in offline"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by subairijas@yahoo.com on 2011-04-26
HI

i am a new person in world of linux,i am using ubuntu 10.10 version, i cant play mp3,video files in ubuntu. but i have vlc player(vlc-1.1.9.tar.bz2) i dnt know how to install it.please help me.
i am looking for complete guide of installation step by step, where i have put this compressed folder?any specific place? because i am stranger in this world


thanks in advance:)

---

### Post by Locke_99GS on 2011-04-26
Open a terminal. (**Applications -> Accessories -> Terminal**)
Paste this:

```

sudo apt-get update
sudo apt-get install ubuntu-restricted-extras vlc

```

You now can play media and use VLC.



The same can be done via the Ubuntu Software Centre (**Applications -> Ubuntu Software Centre**) though you will find most help in the form of terminal commands. This makes it easier for us to give commands, and for you to paste output if required.

---

### Post by subairijas@yahoo.com on 2011-04-26
> **Locke_99GS said:**
> Open a terminal. (**Applications -> Accessories -> Terminal**)
Paste this:

```

sudo apt-get update
sudo apt-get install ubuntu-restricted-extras vlc

```

You now can play media and use VLC.



The same can be done via the Ubuntu Software Centre (**Applications -> Ubuntu Software Centre**) though you will find most help in the form of terminal commands. This makes it easier for us to give commands, and for you to paste output if required.
i enter above commands in terminal, i got message like this,

subairulijas@ubuntu:~$ sudo apt-get install ubuntu-restricted-extras vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-restricted-extras
E: Unable to locate package vlc

---

### Post by krapp on 2011-04-26
You have to be online in order to download from the online repositories.

---

