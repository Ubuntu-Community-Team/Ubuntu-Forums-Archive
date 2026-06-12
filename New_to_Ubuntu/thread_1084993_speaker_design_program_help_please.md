---
title: "speaker design program help please"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by psychosteve72 on 2009-03-02
So i finaly did it made the jump and got ubuntu loaded (hardy lts.) on a new machine. and it works, and im on the internet, and i got eagle pcb design software downloaded and instaled. 

hurrah, it all works. now i just need speaker design software, looked at GnomeSpeakers down loaded from sourceforge.net 

downloaded it

then read that it needs gnucap, spice3f5, and gtkmm, ok so download them.

then i get lost, how do i get them installed, one of the instuctions is a compile, how do i do that? 
how do i "you should be able to safely do  ./util/build linux
  and then      ./util/build linux install" to get spice3f5 insalled?  because i assumed it was a terminal instuction code but something wasnt right as it came back with a no such instruction error!

i know this is a bit involved, and maybe not quite right for "absolute beginner" and i could realy do with a one file, one install program, so any sujestions greatfully accepted, failing that, i could realy do with  key by key instructions.

thanks for reading, hope someone can help. steve.

---

### Post by achase79 on 2009-03-02
gnucap, gtkmm & gtkmm-dev are needed you can get them through synaptic.

---

### Post by psychosteve72 on 2009-03-02
thanks, found gnucap in synaptic pac man, got and installed fine, cant see gtkmm (even tried updating the list) in the list, or am i being to specific? gtkmm-2.14.0 is, i think, the one i need, although 2.00 will do i think. any other suggestions? again, thanks, steve.

---

### Post by psychosteve72 on 2009-03-03
ok found gtkmm and gtkmm-dev got them installed. now all i need to do is compile, make and install gspeaker, how is that done?.

thanks for the help so far, steve.

---

### Post by victorhugo289 on 2010-07-12
Guys help me out here, I downloaded "Spice3f5.tar.giz" file but I don't know how to install it or compile it --the latter which is something new to me, I need to use Spice, I tried following the instructions given here: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo), but I stopped at Step 3 where it says I should look for a file name "./configure" which does not exists, what do I do? 

Any help appreciated

---

### Post by Orvar on 2011-04-09
Another solution, that I have used for years:

Install Wine from the repositories.

Then find and install WinISD -- a windows program that works perfectly under Wine.
(You have to right click on the install file, then choose "open with" and choose Wine. Or, even better: choose properties and change the default opening program to Wine. Then a double-click on a .exe file will automatically use wine for installation.)
If you dare, you can follow the instructions on winehq.org to install the beta version, it has even better compatibility to modern windows software.

Using Wine, you can also install some other good windows software like Irfanview (adding mfc42.dll to the win32 directory) and PhotoFiltre and others.

---

