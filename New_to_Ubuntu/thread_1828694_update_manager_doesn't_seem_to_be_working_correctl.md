---
title: "update manager doesn't seem to be working correctly"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by boregard on 2011-08-19
hello, i' am new to ubuntu - been using it about a month. i am using natty 11.04 and love it so far. but the update manager comes up in launcher so i click to install updates and enter password. it will sit there and cycle for a very long time and message will pop up telling me updates were installed 1 hour ago. if updates were installed 1 hour ago why is update manager asking me to install updates? very annoying, makes me wonder if updates were even installed correctly. thanks for any help or advice, boregard.

---

### Post by jerrrys on 2011-08-19
open a terminal and enter:

sudo apt-get update && sudo apt-get upgrade

this may fix that.  if you get any errors, please post them

---

### Post by jfed on 2011-08-19
I have had a similar issue on a laptop of mine, I'd like to see how this turns out.

---

### Post by boregard on 2011-08-19
i copied & pasted the command in terminal. i don't if that worked or not. i don't know how to read the results but i noticed it said something about  ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted translation-en us thanks for you helping me out.

---

### Post by boregard on 2011-08-23
running that command in terminal seems to have fixed update problem. much thanks for the help.

---

