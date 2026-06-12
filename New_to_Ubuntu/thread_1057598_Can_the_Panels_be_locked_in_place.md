---
title: "Can the Panels be locked in place?"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by k3lt01 on 2009-02-02
**_*SOLVED*_**

Can the Panels in Gnome be locked in place? if they can, how?

My father is new to Ubuntu and he keeps moving the panels around without even knowing he is doing it (I have watched him closely and it is him doing it, even though he denies it, lol).

---

### Post by Crafty Kisses on 2009-02-02
I'm pretty sure you can right click on the panel, and there's an option called "Lock Panel Position". Try that and see if it works.

---

### Post by k3lt01 on 2009-02-02
Nope there is no "Lock Panel Position" option. See screenshot for proof.

---

### Post by gettinoriginal on 2009-02-02
Install Ubuntu Tweak, it is in Synaptic.  After it is installed, it will be under Applications, System Tools.  Once open, go to desktop, gnome, check complete lockdown of panels.   :p

---

### Post by k3lt01 on 2009-02-02
Thanks gettinoriginal, I tested it on my laptop and it worked, now to fix my dads laptop.

---

### Post by marianlibrarian on 2009-05-04
I need help. I thought this would be the answer. I have 5 public access computers and our patrons have so totally screwed the desktop that I have had to resort to reinstalling Ubuntu (the one with the Crane oops edit: Hardy Heron).

So I have been searching through this forum and found this suggestion of using "Tweak"

But this is what is in the Synaptic description:
> an efficient hex editor
Tweak is a hex editor. It allows you to edit a file at very low
level, letting you see the full and exact binary contents of the
file. It can be useful for modifying binary files such as
executables, editing disk or CD images, debugging programs that
generate binary file formats incorrectly, and many other things.

Tweak runs under any terminal emulator using the curses library.  It
has customizable keybindings, but the default keybindings are similar
to emacs.Where is this Tweak in Synaptic that is supposed to "lockdown" panels and such???

---

### Post by starcannon on 2009-05-04
marianlibrarian you can find it here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by riza hylviu on 2009-05-04
HI 
Just search on google for ubuntu tweak and download the deb package, i didn't find it in synaptic

---

### Post by marianlibrarian on 2009-05-04
I went to Ubuntu Tweak link provided above. I think that may be more than this poor old librarian can comprehend.

However, I kept searching through the search results and found reference to something called Pessulus that you can find by going to your Synaptic thing and typing in the word Lockdown. 

Once it is installed, there will be a selection in the System / Administration menu called "Lockdown Editor". This is simple enough for me to understand and will tide me over until I can figure out the Tweak thing.

Thanks!

---

### Post by marianlibrarian on 2009-05-04
Well, it does lock down the panels so they cannot be moved. However, the menu choice is available to all users even some one with no privileges. So I am going to have to figure out what tweak is and hope I don't blow up our computers in the process.

---

### Post by PGScooter on 2009-05-12
marianlibrarian,

Did you figure it out?

---

### Post by Big Luke on 2009-05-12
Well i am just going to infer that you are referring to the panels that are by default one on top and one on bottom. ):P  I also assume that you are having trouble with the panels moving around.  This was a big problem for many in previous distros as seen [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/83286") however with the new release of [Jaunty]("http://www.ubuntu.com/getubuntu/download"), this was fixed.  So if you are indeed having a problem with the panels moving around on you, I would strongly suggest upgrading to jaunty.  I can personally assure you that you _**will not**_ be disappointed.  

Good Luck :D

---

### Post by kaibob on 2009-05-13
The Configuration Editor has an option that prevents panels from being moved or altered (see the screenshot below). The applicable key is:

```
/apps/panel/global/locked_down
```

For more information on this, see the thread at:

[http://ubuntuforums.org/showthread.php?t=1147961](http://ubuntuforums.org/showthread.php?t=1147961)

---

### Post by k3lt01 on 2009-05-13
MarianLibrarian started her own thread a week ago and even though I don't know how she has gone with her issues I'm sure the answer you seek will be in her thread. As for me its all fixed and I beg to differ with Big Luke, my father was able to inadvertently move his panels in Jaunty.

---

