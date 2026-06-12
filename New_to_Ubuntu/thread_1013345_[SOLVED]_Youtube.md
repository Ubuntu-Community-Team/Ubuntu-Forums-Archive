---
title: "[SOLVED] Youtube"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by icyest on 2008-12-16
So I recently captured a few clips on  my camera phone and I'd like to cut some pieces out and fuse them together for a simple video to be uploaded on youtube. The videos end in 3pg.

I have kdenlive. I was advised that nothing else in Linux works.

I just want to put "this video" and "this video" together. I have no idea what multiple time-lines are and have no understanding of digital video science. Obviously the output's dimensions should be the same as the input. There is no reason why the finished product should be different than the original pieces, and obviously I don't want a decrease in quality. Can you explain what I should do in a non complicated way?

I searched all over and could not find any assistance whatsoever.

---

### Post by jpoRS on 2008-12-16
Hey Icy,

You could also try Kino, since kdenlive is a kde program it may not be fully functional in gnome.  There is a very good chance I am wrong about that though.

Other than that I really have negligible experience in video editing, but the best advice I can give is jump in.  Based on your signature I am guessing you are a courageous type, so I don't think that will scare you too much.

Make sure you backup what you are working with though.  That way when you inevitably make a mistake, you haven't ruined everything.

Anyway good luck!
jim

---

### Post by HotShotDJ on 2008-12-16
I have found [Cinelerra]("http://cinelerra.org") to be the very best video editing software for Linux.  It is somewhat difficult to learn and the user interface isn't pretty, but once you get the hang of it, the end result is very good.  The other editors that I've tried (Kino, KDEnlive), while having a pretty user interface, produce pretty shabby results.

You can get instructions for installing it in Ubuntu here: [http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

Undoubtedly, you will also need to study the online documentation here:
[http://cinelerra.org/docs.php](http://cinelerra.org/docs.php)

---

### Post by icyest on 2008-12-16
> **HotShotDJ said:**
> I have found [Cinelerra]("http://cinelerra.org") to be the very best video editing software for Linux.  It is somewhat difficult to learn and the user interface isn't pretty, but once you get the hang of it, the end result is very good.  The other editors that I've tried (Kino, KDEnlive), while having a pretty user interface, produce pretty shabby results.

You can get instructions for installing it in Ubuntu here: [http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

Undoubtedly, you will also need to study the online documentation here:
[http://cinelerra.org/docs.php](http://cinelerra.org/docs.php)

How did you even get yours installed?
I used 
```
wget -c http://akirad.cinelerra.org/pool/addakirad.deb && sudo dpkg -i addakirad.deb
```
like the website states. Where is my program? it's just not there.

---

### Post by HotShotDJ on 2008-12-16
> **icyest said:**
> How did you even get yours installed?
I used 
```
wget -c http://akirad.cinelerra.org/pool/addakirad.deb && sudo dpkg -i addakirad.deb
```
like the website states. Where is my program? it's just not there.You haven't installed the package yet, you've only added the repositories.  The next step is to open System --> Administration --> Synaptic Package Manager, and then choose the Cinelerra package that is best for your system.  If you don't know which one to choose, then you should install the generic Cinelerra package.  Be sure to set up the compatibility with Pulse Audio after you've installed the package or you will run into problems.  CAREFULLY read the instructions provided.  This is a third-party package and is still being very heavily developed.

---

### Post by icyest on 2008-12-16
Okay, I think I'm getting close to warping my head around the concept of repositories. Since they are just like hyperlinks for your computer to go to when calling upon an application you need installed, why doesn't the Ubuntu company just install ALL of the know repositories in the linux community? It's perfectly harmless, and it would seem like the most logical thing to do. From that point on, you can just use the "add/remove..." thingy.

---

### Post by HotShotDJ on 2008-12-16
> **icyest said:**
> why doesn't the Ubuntu company just install ALL of the know repositories in the linux community?There are sometimes licensing issues, not to mention the fact that these third-party repositories are often for development software or for software that has not yet been fully vetted and accepted by Ubuntu developers.  Sometimes, repositories are incompatible with each other.  Finally, the Ubuntu developer community cannot accept responsibility for software that is not part of the official repositories -- by simply installing all of the literally hundreds of third-party repositories on all systems, they would be accepting responsibility for the contents of them.

---

### Post by handydan918 on 2008-12-16
> **icyest said:**
> Okay, I think I'm getting close to warping my head around the concept of repositories. Since they are just like hyperlinks for your computer to go to when calling upon an application you need installed, why doesn't the Ubuntu company just install ALL of the know repositories in the linux community? It's perfectly harmless, and it would seem like the most logical thing to do. From that point on, you can just use the "add/remove..." thingy.

ALL the known repos would warp your system beyond repair. There are so many different flavors of DEBIAN based Linux, it would take pages to list the repos. And eternity to resolve the conflicts.
The Ubu repos use Debian package management, but they are not truly "Debian" in the sense that they can use all Debian packages. Ubu is a "fork" of 
Debian, and as such, must maintain it's own packages, kernel, etc.

---

