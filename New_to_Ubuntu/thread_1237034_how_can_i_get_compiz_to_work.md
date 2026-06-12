---
title: "how can i get compiz to work?"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Rsmoker on 2009-08-10
hey guys i just switched from vista to jaunty jackalope and so far its awesome but ive encountered some problems first of all is how can i get compiz to work?? i own a laptop and i think that my video card sucks *** but i dont know wich one i have how can i check that? and my other problem is that i cant get utorrent to work it says the application is already in use and that i need to terminate it can somebody help me??

---

### Post by hockeyfighter09 on 2009-08-10
> **Rsmoker said:**
> hey guys i just switched from vista to jaunty jackalope and so far its awesome but ive encountered some problems first of all is how can i get compiz to work?? i own a laptop and i think that my video card sucks *** but i dont know wich one i have how can i check that? and my other problem is that i cant get utorrent to work it says the application is already in use and that i need to terminate it can somebody help me??

Have you tried to turn on compiz but doing going to System>Preferences>Appearance>Desktop Effects to see if it works?

---

### Post by stumbleUpon on 2009-08-11
Look here

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

This script will tell you whether or not compiz can run on your machine. First test that and then enable compiz as hockeyfighter09 has mentioned above.

---

### Post by Rsmoker on 2009-08-11
thanks im gonna test it to see ill let you guys know also i read a thread that said that intel video cards have problems with jaunty maybe that could be the problem right?

---

### Post by hockeyfighter09 on 2009-08-11
> **Rsmoker said:**
> thanks im gonna test it to see ill let you guys know also i read a thread that said that intel video cards have problems with jaunty maybe that could be the problem right?

I heard it effects mainly just the 965 model of the intel graphics cards, I have a 945 intel card in my laptop and jaunty worked great.

---

### Post by nhasian on 2009-08-11
to enable compiz to work with your intel video adaptor try copy/pasting this line to the terminal.  reboot and then you should be able to enable desktop effects in system->preferences->appearance 

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

---

### Post by Schendje on 2009-08-11
This is a different subject, but if uTorrent isn't working properly in Wine, you can always try out Deluge which is a torrent application that works very similar to uTorrent.

Install it at Applications -> Add/Remove -> Deluge

Also, if you're not sure what graphics card you have, open Applications -> Accessories -> Terminal, type "lspci" and look for "VGA compatible controller".

---

### Post by Rsmoker on 2009-08-11
Ok so i have an Intel 965 and after spending a looot of hours last night reading in forums and stuff i managed to find the problem and the problem is that my particular video card has a lot of problems with the new jaunty but luckily for me i was able to find a solution but i cant download it since im a completely noob at this ill leave the link to the website to see if somebody can tell me how to download the drivers for my card your help will be very much appreciated i really dont want to give up on ubuntu.....

[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

---

