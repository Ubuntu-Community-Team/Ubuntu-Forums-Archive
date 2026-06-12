---
title: "Firefox troubles"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by padalar on 2009-04-02
hi all

Im super new to this so apologies if I'm rehashing a much covered subject!

Firefox on my computer has given up on life! It still works, but some very basic, but much used functions no longer work. I cant select 'back', 'forwards', 'refresh' 'stop', I can go to any page if I have the address, but if I navigate further the address bar doesn't change. The bookmarks I had saved along the top have all disappeared. On some sites, such as the BBC, it gives up and freezes.

its all really rather annoying, any help would be appreciated.

I'm running ubuntu 8.1 and the latest firefox 3.0

cheers

---

### Post by luckydeveloper on 2009-04-02
try reinstalling firefox.. Go to system->administration->Synaptic package manager and search for firefox. then click it to do reinstall...

---

### Post by WinterMadness on 2009-04-02
try to reinstallit via synaptic.

also, are you using Wubi? I had a similar problem like what you said when i used it. If you are, i suggest a true install

---

### Post by ajgreeny on 2009-04-02
If none of those help, try renaming the hidden ~/.mozilla folder in your home folder (Ctrl+H to see hidden files/folders) as .mozillaold and restart firefox.  If that works, copy over the biikmarks from old to new .mozilla folder but I would leave the rest behind as it will be something from the configuration that caused the problem.  Your bookmarks are now in the file called places.sqlite, not bookmarks.html.

---

