---
title: "minimal configuration"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by RoseBlack on 2011-03-13
i have an old computer at home, and i want to install a version of linux on it. it has only 256 mb of ram, 766 mhz cpu, and 80 gb hd. will ubuntu 10.10.4. or 10.10. lts work on this?

my friend says, it works perfectly on his computer with 512 mb ram, and is much faster than with windows xp. i have now xp on this computer, it's generally ok, i have nothing to complain, it's fast, memory usage is always under 60%, but every now and then is full of viruses and malware.

if ubuntu won't work, is there another version of linux similar to ubuntu, but that will run optimally on my computer?

---

### Post by Paqman on 2011-03-13
The default installs of Ubuntu won't run well on only 256MB, but will run reasonably well on 512MB.

You can do a minimal install of Ubuntu that will result in a much lighter desktop than the default. To do this you just install the stripped down versions of whatever desktop environment you prefer, on top of the minimal install (which starts off with just a command line). You can use the script in my sig to do this for you. If you want something very similar to default Ubuntu then install Gnome core as your desktop environment.

However, the desktop environment is only half the picture. You'll also want to use lightweight apps on it, or you'll find you run out of RAM quickly. Instead of running hefty office apps like Open or Libre Office i'd suggest lighter ones like Abiword and Gnumeric. You could also switch to web apps instead, so that you're only running your browser. SOme good webs are Google Docs or Zoho Office for office apps, pixlr.com for editing photos, and Grooveshark for music.

Of course, the best solution is to get your hands on some more RAM that matches the machine and stick it in the slot!

---

### Post by RoseBlack on 2011-03-13
so, if i add 256 mb ram it will work just fine?
i wanted to add 1 gb, but my motherboard doesn't support more than 512 mb.

till then, i think that minimal installation of ubuntu or linux mint lxde rc will work just fine.
i hope so. :D__[]("http://blog.linuxmint.com/?p=1661")

---

### Post by Paqman on 2011-03-13
> **RoseBlack said:**
> so, if i add 256 mb ram it will work just fine?
i wanted to add 1 gb, but my motherboard doesn't support more than 512 mb.


The jump from 256MB to 512MB will make a _huge_ difference, yes. It won't ever be fast on that machine, but it'll definitely be usable.

> 
till then, i think that minimal installation of ubuntu or linux mint lxde rc will work just fine.
i hope so. :D__[]("http://blog.linuxmint.com/?p=1661")

Hope so. If you have any problems, don't hesitate to ask.

---

### Post by Paddy Landau on 2011-03-13
There is a lightweight version of Ubuntu, called [Lubuntu]("http://www.lubuntu.net/"). I suggest you try that. It works well on my old computer.

If you need a very light version of Linux, try [Puppy]("http://puppylinux.org/"). It's terribly basic but lightning fast and small.

---

### Post by cap10Ibraim on 2011-03-13
I suggest trying a Puppy Live Cd first if you can live with it ? who knows ! ):P

---

### Post by Old_Man_Unix on 2011-03-13
> **Paddy Landau said:**
> There is a lightweight version of Ubuntu, called [Lubuntu]("http://www.lubuntu.net/"). I suggest you try that. It works well on my old computer.


+1

Lubuntu, which is a ***Ubuntu derivative***  based on LXDE,  runs quite nicely in 256Mb and really screams if you have more RAM. It is not yet "recognized" by Canonical but it is a derivative in every other sense.

I have to disagree with some of the people here about running Ubuntu on low RAM/legacy PCs.  We've done some work restoring computers for non-profits.  Ubuntu runs only marginally on, say, a P3 or a Celeron with 512Mb, and is plainly unsatisfactory on anything less than that.  You've got to remember that there are user expectations involved and while you might be willing to overlook marginal performance for yourself, others might not be so tolerant.

The applications that Ubuntu installs by default, like OpenOffice/LibreOffice and Firefox,  are also heavy consumers of RAM.  GNOME itself  is no lightweight, either.  Of course, you can swap those out for lighter applications,  or run a custom installation, but then, are you really running Ubuntu?  And why would you do that when there are lightweight distributions that accomplish the same thing?

We rejected Puppy Linux for security reasons.

There are other lightweight distros based on Lubuntu/Ubuntu, such as Bodhi and Peppermint Ice. They aren't derivatives, however,  and although based on Lubuntu, they depart significantly from it.  You might want to consider them, however.  Worth a look-see.

---

### Post by Paqman on 2011-03-13
> **Old_Man_Unix said:**
> GNOME itself  is no lightweight, either.

You might be surprised. Gnome-core comes in at about 100MB, which is pretty light in my book. It's ubuntu-desktop that's flabby.

So yes, you can have a lightweight Gnome desktop, and if you run lightweight apps on it then it'll do just as well as some of the DEs that are more traditionally considered lightweight. If you're going to be running GTK apps anyway i'd suggest there's minimal advantage to running a non-Gnome DE, as you'll be loading a lot of Gnomey libs anyway.

Having said that, there's nothing wrong with running LXDE or XFCE, and I support them all in my minimal script. I just don't think it's always a clear-cut as Gnome = fat, others = skinny. Except for KDE, which really is fat, and no longer has a minimal package available anyway.
 
I'm inclined to suggest forgetting about desktop apps for a slower machine anyway. Just use a fast browser and web apps. As long as your machine can render all the client side scripting ok you offload a lot of the heavy lifting onto somebody else's server.

---

