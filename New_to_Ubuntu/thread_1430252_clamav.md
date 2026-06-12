---
title: "clamav"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by Drenriza on 2010-03-15
Im running ubuntu 8.04 LTS hardy heron in an VMware-workstation 7enviroment. on-top of my main operativ system windows 7 ultimate. I have installed clamav with the apt-get install clamav command.

Is it possible that i can get my viritual enviroment to scan my windows 7 ultimate system?:KS

Thanks on advance
Kind regards

---

### Post by Frogs Hair on 2010-03-15
Hi,

On your scan check list you can select host , which is windows. Open your file manager,
 and select host to see if you have access to windows files. This works with wubi  
 installations but don't about virtual installations from a disc.

---

### Post by Drenriza on 2010-03-16
arnt clamav only possible to use through the command line?

Their are 0 icons for the program.

---

### Post by overlord.gaurav on 2010-03-16
Install ClamTK. Its the graphic front-end for ClamAV.
```

sudo apt-get install clamtk

```
or install it through Add/Remove Applications or through Synaptic Package Manager.

---

