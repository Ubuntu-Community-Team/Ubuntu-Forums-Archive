---
title: "apt-get doesn't work, synaptic dissapeared"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by ubuntoras on 2010-05-27
hello out there,
i face a strange issue, i use ubuntu 9.10 karmic, during some try outs i remove with synaptic the apt package and now:
1. i can't use apt-get for nothing (nor aptitude or dkpg)
                               2. synaptic dissapeared from the applications
                               3. gnome doesn't appear like an opion on the login
                               4. i can't perform shut down
does any one know what to doooooooooooo!!!!!!

---

### Post by barney385 on 2010-05-27
Have you tried starting it from terminal?

---

### Post by slackthumbz on 2010-05-27
you've screwed your system. Re-install.

---

### Post by -humanaut- on 2010-05-27
Did you delete synaptic? You should open a terminal and try: 

sudo apt-get install whateverpackageyouwant

and post the results back could just be a broken package that can be fixed.

---

### Post by ubuntoras on 2010-05-27
i will try a bit more to fix it,
if nothing happents then i will install new ubuntu.
why not to be able to re-install apt?
if you have ideas i like to try them!

---

### Post by ubuntoras on 2010-05-27
> **-humanaut- said:**
> Did you delete synaptic? You should open a terminal and try: 

sudo apt-get install whateverpackageyouwant

and post the results back could just be a broken package that can be fixed.

apt-get: command not found

---

### Post by -humanaut- on 2010-05-27
Yikes, thats real bad. Here this might help [http://packages.ubuntu.com/search?keywords=synaptic&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=synaptic&searchon=names&suite=lucid&section=all) select your suite sorry I don't remember what version you where running and you can reinstall synaptic from there. I don't know if it will just 'work' but its worth a try.


Here [http://packages.ubuntu.com/karmic/synaptic](http://packages.ubuntu.com/karmic/synaptic) I just re-read your post thats going to be the download page for the version your looking for scroll to the bottom.

If that doesn't install automagically you might have to build dpkg from source heres a link [http://packages.ubuntu.com/karmic/dpkg](http://packages.ubuntu.com/karmic/dpkg)

---

### Post by ubuntoras on 2010-05-29
thanks a lot for your help, it works in learning level but with a new installation i manage to continue 
see you around.

---

### Post by bildr on 2010-05-29
yep, the solution would have been to reinstall apt-get from deb using dpkg

then reinstall synaptic with apt-get to handle depsolving problems.

or just use aptitude to reinstall apt-get.

---

