---
title: "No sound through headphones in Ubuntu 11.04"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by LavenderBlack on 2011-08-05
Hi all,
Im not able to hear any sound through headphones in Ubuntu 11.04. My  laptop is Toshiba satellite L640. Even if i plug in the headphone, the  sound comes out of the speakers alone. I dunno how to fix it, can  someone help me?

---

### Post by Daveth on 2011-08-05
this post

[HTML]http://groups.google.com/group/ilug-tvm/msg/a4236f6363c40c30
[/HTML]

suggests that is a bios bug and can fixed by a Toshiba upgrade.

Alternatively, and probably more safely since bios upgrades always strike terror in me, follow this ubuntu post

[HTML]http://ubuntuforums.org/showthread.php?t=1613746[/HTML]

from post 10 onwards

---

### Post by Basher101 on 2011-08-05
You should know that updating a BIOS comes with a lot of risks. If you mess up, your motherboard is rendered useless. Be very careful when doing anything to the BIOS.

---

### Post by Daveth on 2011-08-05
hence my warning!!!!:D

---

### Post by Basher101 on 2011-08-05
I will soon build my own Desktop PC, with specs like 8 GB RAM, quadcore CPU, Graphic cards with 2 GB VRAM and such...a real nice gaming system with some horse power under the hood :D Then BIOS flashing should be less troublesome - the newest Motherboards come with 2 Chips, one flashable and the other untouchable so you always have a backup.
edit: check your motherboard if you have 2 chips...could save you the fear of messing up^^

---

### Post by LavenderBlack on 2011-08-08
> **Daveth said:**
> this post

[HTML]http://groups.google.com/group/ilug-tvm/msg/a4236f6363c40c30
[/HTML]

suggests that is a bios bug and can fixed by a Toshiba upgrade.

Alternatively, and probably more safely since bios upgrades always strike terror in me, follow this ubuntu post

[HTML]http://ubuntuforums.org/showthread.php?t=1613746[/HTML]

from post 10 onwards
Thank u very much Daveth.. :) I fixed my prob from the solns provided in the link of ubuntuforum u hav sent... :) :)

---

### Post by LavenderBlack on 2011-08-08
Just follow by copying & pasting all commands, line by line in Terminal. That's it. :razz:

1. Add new repository for newest alsa driver.

**[SIZE=2]*sudo add-apt-repository ppa:ubuntu-audio-dev/ppa*[/SIZE]**
  [B][SIZE=2][I]sudo apt-get update
[/I][/SIZE][/B]
2. Then install newest alsa driver by[B][SIZE=2][I]

sudo apt-get install linux-alsa-driver-modules-$(uname -r)[/I][/SIZE][/B]

3. Once you get new driver installed properly then open alsa config file by

[SIZE=2]***sudo gedit /etc/modprobe.d/alsa-base.conf***[/SIZE][SIZE=3]
[/SIZE]
4. Add this line at the bottom of this file

[SIZE=3]*[SIZE=2]**options snd-hda-intel model=ideapad**[/SIZE]*[/SIZE]

5. Then restart.

---

### Post by Daveth on 2011-08-09
pleased that one worked out for you. Happy listening!

---

