---
title: "get to cairo-dock and cairo-clock user folder"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by misswham on 2010-03-07
I have forgotten how to get to my folders where cairo dock and clock are located.  I remember putting a command in the terminal i believe that took me to some folders and i had to go to share and user i believe.  Can someone tell me how to get there?

---

### Post by fabounet on 2010-03-08
dunno what you want to do exactly but Cairo-Dock's user files are in ~/.config/cairo-dock

---

### Post by misswham on 2010-03-08
I want to add new themes to mac slow cairo clock and I cant find it.  I have gone to my home folder and hit ctrl h and i dont see cairo clock there.  i have gone to the config folder and see cairo dock but not cairo clock.  i tried to use the clock in the cairo dock but there is no theme there and when i add it to the dock, it is an empty space.  i have gone to the cairo dock folder in my home folder and places a lot of different clocks in the theme folder there but nothing still shows up.

---

### Post by fabounet on 2010-03-09
go in ~/.config/cairo-dock
there should be a folder named *extras*.
if not, just create it.
the inside you can add extras themes for any applets.
there is probably already a *Clock *folder, otherwise create it.
Inside this folder you can add several Cairo-Clock themes, they will be listed in the config panel of the Colck applet.

---

### Post by misswham on 2010-03-09
i have found the cairo clock folder.  I have put different themes in the clock folders and still when i click clock in the cairo-dock configuration in accessories and i am still getting 

the theme couldnt be found.    i have a lot of clock themes saved that worked before and now when i click clock an empty space shows up on the dock.

---

### Post by misswham on 2010-03-09
I actually found what I was looking for.  I wanted to know the command  gksu nautilus  i was trying to get to the folder that way.  i added themes to the cairo clock there and they show up in the list but when i click one that i have added, cairo clock closes.  What do u think it is?  I have used these exact same folders before and they worked.  and yes they are extracted

---

### Post by fabounet on 2010-03-10
which version of the dock are you using ?
the current stable is 2.1.3-6.
if it happens with it, you can run it in a terminal and post here the output :
cairo-dock -l debug
I personnaly don't have any problem with the themes integrated inside the dock.

---

### Post by misswham on 2010-03-10
this is the version i have.   

version 2.0.9-karmic1

how do i upgrade to the newest one?

---

### Post by fabounet on 2010-03-11
see the wiki on glx-dock.org, it's well explained.

---

### Post by afrodeity on 2010-04-29
Installed the latest version, but still can't figure out how to get the clock working. Keeps asking for a theme.

---

### Post by Claus7 on 2011-04-20
Hello,

Go to Places -> Home Folder
then
View -> Show Hidden Files

and then go to:
.config/cairo-dock/extras/clock

and place there the folder of the clock theme you have downloaded.

Then go to your desktop where the clock applet exists and right click on it.

Then go to:
Configure this applet-> Configuration-> click on the left hand side of analogue view-> and choose from the list of available display your new clock applet.

Those were for ubuntu maverick 10.10 and cairo-dock version 2.2.0-4.

Regards!

---

### Post by Chiapo on 2011-04-28
Since I don't have any cairo-dock, but I do have cairo-clock, I found the clock files in the following location:

```
/usr/share/cairo-clock
```

More info from MacSlow: [http://macslow.thepimp.net/?page_id=23](http://macslow.thepimp.net/?page_id=23)

Hope this helps save someone else some time.

---

