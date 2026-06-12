---
title: "permission problems with sudo"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by Caramin on 2010-02-20
Hello!

I played some supertux2 - there are sound problems. That is no problem, because i play it without sound. But i'd like to disalbe the game-intern console, which disturbes a little during playing. I found:
[http://ubuntu-install.blogspot.com/2009/11/supertux2-cheats.html](http://ubuntu-install.blogspot.com/2009/11/supertux2-cheats.html)

I tried that, but I don't have the permission to change console.nut .So I read a little about permissions in ubuntu, opened a termial and typed sudo - than the tree -( where the data is), and tried to change it again - but that didn't help. what was i doing wrong? Its ubuntu karmic with studio upgrade.

THX

---

### Post by Muscovy on 2010-02-20
You shouldn't need to use sudo. The webpage says the config stuff is in "~/.supertux2/config", which is /home/YOUR_NAME/.supertux2/config , which you should own.

---

### Post by Caramin on 2010-02-20
in my case its /usr/share/games/supertux2/scripts/console.nut

didn't find it anywhere else.

is that wrong?

---

### Post by Caramin on 2010-02-20
Or maybe is there a way to give over all permission for a short time? Switch in - change - switch off?

---

### Post by RedSingularity on 2010-02-20
You can start nautilus as root and change what you need to.

In terminal 

sudo nautilus

---

### Post by Caramin on 2010-02-20
Perfect - i could change it with that. Two last question

1. Nautilus opens an "explorer" with allover permission, right? then =>

2. Is it a kind of process that I have to stop, or does it stop by closing the window?

THX

---

### Post by RedSingularity on 2010-02-20
Yes that command opens nautilus with admin privileges and to exit you just need to close the terminal window.

---

### Post by Caramin on 2010-02-20
That is a great hint! Thank you!!!!!!:D

---

