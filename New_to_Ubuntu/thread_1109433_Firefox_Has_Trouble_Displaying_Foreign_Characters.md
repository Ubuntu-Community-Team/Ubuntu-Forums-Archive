---
title: "Firefox Has Trouble Displaying Foreign Characters"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2009-03-28
I have noticed in most of the websites I have gone to, Firefox is able to display all of them. But in some, it cannot and displays clear boxes with numbers in them and black diamonds with clear question marks in them, instead.

Here are some examples.
[http://music.ibiblio.org/pub/multimedia/chinese-music/html/traditional.html]("http://music.ibiblio.org/pub/multimedia/chinese-music/html/traditional.html")

and
[http://en.wikipedia.org/wiki/He_(letter)]("http://en.wikipedia.org/wiki/He_(letter)")

It seems to be related to language packs. I know how to install them in Windows XP, but in Ubuntu, I do not know how to do this.
Could someoe teach me how to, please?

Thank you for your time.

Take care,
RedStarYellowSun

---

### Post by ethoxyethaan on 2009-03-28
sudo apt-get install ttf-arphic-ukai ttf-sil-yi xfonts-intl-chinese xfonts-intl-chinese-big

try to install those packages.

i use iceweasel and the characters display.

---

### Post by fly-by-night on 2009-03-28
I didn't install anything.

In Firefox under **View/Character Encoding** you need to choose the appropriate encoding option.  For the first link you provided, I chose **Simplified Chinese** and it displayed the characters.

---

### Post by RedStarYellowSun on 2009-03-29
Thanks, my friends!
It works!

Take care,
RedStarYellowSun

---

