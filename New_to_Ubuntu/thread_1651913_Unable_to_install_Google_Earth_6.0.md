---
title: "Unable to install Google Earth 6.0"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by OldBoy44 on 2010-12-23
Hi all,

I fear I may have made a fool of myself! I have Ubuntu 10.04.1 installed and am trying to install Google Earth.
Looking around on the forum and elsewhere I thought that the following would be O.K.

Commands sudo apt-get install googleearth-package followed by sudo apt-get install lsb-core

Have I done too little or too much?

Google Earth hasn't appeared on Internet Menu as expected.

Any help would be gratefully received.

Cheers,  :)

---

### Post by ImDougy on 2010-12-23
i have a few ideas. download ubuntu tweak from ubuntu-tweak.com, install it, open it, go to source center and enable google stable source and refresh then try to install it. or simply download it from earth.google.com and choose 32 bit .deb or 64 bit .deb if ur running 64 bit ubuntu, then install it

---

### Post by sandyd on 2010-12-23
> **aussiebean said:**
> Hi all,

I fear I may have made a fool of myself! I have Ubuntu 10.04.1 installed and am trying to install Google Earth.
Looking around on the forum and elsewhere I thought that the following would be O.K.

Commands sudo apt-get install googleearth-package followed by sudo apt-get install lsb-core

Have I done too little or too much?

Google Earth hasn't appeared on Internet Menu as expected.

Any help would be gratefully received.

Cheers,  :)
run
```

googleearth
```

or is it
```

google-earth
```?
in a terminal

---

### Post by OldBoy44 on 2010-12-23
Thanks ImDougy - I will try that.

sandyd - both commands not found unless I didn't enter properly!

:)

---

### Post by ImDougy on 2010-12-23
i also have been trying to install google earth... hasn't been going well but it works fine in linux mint when u install it from the software manager

---

### Post by ImDougy on 2010-12-23
i also heard medibuntu has a google earth package or something so enable that source in the source center on ubuntu tweak too

---

### Post by OldBoy44 on 2010-12-23
Thanks ImDougy - I can't find Software Manager! - shows how much of a newbie I am.


:(

---

### Post by ImDougy on 2010-12-23
o.o thank u aussiebean! until now i couldn't get google earth to launch when i clicked the icon, until i typed that command u typed up there (sudo apt-get install lsb-core) now google earth launches and works perfectly. after u enable google stable source just look 4 it in the software center or type in a terminal:

sudo apt-get install google-earth-stable

and the software manager is in linux mint... in ubuntu u have ubuntu software center

---

### Post by OldBoy44 on 2010-12-24
I'm glad I did a little to help you ImDougy.

Software Center says googleearth - package is installed - problem is I can't see it on a menu!

:(

---

### Post by ImDougy on 2010-12-24
once u install google earth it should be in the internet category

---

### Post by clhsharky on 2010-12-24
aussiebean

Google Earth 6.0 is still beta and not in repos.

.deb files Google Earth beta and stable are here

[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

tic advance setup for choice.
download your choice, double click to start install.

Sharky

---

### Post by ImDougy on 2010-12-24
idk how to delete this post sooooooo ignore this lol

---

### Post by OldBoy44 on 2010-12-24
Thanks Sharky.

:p

---

### Post by ImDougy on 2010-12-24
r u sure u installed google earth? r u sure it's not the utility that automatically builds a debian package?

---

### Post by OldBoy44 on 2010-12-24
Hi all,

As I hadn't downloaded Wubi long ago I decided to take the plunge and un-install re-install.
I decided to do this as I didn't know how to undo commands I had already entered.

Anyway, the end result was that I had success by downloading from site suggested by Sharky and then entering command sudo apt-get install lsb-core.

The end result - I now have Google Earth working and I am very happy!

Thanks go to Sharky and ImDougy for their contributions!

  :popcorn:

---

### Post by ImDougy on 2010-12-24
ur welcome ^_^ enjoy ur google earth lol

---

