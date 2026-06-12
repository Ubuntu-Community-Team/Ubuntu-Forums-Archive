---
title: "Cleaning up your computer"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by moonoo on 2009-09-18
Hi All,

For those newcomers who have a hankering to clean up your computer routinely here is a little script that I run to keep everything tip top (not that you really need it) :)

Open a terminal and type in the following:

```

touch cleanup.sh

```

then 
```

nano cleanup.sh

```

then type in the following

```

#! /bin/bash
reset
echo -e '\E[34;47mTaking the Trash out.'; tput sgr0
rm -rf  /home/<< your username >>/.local/share/Trash/files/*
rm -rf  /home/<< your username >>/.local/share/Trash/info/*

echo -e '\E[34;47mFixing Apt.'; tput sgr0
dpkg --configure -a
apt-get -f install

echo -e '\E[34;47mPerform repository update.'; tput sgr0
apt-get update

echo -e '\E[34;47mPerform any upgrades.'; tput sgr0
apt-get upgrade

echo -e '\E[34;47mKilling Orphans.'; tput sgr0
deborphan --guess-all | xargs apt-get -y remove --purge

echo -e '\E[34;47mAutoremove.'; tput sgr0
apt-get --yes autoremove --purge

echo -e '\E[34;47mAuto clean.'; tput sgr0
apt-get --yes autoclean --purge

echo -e '\E[34;47mMoooo'; tput sgr0
apt-get moo

```

save and close (control+O then control+X)

then type 
```

chmod +x cleanup.sh

```

to run open the terminal and type
```

sudo su
<your password>
./cleanup.sh

```

Hope that helps somebody

:)

---

### Post by k3lt01 on 2009-09-18
Here's another thread called ["HOWTO: Cleaning up all those unnecessary junk files..."]("http://ubuntuforums.org/showthread.php?t=140920") for the same end result that explains everything as you go.

---

### Post by moonoo on 2009-09-18
Ooops, sorry for old news!

Ok, disregard my post above as I am sure it's all been covered before!

:P

---

### Post by k3lt01 on 2009-09-18
Hey variety is the spice of life, giving people the choice to do things in the way that suits them the best is a gift worth giving. You have provided another option (not that I have tried it) that others may prefer.

Keep up the good work :popcorn:

---

