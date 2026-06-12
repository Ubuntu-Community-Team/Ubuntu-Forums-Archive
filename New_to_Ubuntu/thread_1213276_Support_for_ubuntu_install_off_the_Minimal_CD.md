---
title: "Support for ubuntu install off the Minimal CD"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by Buce on 2009-07-14
I'm having a seriously hard time finding help for a command-line-only installation of ubuntu. Seems like every other instruction says to go to some app or other under the Administration menu. Are there any wikis or other resources geared towards someone who installed off the Minimal CD?

---

### Post by LewRockwell on 2009-07-14
[http://ubuntuforums.org/showthread.php?t=155467](http://ubuntuforums.org/showthread.php?t=155467)

[http://xinocat.com/refcard/](http://xinocat.com/refcard/)

not sure it will help but we're trying...

.

---

### Post by lemuriaX on 2009-07-14
There is some useful info here:
[http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)

---

### Post by bodhi.zazen on 2009-07-14
[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by Buce on 2009-07-14
I appreciate the posts, guys, but I'm not exactly looking for an introduction to the command line, or a tutorial on how to install off the Minimal CD, or a cheatsheet of helpful commands, or instructions for how to restore a botched DE from the command line. Sorry my first post was so vague. What I want, if it exists, is a place geared towards people building a desktop environment (fluxbox, in my case) from a minimal install, where I can find info on how ubuntu works under the hood.

It seems like the biggest problem I'm encountering is that there's too much information on how to fix hardware problem X on a default install, where going to a GUI widget to configure things is easier than editing the config files from a text editor. But that's what I want -- I'm coming from Arch, where that's pretty much the standard. Not that I want the Ubuntu community to stop doing things how they are now just for me -- It's just that I wish there was an Ubuntu Minimal equivalent to [ArchWiki]("http://wiki.archlinux.org/index.php/Main_Page").

Hm. Maybe I should just stop including 'ubuntu' in my search terms and use 'debian' or 'linux' instead.

Anyway, here's a handful of problems I have that might help characterize the issue I'm having generally:

Gnome themes didn't work correctly (turns out I needed the clearlooks-engine package)
Sound didn't work (I think I needed a proprietary driver here, though I'm unclear as to which thing I tried did the trick)
Mic didn't work (needed an esd package, and had to configure something with a GUI app, which I didn't like)
Thunar autodetection with the thunar-volman package didn't work (Needed hal, which really surprised me -- thought it would've been included by default)
Don't know how to install 'urw chancery l' font (Problem still unresolved. Installing t1-cyrillic didn't do the trick, though the package description says it includes chancery fonts.)

And there were a few others that come to mind, but were do to user error (trying to startx from within a screen, f'rex. woops). The fixes are really simple, and usually involve installing a package, but since most people who need those packages already have them, the tutes and things that cover those issues aren't cluing me in to those packages. Maybe I should just be more aware of what problems are Ubuntu-specific, and which ones are just linux-specific, but if anyone has any other advice, I'd be very appreciative.

---

### Post by Buce on 2009-07-28
To help others who want to do with Ubuntu Minimal what I did, I catalogued my experiences at this thread: [http://ubuntuforums.org/showthread.php?t=1225523](http://ubuntuforums.org/showthread.php?t=1225523)

---

