---
title: "Me menu colour problem - black on black on black???"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-02-13
Theres some problem with my me menu, i know between that and gwibber theyve had loads of criticism but i finally seem the have facebook working on gwibber and i can update my status through the me menu but the colour scheme for is is black text on a black background in a black window?? Its readable but not easily especially if im sitting back from the screen slightly. Also the default text will stay there once i try and type and i have to manually delete it first. 
Anyone else having this bug??

---

### Post by linuxsyst on 2011-02-13
That's ok in ubuntu 10.10
everybody has it like this but if you want you can change it
System -> Preferences -> Theme -> Customize

Controls is the part you want to change.

---

### Post by linuxsyst on 2011-02-13
Also I forgot:
there are a bunch of themes in the repositories. Search synaptic for gtk2-engines and gnome-themes

---

### Post by linuxsyst on 2011-02-13
Oh sorry for that it was in old version of ubuntu
That's a bit difficult in the new version, you have to modify > /usr/share/themes/Ambiance/gtk-2.0/gtkrc file. It's not as difficult as it seems to be, the syntax is very intuitive. I don't know how is the dropmenu called in this progamming language, but it must be something with «menu», I think. The only thing you have to know is RGB code of colors.

I had a look at the file and it seems to be the > style "menu" = "dark" { part in gtkrc.

Remember to make a backup.
Cheers

---

