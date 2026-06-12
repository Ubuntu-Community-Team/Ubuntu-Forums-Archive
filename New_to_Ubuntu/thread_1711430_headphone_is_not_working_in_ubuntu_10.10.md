---
title: "headphone is not working in ubuntu 10.10"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by pratibhaz on 2011-03-21
Hello..
 i have lenovo laptop in which inbuilt sound speakers are working but when i plug in the headphone then no sound from headphone ....
After plugin the headphones inbuilt speakers work but not headphones
 plz tell me, how to hear through headphones...

---

### Post by Arijit_Kundu on 2011-03-21
install alsamixer (sudo apt-get install alsamixer). Then run alsamixer in a terminal. set all volumes to high. Press tab to move through the pages. Then press esc for return. This may help.

---

### Post by pratibhaz on 2011-03-21
still not working

---

### Post by Arijit_Kundu on 2011-03-21
Can you try to change through the sound hardware options in the volume manager? Is this showing your headphone when it is plugged in?

---

### Post by Arijit_Kundu on 2011-03-21
if it still does not work, you can try to install new drivers by installing 
linux-backports-modules-alsa-karmic-generic from synaptic.

---

