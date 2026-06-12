---
title: "ubuntu 2.30.2"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by jjb945025 on 2010-11-04
hello. can anyone help me out with this... when i try to open synaptic i get this message:failed to run as user root and something about an Xauthorization file. can anyone help me out here, i need to uninstall some apps. thanks.

---

### Post by oldos2er on 2010-11-04
In a terminal, run **sudo apt-get remove <package name>** , where <package name> is an app you want to uninstall. If there are errors, please copy and paste the entire output here.

---

### Post by rmockler on 2010-11-04
If you're having difficulty starting synaptic without root authority, try the follow command in terminal:

Code:

gksu /usr/sbin/synaptic

If this works, then we can figure out what is wrong with your menu command.

---

### Post by jjb945025 on 2010-11-06
ok rmockler, it opened synaptic.can you tell me what  to do ,like i was  looking for the apps i want to uninstall but... they're not there.. ha! i  dunno man, i'm tryin to uninstall itunes and i've only seen isync and  ipod in the lists. guess ya cant help me anymore but i do appreciate  what information you've provided.. thanks.

---

