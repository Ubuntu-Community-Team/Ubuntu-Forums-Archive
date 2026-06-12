---
title: "Has anyone figured out how to install plasmoids on KDE 4.2?"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by tarahmarie on 2009-03-17
I'm just curious.  KDE-Look has removed the "How to Install" link on plasmoid pages, and I don't know how to install a 3rd party plasmoid any longer.  Is there a howto yet?

---

### Post by raul_ on 2009-03-17
> **tarahmarie said:**
> I'm just curious.  KDE-Look has removed the "How to Install" link on plasmoid pages, and I don't know how to install a 3rd party plasmoid any longer.  Is there a howto yet?

You can compile it and then in the "Add Widgets" window select Install new Widgets -> Install from local file

---

### Post by tarahmarie on 2009-03-17
I'm aware that that's what I need to do; I need to know HOW to do it.  Is there a howto somewhere?

---

### Post by raul_ on 2009-03-17
> **tarahmarie said:**
> I'm aware that that's what I need to do; I need to know HOW to do it.  Is there a howto somewhere?

You mean how to compile?

Download the source, extract it, open a console, go to the folder you extracted and:

```


$ ./configure
$ make
$ make install


```

some packages don't need those 3 steps (i don't think plasmoids even need configure, but run it anyway since it doesn't do any harm). i think "make" should do the trick.

That should generate a file which you can use to install the plasmoid.

---

### Post by arochester on 2009-03-17
"how to install additional plasmoids/widgets " at [http://kubuntuforums.net/forums/index.php?topic=3098671.0](http://kubuntuforums.net/forums/index.php?topic=3098671.0)

---

### Post by raul_ on 2009-03-17
> **arochester said:**
> "how to install additional plasmoids/widgets " at [http://kubuntuforums.net/forums/index.php?topic=3098671.0](http://kubuntuforums.net/forums/index.php?topic=3098671.0)

Oh, right, I forgot the prefixes part :(

---

### Post by tarahmarie on 2009-03-17
I was wondering if there was an updated howto.  I've already used this howto, and gotten this error message:

CMake Error at /usr/share/kde4/apps/cmake/modules/FindPlasma.cmake:13 (message):
  FindPlasma.cmake is deprecated.  Now with KDE 4.2 Plasma is part of kdelibs

That's the reason I was posting my questions; I had assumed someone had tried to install a plasmoid using these instructions and had updated the howto for this error message. I've installed many plasmoids in 4.1; this is a new problem--hence me asking specifically about installing them in 4.2.

Am I SOL?

---

### Post by txcrackers on 2009-03-18
Until the specific plasmoids are updated to work with KDE 4.2, yes, you are.

---

### Post by tarahmarie on 2009-03-18
rats.

Thanks, I appreciate it.

Any knowledge of when there will be a general update of 3rd party plasmoids?  Or is that a stoopid question?

Thanks, all.

---

### Post by raul_ on 2009-03-18
> **tarahmarie said:**
> rats.

Thanks, I appreciate it.

Any knowledge of when there will be a general update of 3rd party plasmoids?  Or is that a stoopid question?

Thanks, all.

It's up to the developers. What plasmoid are you interested in?

---

### Post by suffice on 2009-03-18
i get the same problems too...having a reallly hard time with plasmoid installs....

basically not sure of the process.....im new to KDE in general.....
.......

as i was writing this post i also found another post about stuff and it fixed things..

basically on my prefix command... take out the '..' at the end.... and then make the the  quote ' ' intead of ` ` ...

then got a msgfmt error with the cmakke  

looked at another post and installed installed 

sudo apt-get install gettext

which then allowed me to cmake path yada
then make and make installed worked..

...
still not in my widget list...but i guess a working compile is one step closer...

the whole plasmoid process has been driving me nuts for a week..

---

### Post by suffice on 2009-03-18
ok i got it all to work ....

basically forget what i said about the  `` and '' doesnt seem to matter..

the key is just having all the libs and **** installed and getting through the makes and stuff..

then 

$kbuildsycoca4

puts it plasmoid in the menu

then 

$kquitapp plasma; sleep 1; plasma

restarts plasma...

it has all worked on several plasmoids now.....

im pumped!

---

