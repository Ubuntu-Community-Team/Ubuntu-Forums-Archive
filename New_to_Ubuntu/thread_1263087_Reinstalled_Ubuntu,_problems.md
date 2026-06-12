---
title: "Reinstalled Ubuntu, problems"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by Fableflame on 2009-09-10
Ok, so I had to reinstall Ubuntu today, and I'm having a few problems.
For one, whenever I try to update the information in the Add/Remove or the Sypnatic Mangager, I get this error.

[IMG]http://i398.photobucket.com/albums/pp67/fableflame/Screenshot-1.png[/IMG]


The next problem, is when I try to install a Flash Plugin, I get the error that the package cannot be found.

[IMG]http://i398.photobucket.com/albums/pp67/fableflame/Screenshot-1-1.png[/IMG]

So when I got the above error, I went directly to the Adobe site to download Flash Player from there. However, when I try to install it, I get an error about not having a particular dependency. Apparently I'm missing the dependency "libnspr4-dev"

[IMG]http://i398.photobucket.com/albums/pp67/fableflame/Screenshot-2.png[/IMG]

So apparently I'm missing some dependencies, and I can't connect to whatever server I'm supposed to connect to to update my sypnatic package manager and up add/remove stuff.
Can someone help please?

---

### Post by arochester on 2009-09-10
1) I can't really make out from the graphic which repositories have not downloaded. It might help is you can copy and paste your sources list here. (gksudo gedit /etc/apt/sources.list)

2) Read [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) particularly the bit that says "If you are using Ubuntu 9.04, this tutorial will be useless to you. I don't know what plugin Ubuntu tries to use by default (Gnash and Swfdec are not installed), but it tries to play YouTube instead of prompting you to display a plugin. So you can either install all the major proprietary codecs or just install flashplugin-nonfree."

Try installing flashplugin-nonfree instead of adobe-flashplugin.

---

### Post by achase79 on 2009-09-10
Are you using some kind of proxy server?  Synaptic & Add/Remove may not be set to the correct proxy settings if that is the case.

---

### Post by Fableflame on 2009-09-10
Nope. Didn't set up any proxies.

---

### Post by misfitpierce on 2009-09-10
Alot of repos mainly the security servers are updating or something and a lot of people are seeing repo errors... Hopefully it will be resolved by later tonight... Can see some discussion about repo problems in general help section.

---

### Post by Fableflame on 2009-09-10
> **misfitpierce said:**
> Alot of repos mainly the security servers are updating or something and a lot of people are seeing repo errors... Hopefully it will be resolved by later tonight... Can see some discussion about repo problems in general help section.

Oh so it's not just my computer?
*sighs in relief*
But what about the dependencies I'm missing? Are those missing because I haven't reloaded the sympnatic manager?

---

### Post by misfitpierce on 2009-09-10
It could be... If it cant update the repos to see if you have the dependancies avail for download then it can't automatically download them... Its the case in some cases, others you need to find the dependancies manually but most are usually in repos and it automatically downloads and installs when you try to install package... But since some of the repo's are down it may be why you are getting errors and why it cant find dependancies to auto download and install. Give it a bit and they should come back online and everything should work out fine.

---

### Post by Fableflame on 2009-09-10
> **misfitpierce said:**
> It could be... If it cant update the repos to see if you have the dependancies avail for download then it can't automatically download them... Its the case in some cases, others you need to find the dependancies manually but most are usually in repos and it automatically downloads and installs when you try to install package... But since some of the repo's are down it may be why you are getting errors and why it cant find dependancies to auto download and install. Give it a bit and they should come back online and everything should work out fine.

Alright. Thanks :D

---

