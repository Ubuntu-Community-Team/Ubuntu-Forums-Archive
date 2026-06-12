---
title: "XXXX needs dependency, needs dependency, needs dependency"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by M3TAL1QU1D on 2008-06-25
I seemed to have ran into a freakin circle. i am trying to install kppp on ubuntu 8.04 for my sierra 595u wireless card (which is my only means of getting on the internet in ubuntu) and i needed to satisfy a list of dependencies. The problem is i ran into 3 packages that need eachother to install. Example:

In order to get kppp going, i need:

kdelibs4c2a, 
which needs kdelibs-bin, 
which needs kdelibs4, 
which needs kdelibs4c2a
which needs kdelibs-bin, 
which needs kdelibs4,
ect....

What the hell!!??? its like a freakin triangle!! is there anyway to get around this, or is there something similar to kppp i can use for my card??? Any takers????

---

### Post by utsuprainfra on 2008-06-25
try downloading and installing the package files manually with a force switch?

---

### Post by M3TAL1QU1D on 2008-06-25
oh, i shoulda mentioned im a newbie to linux too.... i got the 3 packages sittin on my desktop (in a triangle shape actually). as for force switchig them, i am not too sure how to do this.:)

---

### Post by markkie on 2008-06-26
> **M3TAL1QU1D said:**
> I seemed to have ran into a freakin circle. i am trying to install kppp on ubuntu 8.04 for my sierra 595u wireless card (which is my only means of getting on the internet in ubuntu) and i needed to satisfy a list of dependencies. The problem is i ran into 3 packages that need eachother to install. Example:

In order to get kppp going, i need:

kdelibs4c2a, 
which needs kdelibs-bin, 
which needs kdelibs4, 
which needs kdelibs4c2a
which needs kdelibs-bin, 
which needs kdelibs4,
ect....

What the hell!!??? its like a freakin triangle!! is there anyway to get around this, or is there something similar to kppp i can use for my card??? Any takers????
To get kppp installed open a console and type:-   sudo apt-get install kppp - That should take care of all dependencies.

---

### Post by markkie on 2008-06-26
You might also find this post helpful  [http://www.pbandjelly.org/2006/12/sierra-wireless-aircard-595-configuration-sprintpcs/](http://www.pbandjelly.org/2006/12/sierra-wireless-aircard-595-configuration-sprintpcs/)  

Good luck:)

---

### Post by dmizer on 2008-06-26
did you try just doing:
```
sudo aptitude install kppp
```
i think this package is part of the ubuntu repositories, so you don't need to install separate packages, and aptitude will resolve all your dependencies for you.

---

### Post by M3TAL1QU1D on 2008-06-26
well, neither of those commands worked for me.... i already have a manual for linux setup for my card from sprint, but thanks for the info markkie!

I am installing the packages manually because i have no access to the internet. Ive been downloading them in vista, sending them to ubuntu via sd card, installing the packages, and meeting the dependencis required untill i ran into this little snag. its weird how that is, i cannot install one without the other one, which needs another one, which needs the first one, but cand be done without the second one ect....

if i can get my card up and going i will be set. as of now, this is my only way on the internet with ubuntu and it does not work yet. the sprint manual for my 595u card calls for kppp and has specific instrctions for it. that is why i am working so hard to get kppp installed, just to run into a problem like this.

i wonder if it is possible to just get the repositories on cds or dvds thru the net. if so i can do that. it may have kppp and its reqired dependencies.

---

### Post by unutbu on 2008-06-26
Click on System>Administration>Synaptic Package Manager. Click on kppp and mark it for installation.
Then click on File>Generate package download script.
Save the script as, say, "dlscript".

Quit Synaptic.

Now copy dlscript over to Vista (via the sd card)

Boot Vista. Open dlscript in a text editor. It will show all the packages you will need to install kppp.
Download each of them. Copy them over to Ubuntu.

On Ubuntu, place the .deb files all in a directory by themselves. Then you can install kppp with the command

```

cd /path/to/directory/with/the/.debs
sudo dpkg -i *.deb
```

---

### Post by M3TAL1QU1D on 2008-06-29
thanks for everyones help, but i got the internet to work using gnome-ppp with no dependencies!!

---

