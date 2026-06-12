---
title: "Eeeeek!  Where is my new firefox hiding?"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by anothernewuser on 2010-04-14
I just updated from 6.06 to 8.04 and have been fighting through the updates for hours ... of course 8.04 comes with firefox 2 as default ...

So I shopped around the forums to see how to update and found the idea to use:
gksu firefox and then use the built in update facility

which after a couple of updates got me to firefox 3.6  ... i was quite pleased that it ran and was able to get some add-ons in place.

However, at the moment the only way I can launch the 3.6 is through gksu .... the icon at the top of the screen launches 2.0 ... the applications menu launches 2.0 ...

I don't want to use gksu to launch it ... help! I noticed that i can alter the properties of the quick launch button by right-clicking it but i have no idea what to change to ... i went looking for the new file ... I haven't found it on my system yet.

Where do i find the new firefox an my system and how do i get it to launch from the options at the top of the screen?

Thank you in advance for any and all advice :)

---

### Post by philinux on 2010-04-14
If you are running a 32 bit install this is a good way to got.

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by anothernewuser on 2010-04-14
oki doki .. thx for your quick response sorry for my delayed reaction ... I'll poke around there and see what i learn :)

---

### Post by Paqman on 2010-04-14
> **anothernewuser said:**
> 
I don't want to use gksu to launch it ... help!

Good! Gksu will launch your whole browser as root, which is a huge security risk. Not recommended at all.

Have you tried launching it with:
```
firefox-3.6
```
If that works, you can change the launchers to reflect it. Or you could link the command "firefox" to the actual command.

---

### Post by anothernewuser on 2010-04-14
Again ... sorry for my delayed response this install is beating me half to death ;)  I gave up for a while

firefox -3.6 (Within terminal)does indeed launch the newest version

However, I don't seem able to get internet access reliably from 8.04 at the moment.  

In Windows there's a repair connection option which seems to help in such cases but can't find such a thing here yet ... that's neither here nor there.

Mysteriously, this time, when I started 8.04 the launch buttons seemed to launch 3.6 but I have no internet access so I've come back to windows to see what I can do and clearly I have access through windows as I'm making this post :confused:

Thx for your response though ... I'll keep at it.

---

