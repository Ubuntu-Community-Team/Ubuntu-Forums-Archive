---
title: "Itunes? Ipod etc, on Ubuntu possible?"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by Ertwong on 2011-03-05
does itunes run on Ubuntu? and if it doest is there a way to sync my ipod with the music?

---

### Post by sdlynx on 2011-03-05
You can use Rythmbox or gtkpod to do this.  I'm not sure if it works with an iTouch/iPhone though.

---

### Post by jbiggs12 on 2011-03-05
iPods work fairly well with Gtkpod, note that they can be rather finicky with Rhythmbox and you won't get the features that you would get if you used iTunes (Genius, Genius Mixes, etc.) Another minor annoyance that I have to deal with on my Gtkpod synced iPod is that it groups all of the "The's" together (e.g., The Shins, The Cars, etc.) and doesn't sort them by their "actual" name.

Setting up sync with the iPod Touch / iPhone can be somewhat difficult, I managed to sync my iPhone 2G with iFuse, which is easily installable through APT (sudo apt-get install ifuse in terminal.) Google around about setting up the device... I can't find the link that got me to figure it out at the moment but you'll have to generate the HashInfo file and move it into the directory of the iDevice after you've mounted it.

Sounds complicated, I know... it kind of is. Apple is as proprietary as you get and they enjoy letting us open-source users know :)

---

