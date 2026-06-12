---
title: "OTF font installation"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by jennyyin on 2009-12-06
Hello! Nearly total beginner writing here. 

I have a few .otf fonts I would like to install. I am running Ubuntu 8.10...
I've successfully installed .ttf fonts recently, but can't seem to figure out how to work with these different file types. Im mostly interested in using these fonts with GIMP and Inkscape. I did read online that OpenOffice cant handle the .otf files, and that's not problematic for me...

Can anyone link me to some very detailed and dumbed down instructions on how to do this? I have no real computer experience and am learning as I go. 

Much much appreciated,
jennifer

---

### Post by asmeetkumar on 2009-12-06
hi
this post should help you... 
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

to sum it up you need to press : ALT + F2
then type in : gksu nautilus /usr/share/fonts/truetype
hit enter, it'll prompt you for your password type it in 

copy your fonts into that directory 


then again press : ALT + F2
type in : gnome-terminal
hit enter and now run this command : sudo fc-cache -f -v
again give your password when prompted 

hth

---

### Post by kostkon on 2009-12-06
Or just copy them to the *.fonts* folder in your home.

---

### Post by jennyyin on 2009-12-06
hey thanks! that was way easier than i was trying to make it....i had read the post you recommended, but somehow, the way you summed it up made more sense.

doesnt mean i quite understand what exactly i just did, but now i can trace it back and try to learn. thanks!

---

### Post by hugmenot on 2009-12-06
Nowadays, there is absolutely no need to copy fonts into the system directories. 
Using the ».fonts« subdirectory in your home is fine (you might need to create it).
There is also no need to run any commands after putting them in there.
It&#8217;s all automatic.

---

### Post by jennyyin on 2009-12-07
After what seemed like instaneous success, 
I realised..not so.

I hope I can explain this well enough: 

I have a whole "family" of fonts Im looking to install. 
Called "fink", there are 8 variations...fink condensed, fink brush, etc. 

Looks like only one font actually was installed in Inkscape,
 and in Gimp, 8 fonts show up, all called fink, but they are all the same. 

When I followed your instructions, I copied them all at once....is there a better way to do this? thank you! 
jennifer

this post should help you... 
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

to sum it up you need to press : ALT + F2
then type in : gksu nautilus /usr/share/fonts/truetype
hit enter, it'll prompt you for your password type it in 

copy your fonts into that directory 


then again press : ALT + F2
type in : gnome-terminal
hit enter and now run this command : sudo fc-cache -f -v
again give your password when prompted 

hth[/quote]

---

### Post by hugmenot on 2009-12-07
To install this family it is enough to copy them into the hidden ».fonts« folder in your home directory.

the question then is where are you looking for the different fonts in that family. The normal font list will not display all these fonts, because it only displays families.

Open the Text and Font dialog in Inkscape to see if they are listed in the right-hand panel called »Style« (this is where styles like Bold and Italic are listed for simple font families).

---

### Post by jennyyin on 2009-12-07
hugmenot,
 thanks for the tips. 
 i did see the "text and font dialog thing", and that did indeed contain bold./italics, etc. 
the problem is, and i suppose i chose the wrong word of "family", i have a group of fonts, all purchased from here: [http://www.houseind.com/fonts/ratfinkfonts/viewfonts](http://www.houseind.com/fonts/ratfinkfonts/viewfonts)

all distinct fonts, but with "fink" in each name. so when i dragged them all the folder, 8 fonts show up, but all the same one (fink bold)...i did an experiment with one of the other fonts in the group, erased all the others and reinstalled, and it did work. so something is tricky with all of them being in the same folder. can i make a new folder in the hidden .fonts directory? 
its ok if none of this makes sense to you, im playing around with it. 
i do so appreciate your assistance!
thanks, jennifer

> **hugmenot said:**
> To install this family it is enough to copy them into the hidden ».fonts« folder in your home directory.

the question then is where are you looking for the different fonts in that family. The normal font list will not display all these fonts, because it only displays families.

Open the Text and Font dialog in Inkscape to see if they are listed in the right-hand panel called »Style« (this is where styles like Bold and Italic are listed for simple font families).

---

### Post by hugmenot on 2009-12-07
Yes, we can figure out what&#8217;s wrong. Just takes some more inspection.

Open Nautilus and toggle the display of hidden folders. Then make a subfolder in ».fonts«.

```
.fonts/fink
```

Put all your Fink fonts in there.

And then please open a Terminal window and type this command:
```
fc-list | grep -i fink
```

Please paste the output here. It should be a list of all fonts in your font catalogue that are usable by your apps (with "fink" in the name)

---

