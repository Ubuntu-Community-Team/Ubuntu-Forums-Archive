---
title: "how 2 install packages in ma pc?"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by seshagiri on 2009-07-21
im living in a village n derr is no net connection.
derr is only as single internet cafe in our village.
frm werr can i get enough packages?
in the internet cafe they r running windows xp.
hw can i download packages from here?

---

### Post by philcamlin on 2009-07-21
i assume you want a router to get wifi?

---

### Post by seshagiri on 2009-07-21
no i have no funds 2 get internet in ma home!
wot can i do is 2 go to internet cafe n download packages 4 ubuntu 9.04.
i hav tried once but it wasn't successful!
hw can u get full components ie setup of a package???

---

### Post by lisati on 2009-07-21
Which packages are you interested in?

---

### Post by philcamlin on 2009-07-21
whatever package you want type in

sudo apt-get install *package name*

---

### Post by seshagiri on 2009-07-21
i want g++ compilers, Audio-Vedio codecs, wine, blender, kate, music players, compiz, i can enable desktop effects it is showing dat ATI raidon's driver is not installed.
i want all these packages. pls give me a link such dat i can get these all.
n im using windows from a cafe?

---

### Post by seshagiri on 2009-07-21
im not using ubuntu nw!
im using windows from a cafe!!
i don hav internet in ma home!
i don have funds!

---

### Post by lisati on 2009-07-21
> **seshagiri said:**
> i want g++ compilers, Audio-Vedio codecs, wine, blender, kate, music players, compiz, i can enable desktop effects it is showing dat ATI raidon's driver is not installed.
i want all these packages. pls give me a link such dat i can get these all.
n im using windows from a cafe?

*Some* packages can be installed from the CD. You will need to open up the System->Software sources menu, and enable the inclusion of the CD-ROM in your software sources.

---

### Post by Mark Phelps on 2009-07-22
> **seshagiri said:**
> i want g++ compilers, Audio-Vedio codecs, wine, blender, kate, music players, compiz, i can enable desktop effects it is showing dat ATI raidon's driver is not installed.
i want all these packages. pls give me a link such dat i can get these all.
n im using windows from a cafe?
You've asked for things that may seem simple on the surface ("wine") but are really very complex. Each of these things will start with one package, which in turn, will rely on a host of others. By the time you're done, it could be well over a hundred packages.

But the number is not really the problem; it's all the details you would have to know. Not only would you have to know the specific name of each and every package, you would need to know the version, and which specific repository to use for the download.

That's hours and hours of work just to compile all that information, and hours more to type in every package ID and to do the downloads. Just understand that you're asking for a LOT of time and effort -- all for free.

---

### Post by Tyke91 on 2009-07-22
ubuntu is really for people who have a persistent internet connection.

perhaps you can try to use that internet cafe to get a hold of another distro? I know that Fedora, SuSE and Sabayon all come with DvDs that are full of packages

---

### Post by Cheesemill on 2009-07-22
Take a look at [Keryx]("http://keryxproject.org/").

---

### Post by EXCiD3 on 2009-07-22
[Keryx]("http://keryxproject.org") will do what you need as long as you have a flash drive.

Cheesemill++ :D

---

### Post by Tyke91 on 2009-07-22
:o that looks awesome!
while True: cheesemill +=1

---

