---
title: "complete n00b to ubuntu, migrating from the darkside....virtual machines?"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by jotto! on 2009-11-10
Hey guys and gals!
Have just installed ubuntu as a dual boot on my xp pro box and have to say Im liking it! Will take me a little while to get my head around it after all these years of MS brain washing!

Have been doing a little research and have to admit Im a little daunted about becoming a free man.
I have a few applications that I would like to run under ubuntu such as Dreamweaver and tried wine ( although if Im honest I didnt have a clue as to what I was doing ) and I also looked at cross over. Neither of which appeared to work, but that could just be me!

Anyway, I read up on virtual machines and saw that I could use ubuntu as my host and have a virtual XP in which these programs would work.

What do you guys run or what would you recommend I run. Ideally, free software would be my ideal as I would like to get away from my bad habit of downloading windows based software from not so nice sites.

Failing that, if there is a program I could buy without paying more in to Bill's pockets, that would be fine with me!

Sorry if this question has been asked hundreds of times before.

Cheers! ):P

Just a quick edit, I installed version 9.10 and have had no problems with it at all....seems others maybe experiencing a few teething troubles? AND all my hardware worked from the second it first booted...no messing around installing drivers! w00t!

---

### Post by chazn85 on 2009-11-10
a good free virtual machine is "virtualbox"  which can be found here [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by Schendje on 2009-11-10
> **jotto! said:**
> Hey guys and gals!
Just a quick edit, I installed version 9.10 and have had no problems with it at all....seems others maybe experiencing a few teething troubles? AND all my hardware worked from the second it first booted...no messing around installing drivers! w00t!
Yeah, but keep in mind that this is a support forum, so most of the topics will be about problems. :D

I didn't have any trouble either, installing went like a charm.

> **chazn85 said:**
> a good free virtual machine is "virtualbox"  which can be found here [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
I use this one too. It's also in the Software Center for easy installation (not the latest version though).

Works great with Windows 7. Use it to run Microsoft Office and Adobe's CS when I need to. :)


//Edit: about Dreamweaver... I think Kompozer is also a WYSIWYG HTML editor, but I personally use Bluefish (and am looking at Geany) for web development. For pictures, Inkscape is a great vector editor.

Good luck, and welcome to freedom! :D

---

### Post by jotto! on 2009-11-10
> **Schendje said:**
> 
//Edit: about Dreamweaver... I think Kompozer is also a WYSIWYG HTML editor, but I personally use Bluefish (and am looking at Geany) for web development. For pictures, Inkscape is a great vector editor.

Good luck, and welcome to freedom! :D

Thanks for the prompt replies! liking this forum already!!!!

I only use dreamweaver as it was given to me and seems fairly easy in split mode...Im not to good with code, WYSIWYG is more my thing. Will check out Kompozer and the others you mention.


Am now looking at virtualbox, thanks again!

---

### Post by Mark Phelps on 2009-11-10
> **jotto! said:**
> ... 
I have a few applications that I would like to run under ubuntu such as Dreamweaver and tried wine ( although if Im honest I didnt have a clue as to what I was doing ) and I also looked at cross over. Neither of which appeared to work, but that could just be me!
...

Don't sell yourself short!  Wine is not the "miracle cure" that some folks claim.  It runs some stuff well, other stuff OK, and other stuff not-at-all.

Besides, migrating away from MS Windows means leaving that behind, NOT find a way to continue the enslavement but on a Linux box!

Congrats for making the leap and welcome to Ubuntu.

---

### Post by cob05 on 2009-11-10
> **Schendje said:**
> I think Kompozer is also a WYSIWYG HTML editor, but I personally use Bluefish (and am looking at Geany) for web development.
 
Geany is great for web development.  I use it for my PHP coding and love it.  I had a great editor (commercial) on Windows that I thought I would miss a lot when using Linux but then I found Geany (free!) and it is a great replacement.  I recommend it highly.

---

### Post by jotto! on 2009-11-10
I think some of the web design packages may be a little too complicated for me right now...I really am just using DW to do a bit of text and a few pics, ie, [www.pamsghia.co.uk](www.pamsghia.co.uk) which is in need of updating but it gives you an idea of what im trying to do. I just type some blurb and insert a few pictures and videos! lol.

Have DL the Kompozer tar file...now to work out what to do with it.....google is my friend I think!

---

### Post by undecim on 2009-11-10
> **jotto! said:**
> Have DL the Kompozer tar file...now to work out what to do with it.....google is my friend I think!

In most cases, you don't need to download software from a website. Look in the Software Center or Synaptic Package Manager.

If you do need to install something that isn't in the software center though, try to find a ".deb" file, which will install much easier than source code. The .deb files may be called "Ubuntu packages", "Debian packages", or something of that nature.

---

### Post by jotto! on 2009-11-10
so deb files are like an exe in windows? that would make life simpler! lol.

---

### Post by yknivag on 2009-11-10
> **chazn85 said:**
> a good free virtual machine is "virtualbox"  which can be found here [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

It's much easier to install it from the respositories.

Copy and paste this into a terminal to do so:
```
sudo apt-get install virtualbox-ose
```

That way you get automatic updates for it too.

---

### Post by Schendje on 2009-11-10
> **jotto! said:**
> so deb files are like an exe in windows? that would make life simpler! lol.
It's even easier. One button! :D

But Kompozer is also in the repo's, so paste the command above me or go to the Software Center to install it.

---

### Post by empty_spaces on 2009-11-10
> **yknivag said:**
> It's much easier to install it from the respositories.

Copy and paste this into a terminal to do so:
```
sudo apt-get install virtualbox-ose
```

That way you get automatic updates for it too.

Except that the repository version lacks some important features like usb support, etc
[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by andrew.46 on 2009-11-10
Hi jotto,

> **jotto! said:**
> Anyway, I read up on virtual machines and saw that I could use ubuntu as my host and have a virtual XP in which these programs would work.

I am a huge fan of VirtualBox and because I have no need of usb support in the guest machines I can claim the high moral ground of running the OSE version :). I attach a screenshot of VirtualBox in action with a Slackware 13 host and guests Karmic Koala and Windows XP.

All the best,

Andrew

---

### Post by roastedbeans on 2009-11-10
I just installed ubuntu on my macbook after being away from linux for some time. I must say that I'm impressed with it, especially coming from the mac world. It's a bit annoying when your normal windows or mac workflow doesn't jive like it did before, but don't look for ways to make ALL of your old software work. Try some of the free apps.

That's a long leap to make and one I'm having difficulty with at the moment, but I can happily say that the issue I had with my macbook before isn't present and hasn't been. I'm also having a lot of fun with some of the open source apps. 

Good luck with ubuntu and hello all on the forums!

---

