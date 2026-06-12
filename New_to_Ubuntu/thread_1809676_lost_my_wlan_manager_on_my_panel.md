---
title: "lost my wlan manager on my panel"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by eddski on 2011-07-21
i dont know how it happened, but I had my laptop off for awhile and all of a sudden my wlan manager/monitor icon is missing from my panel. Can someone tell my why it left and /or how to get it back?
thanks in advance, you guys are the best

---

### Post by Paddy Landau on 2011-07-22
If you made no changes, it's possible it just crashed. Restart your computer. Let us know if that works.

---

### Post by eddski on 2011-07-29
sorry for late reply(working 2 many hrs), but no that didnt work and i have no wireless, i even tried ifconfig wlan0 up and nothing. Ifconfig just mac addr and nothing else

---

### Post by sadaruwan12 on 2011-07-29
Did you try adding a new notification area that might solve your problem.

---

### Post by eddski on 2011-08-03
how do add a NEW notification area, did you mean "add to panel"? If so, i tried that and nothing was in there to add for wireless.

---

### Post by gandaran on 2011-08-03
> **eddski said:**
> how do add a NEW notification area, did you mean "add to panel"? If so, i tried that and nothing was in there to add for wireless.
just do add to panel » "notification area" and you'll get the network icon back.

---

### Post by eddski on 2011-08-06
to gandaran, all that did was add a separator. I still have no wireless, i think it might have gotten stomped on when i upgraded to 32-32 kernel, thats the only thing i can think of that changed.

---

### Post by Basher101 on 2011-08-07
try running```
nm-applet
``` in the terminal

---

### Post by amjjawad on 2011-08-07
If this is Lubuntu then:

1- Point your mouse pointer next to the timer

2- Right Click

3- Add/Remove Panel items

4- Check attached:

5- Done ;)

---

### Post by eddski on 2011-08-26
ok, nm-applet didnt work, kinda gettin frustrated. i dont think my wireless card is recognized. how can i check if its there, i cant find reference to it, can i just reinstall(intel 3945abg card)? would it be better to upgrade to natty from a disk?

---

### Post by amjjawad on 2011-08-27
> **eddski said:**
> ok, nm-applet didnt work, kinda gettin frustrated. i dont think my wireless card is recognized. how can i check if its there, i cant find reference to it, can i just reinstall(intel 3945abg card)? would it be better to upgrade to natty from a disk?

Have you checked my previous post?
Are you using Lubuntu or another variant of Ubuntu?

Please, post the output of:

```
sudo lshw -C network

```

When posting the output, please wrap up the text with "CODE" tags or "#".

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]

---

### Post by fractalman on 2011-08-28
I have been having the same problem on my pc,  the network icon just disappeared and everything solution from google turn out to be no good, anyway i just tried entering 'nm-applet' in the terminal and it says i need the 'network manager - gnome' package,  i have just installed ' network manager-gnome' and hey presto my applet is back where it should be.  turns out when i removed all the bluetooth packages from my system it took the network manager with it

anyway, i don't know if this will work for you but it worked for me.

---

### Post by eddski on 2011-08-30
to fractalman YOU ARE THE MAN, i did exactly what you posted and presto! im back in business! i uninstalled bluetooth thinking i didnt need it. i then reinstalled bluetooth and network man gnome and its back, thank you very much fractalman!

---

### Post by eddski on 2011-08-30
solved!  i uninstalled bluetooth thinking i didnt need it. i then reinstalled bluetooth and network man gnome and its back, thank you very much fractalman!
__________________

---

### Post by amjjawad on 2011-08-30
Congratulation :)

Please, I'd like to know what variant of Ubuntu are you using? Lubuntu? or Ubuntu?


IF solved then ...

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

### Post by eddski on 2011-08-31
im using ubuntu 10.04 and thanks for the info on how to mark the post as "solved"

---

