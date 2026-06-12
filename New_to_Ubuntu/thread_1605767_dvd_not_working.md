---
title: "dvd not working"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by N84Christ on 2010-10-25
Hi I am new to ubuntu, my ver is 10.04 and i have a compac presario laptop . My dvd player was working when i had windows but after loading ubuntu it does not play video. Is there a driver that I need to load?

---

### Post by Hippytaff on 2010-10-25
In a terminal, if you could post the results of
```

lspci

```open a terminal with CTRL+ALT+T :-)

oh...and welcome!

edit - I also have a compac presario laptop - no probs as of yet :-)

---

### Post by LowSky on 2010-10-25
open a terminal

copy and paste this command

```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb && sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb && wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2.1_i386.deb && sudo dpkg -i w32codecs_20071007-0medibuntu2.1_i386.deb && sudo apt-get install ubuntu-restricted-extras
```

What it does is add dvd playback, and install all codecs you may need in the future, plus flash, java, and more fonts to say the least.

hope that helps

---

### Post by ArgusVision on 2010-10-25
When you say "not working" do you mean the OS/applications can't see it at all, or that it won't play DVD's? 
The second problem is fixed by going to [http://medibuntu.org](http://medibuntu.org) and following the step in the repository How-to. (You'll see a link up top of that page.)

@Hippytaff 650 beans and counting! You've been busy!

EDIT: Or do what lowsky said...  show off...    :)

---

### Post by trikster_x on 2010-10-25
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Adds medibuntu to your repository.

```
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```
Adds packages from medibuntu to package managers.

```
sudo apt-get install libdvdcss2 ubuntu-restricted-extras
```
Downloads and installs the restricted extras, which are required for playback of many media formats, as well as containing the encryption key for playing older dvds.  Also installs the encryption key needed to play newer dvds.

---

