---
title: "Build Essentials"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by Otis Spunkmiyer on 2010-04-08
[SIZE=4][FONT=Courier New]Hi,

I just installed the Ubuntu 9.10 Netbook Remix and it's working wonderfully.  Would there be any need for me to run the terminal command of apt-get install build-essentials ?
I ask because I have removed somethings and install other scrips to tweak the system.  But I wonder if might have removed something that depends on something or that I simply need.  I note that when I tried the command, which I said no, until I ask in the forum, but it wanted to install allot of deb. stuff.  25mb of additional space.


[/FONT][/SIZE]

---

### Post by oldos2er on 2010-04-08
If you plan on compiling source code, or building deb packages, you'll need build-essential.

---

### Post by nothingspecial on 2010-04-08
build-essential installs various compilers and other stuff need for building source code. If you don`t do that you don`t need it.

apt will remove anything that depends on something you decide to remove and warn you about it.

---

### Post by Otis Spunkmiyer on 2010-04-08
Thank you 'both' very much.
I feel relieved, that I did not mess something up.  Everything is working.

---

