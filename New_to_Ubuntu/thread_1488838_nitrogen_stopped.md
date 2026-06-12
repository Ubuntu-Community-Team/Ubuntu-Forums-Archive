---
title: "nitrogen stopped"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by dzon65 on 2010-05-20
Nitrogen stopped working.Uninstalling/reinstalling doesn't do anything.The settings towards the backgrounds is still the same.I can open it from a terminal with the following error:(nitrogen:2044): Gtk-WARNING **: Theme directory  of theme John's has no size field,and there are no backgrounds displayed.

---

### Post by kerry_s on 2010-05-21
> **dzon65 said:**
> Nitrogen stopped working.Uninstalling/reinstalling doesn't do anything.The settings towards the backgrounds is still the same.I can open it from a terminal with the following error:(nitrogen:2044): Gtk-WARNING **: Theme directory  of theme John's has no size field,and there are no backgrounds displayed.

nitrogen keeps settings in your, open your browser, press ctrl+h
you should see ".nitrogen" just delete it.
then launch "nitrogen", click preferences-> add & select your folder with backgrounds.
then just select your background & apply.

---

### Post by dzon65 on 2010-05-21
Did a total reinstall.Now I can't open synaptic,same error:(synaptic:5318): Gtk-WARNING **: Theme directory  of theme John's has no size field

john@john:~$ sudo apt-get purge synaptic
sudo: /etc/sudoers is mode 0640, should be 0440
Segmentatiefout
 (segmentation error).Wtf is going on here?

---

### Post by kerry_s on 2010-05-21
> **dzon65 said:**
> Did a total reinstall.Now I can't open synaptic,same error:(synaptic:5318): Gtk-WARNING **: Theme directory  of theme John's has no size field

john@john:~$ sudo apt-get purge synaptic
sudo: /etc/sudoers is mode 0640, should be 0440
Segmentatiefout
 (segmentation error).Wtf is going on here?

are you using a old home folder on your new installs?

did you make sudoers writable?
it should only be edited using "sudo visudo".

run a memory test just in case.

---

### Post by warfacegod on 2010-05-21
Did you *purge* Nitrogen or simply Remove and Install again?

---

### Post by dzon65 on 2010-05-21
It's not even possible to purge.The terminal stops there.Nothing happens.I can't open synaptics,only via terminal and without the possibility to do any changes.

---

### Post by warfacegod on 2010-05-21
Login as root, instead of your user account.

---

