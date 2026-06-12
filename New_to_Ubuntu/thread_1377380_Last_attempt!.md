---
title: "Last attempt!"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by iggy pop on 2010-01-10
I have tried to download the getdeb installer package:

getdeb-repository_0.1-1~getdeb1_all.deb

and i eventually located it in the /tmp folder. So i right-clicked on the package and extracted it's contents to that folder.

Could someone tell me how i can install this package now please.

Thanks in advance.

---

### Post by cosine352 on 2010-01-10
just double click will install the application. But i do not know why are you installing it.

---

### Post by cartisdm on 2010-01-10
I'm a little confused, I thought the getdeb installer package came in the ubuntu distros by default.  What version are you running and what exactly are you trying to accomplish?

---

### Post by techno-mole on 2010-01-10
why dont you just download it to your home folder and then double click on it ? thats how i normally install .deb files ?
 

go to this page - [http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install) and select the first option, the " install the getdeb package " 

click the link and your browser will either download the file to a default location, or it should ask you where you want to download it to.

once downloaded double click the file and follow the prompts, at some point it should ask for your password, and it will also warn you of any dependency issues, it should be as simple as that, least thats how it went for me when i installed it.

cheers.

---

### Post by iggy pop on 2010-01-10
I am trying to install Songbird and like the noob i am keep failing. I have checked in Synaptic and the getdeb installer package was not there.

When i click on "install the getdeb package" it is saved in the /tmp folder. There is a lock image on the package so would this mean that i would have to change permissions so that i could then double click the package to install it?

How do you change permissions?

Sorry for being a noob it's really not easy

---

### Post by techno-mole on 2010-01-10
what browser are you using ?

i use firefox, and it either downloads to the desktop (by default) or it downloads to my home folder (which is what i set it to do)

if you are using firefox go to edit --> preferences and select the main tab.

then where it says downloads you can either set it to ask you where you want stuff downloaded to, or you can set a location, i would suggest either your desktop, or your home folder, so select " save files to " and then point it to the location of your home folder etc

once you have done that try downloading the file to your home folder and then double clicking it, its easier this way, and you wont have to keep messing around like this for future downloads.

you could also move the .deb file to your home folder, but try the method above first.

---

### Post by iggy pop on 2010-01-10
I have opened Firefox clicked on Edit -> Preferences save all files to "Downloads" but for some reason the getdeb installer package get sent to the /tmp folder.

I drag the getdeb installer package to the desktop (it still has the lock image above it) double click on it and .....nothing?

---

### Post by L Campbell on 2010-01-10
> **techno-mole said:**
> what browser are you using ?

i use firefox, and it either downloads to the desktop (by default) or it downloads to my home folder (which is what i set it to do)

if you are using firefox go to file --> preferences and select the main tab.

then where it says downloads you can either set it to ask you where you want stuff downloaded to, or you can set a location, i would suggest either your desktop, or your home folder, so select " save files to " and then point it to the location of your home folder etc

once you have done that try downloading the file to your home folder and then double clicking it, its easier this way, and you wont have to keep messing around like this for future downloads.

you could also move the .deb file to your home folder, but try the method above first.

With all due respect here, when you wrote "firefox go to file --> preferences", should that have been, "edit --> preferences"?

Kind regards.

---

### Post by techno-mole on 2010-01-10
okay, thats odd.

try this.

open terminal and type the following - 

```
sudo dpkg -i 
``` just copy and paste it into terminal.

then find the .deb file and drag it onto the terminal, (make sure you leave 1 space between the -i and the start of the .deb file) it should pop into it, then hit enter.

you should be asked for your password, type it in.

it should then start to install it, if you get any errors this maybe down to dependencies, but we can look at that later.

---

### Post by techno-mole on 2010-01-10
> **L Campbell said:**
> With all due respect here, when you wrote "firefox go to file --> preferences", should that have been, "edit --> preferences"?

Kind regards.

yes your are right, my bad, sorry about that.

i would suggest that the op do this anyway, at least this way downloaded files should be easy to find.

PS - I have amended that particular post :-)

---

### Post by iggy pop on 2010-01-10
Did as you suggested and it did appear to install but can't find where?

---

### Post by techno-mole on 2010-01-10
its under applications, sound and video on my system, which is where it should be i guess.

you can always go to synaptic and then search for songbird, then highlight it and at the top should be a button that says properties, if you click this and then installed files it will show you where all related files are located, you can create your own launcher easy enough.

---

