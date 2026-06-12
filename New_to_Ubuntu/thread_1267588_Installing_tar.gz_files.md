---
title: "Installing tar.gz files?"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by XKCD64 on 2009-09-15
How do I?

To me, it just shows up as a bunch of folders inside of a big one.  =/

How do I install it?

---

### Post by N9NE on 2009-09-15
Hmm, This should help you

[http://lmgtfy.com/?q=How+to+Install+Tar.gz+Files](http://lmgtfy.com/?q=How+to+Install+Tar.gz+Files)

Reply Back And let us see how it worked out for ya'

---

### Post by MelDJ on 2009-09-16
try this too: [How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually")

---

### Post by Paqman on 2009-09-16
Generally speaking, it's easiest to stay away from them. 

You should always check Synaptic to see if it's available there. If that doesn't work you can try sites like [Getdeb]("http://www.getdeb.net/"), where you can get a nice smple .deb file to install. The other option is Googling for a PPA, which is a private repo you can add. Sometimes they have packages that are more up-to-date or not available in the normal Ubuntu repos.

---

### Post by nhasian on 2009-09-16
if you tell us what package your trying to install we might be able to find a deb or ppa for you instead of compiling something yourself.

---

### Post by 3rdalbum on 2009-09-16
> **XKCD64 said:**
> How do I?

To me, it just shows up as a bunch of folders inside of a big one.  =/

How do I install it?

There should be a file inside the folder called "INSTALL". This contains installation instructions.

If you are asked at any point to install something that the software depends on, then install it from Synaptic Package Manager. (You might need the "-dev" development headers).

If you get confused, then just stick to the software from the repositories until you know Linux better.

---

### Post by bruno9779 on 2009-09-16
I don't think that you should stay away from compiling SW yourself.
most of the times it is as simple as running the following commands from the folder you extracted from tar.gz: 

```

./configure
make
makeinstall
```
Think about is as if you where downloading a recipe instead of a take away:

./configure  checks that you have all the right ingredients
make         chops them and
makeinstall  bakes them

_________________

On a side note, I don't think it is a very good Idea to run Karmic alpha for testing if you aren't aware of compiling and dependencies installing.

---

### Post by Paqman on 2009-09-16
> **bruno9779 said:**
> 
On a side note, I don't think it is a very good Idea to run Karmic alpha for testing if you aren't aware of compiling and dependencies installing.

+1

I'd also point out that compiling your own software can lead to an unstable system, as it breaks the dependency system in your package manager. It's always preferable to use a proper .deb package.

---

### Post by wobin77 on 2009-09-16
> **bruno9779 said:**
> I don't think that you should stay away from compiling SW yourself.
most of the times it is as simple as running the following commands from the folder you extracted from tar.gz: 

```

./configure
make
makeinstall
```Think about is as if you where downloading a recipe instead of a take away:

./configure  checks that you have all the right ingredients
make         chops them and
makeinstall  bakes them

_________________

On a side note, I don't think it is a very good Idea to run Karmic alpha for testing if you aren't aware of compiling and dependencies installing.

I would recommend ./checkinstall

So it can be removed quite easy if needed.

---

### Post by XKCD64 on 2009-09-16
I'm installing a theme,  is there an easier way?

---

### Post by fraser_m on 2009-09-16
Open up Appearance, and drag the .tar.gz into the Theme tab.

---

### Post by freackout on 2009-09-16
> **XKCD64 said:**
> I'm installing a theme,  is there an easier way?

yes you may find a filename.deb file out there. ie theme.deb or theme1.deb ect.

---

### Post by morelia on 2009-09-18
Hi, my name is Juan. Sorry to get in the conversation; I am a totally (first contact with lynux products) newby at lynux and I tried to download and install the USB bootable creator --I think-- and the system told me something like "can't open the file because not having the .tar.gz application extension handler, modify your preferences" or something like that . . . Where can I find info on how to do exactly that? please . . .  :-)

---

### Post by jmszr on 2009-09-18
Juan,

You didn't state which version of Ubuntu you are using. The USB Creator has been standard since 8.10 - so perhaps you are using 8.04 - in which case you can download a .deb for the USB Creator here: [http://packages.ubuntu.com/en/hardy-backports/all/usb-creator/download](http://packages.ubuntu.com/en/hardy-backports/all/usb-creator/download) . Just click on one of the mirrors and the GDebi Package Installer should take care of the rest.

---

### Post by camaron1 on 2009-09-18
> **XKCD64 said:**
> I'm installing a theme,  is there an easier way?

Go to System>Preferences and open Appearance. Just drag and drop your tar.gz file. If the theme is compatible that is all you need to do.

---

