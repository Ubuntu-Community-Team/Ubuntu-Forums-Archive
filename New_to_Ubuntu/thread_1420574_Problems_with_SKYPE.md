---
title: "Problems with SKYPE"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by awilliams11964 on 2010-03-03
:oWhen I installed Skype 32 bit on 9.10, I lost my internal microphone. Video and speakers are fine. Any thougths?

---

### Post by Arijit_Kundu on 2010-03-03
install alsamixer. that is run in a terminal
sudo apt-get install alsamixergui

then run in a terminal

alsamixer

browse through by left key and Tab and make all volues related to mic/internal mic/front mic to 100 

this will probably fix the problem

---

### Post by Arijit_Kundu on 2010-03-03
oh, press Esc to get out from alsamixer in the terminal

---

