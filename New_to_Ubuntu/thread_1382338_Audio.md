---
title: "Audio"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by ncc1701e on 2010-01-15
I need to install realtek audio drivers on my system but they are only available in source form i.e. not in synaptic or any other repository. I am new to the concept on installing from souce I know the gist of commands like ./configure, make, make install...but since these are drivers and not just application software do I need to do anything special/additional?

thanks

---

### Post by sandyd on 2010-01-15
nope. other than running depmod and modprobe after the installation of the drivers, there should be no other stuff needed

---

### Post by ncc1701e on 2010-01-15
Thank you for the good advice. unfortunately Im such a newbie that your answer to my question has generated another question from me and that is that after installing the drivers you talk of depmod and modprobe. I know that they are commands that probe for hardware but can you please tell me what order I run the commands and the syntax?

for example would it be something like

depmod <nameof my soundcard)
modprobe <name of my soundcard)
?

thanks

---

