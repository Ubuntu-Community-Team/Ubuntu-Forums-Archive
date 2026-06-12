---
title: "ndiswrapper doesnt seem to exist, using 6.10btw"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by Mooney on 2007-02-12
Hi, i downloaded 6.10 the other day and at the moment im dual booting it with windows, just while i get used to it and them later on im planning on formatting and just using ubuntu, but thats irrevelvant at the moment.

My problem is this, i have a belkin F5D7000 wireless network card already installed in the computer, but i cant seem to get anything to happen with it.

iv tried installing the drivers but when i do the ndiswrapper -i thing it says command not found. i read elsewhere that i needed to go into synatics package manager and install it, but its doesnt seem to be there.

am i doing something wrong? i tried searching the forum but i didnt find a similar problem, if someone could just point me in the right direction that would be great.

thanks in advance.


Mooney

---

### Post by moitio on 2007-02-12
try "sudo apt-get install ndiswrapper-utils-1.8" - that should install it with the other package it's dependant on.

---

### Post by Mooney on 2007-02-12
not sure what i was supposed to do with "sudo apt-get install ndiswrapper-utils-1.8" so i tried typing it in the terminal and looking in that package manager for it, both with no success.

i took a [screenshot]("http://mooney.sitesled.com/ubuntu%20screenshot.png") so you can have a look for yourself.

---

### Post by moitio on 2007-02-12
It seems you don't have the right repositories. See [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu") for a guide on what to do.

I think you need the universe repositories.

---

### Post by Mooney on 2007-02-12
alright i got ndiswrapper back.

what i did was put the unbuntu CD back in and ran the packages manager and in file or something there was an add cd button, so i did that and then it brought up all the packages that hadnt been installed.

just though id post what i did incase anyone else gets the same problem.

now i just have to try and get the network to actually work.

---

