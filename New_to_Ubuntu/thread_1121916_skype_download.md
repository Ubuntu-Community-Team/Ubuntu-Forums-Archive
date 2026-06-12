---
title: "skype download"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by shoneils on 2009-04-10
I'm actually new using ubuntu. I followed the instructions on installing Skype but when it almost completes download then it prompts and says: /tmp/skype-debian_2.0.0.72-1_i386-3.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

Please, how do i go about that?

Thanks guys

---

### Post by taurus on 2009-04-10
Try installing it from a terminal.

Applications -> Accessories -> Terminal
```
sudo dpkg -i /tmp/skype-debian_2.0.0.72-1_i386-3.deb
```
Otherwise, add Medibuntu and install it from there.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by El1iP3S01D on 2009-04-12
Folks, what does this mean?

skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory

---

### Post by Armor Nick on 2009-04-12
I could be wrong, but try installing qt4. Are you using regular Ubuntu or K/Xubuntu?
Seems strange, though, as a deb should resolve dependencies automatically.

---

### Post by waspbr on 2009-04-12
try the command 

```
sudo apt-get install libqt4*
```

---

### Post by Paqman on 2009-04-12
There is an Ubuntu repo that has Skype in it. It's called [Medibuntu]("http://www.medibuntu.org/").

Using a repo has a couple of big advantages over using a .deb file.

[LIST=1]
[*]You caninstall it through Synaptic or Add/Remove just like normal software
[*]It'll automatically update you whenever new versions are released. That's really important for security.
[/LIST]

Medibuntu has a lot of other good stuff in it, too. I'd highly recommend it.

---

