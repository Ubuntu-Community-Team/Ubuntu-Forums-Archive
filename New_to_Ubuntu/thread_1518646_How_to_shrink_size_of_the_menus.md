---
title: "How to shrink size of the menus"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by t1nm@n on 2010-06-26
you know the gnome menu well mine a bit big in size how can i decrease the size of it .

heres a screenshot

---

### Post by ubudog on 2010-06-26
Just right click on it, select Properties, and the setting should be in there.

---

### Post by t1nm@n on 2010-06-26
i dont understand...when i click the applications a dropdown menu appears ... i want to shrink that down it's kind of big. thanks for the reply

---

### Post by ubudog on 2010-06-26
Yes, sorry.  What theme are you using?  This would have an effect on it.

---

### Post by stinkeye on 2010-06-27
You can adjust the difference between each item in the menu using 
gnome-color-chooser.
Change the Y-Padding value.
```
sudo apt-get install gnome-color-chooser
```

---

### Post by t1nm@n on 2010-06-27
the theme is called Victory ..... this is the link
[http://gnome-look.org/content/show.php/Victory+%28Strikes+Again%29?content=123936](http://gnome-look.org/content/show.php/Victory+%28Strikes+Again%29?content=123936)

what does the color chooser do..any way will try that when i get home thanks

---

### Post by stinkeye on 2010-06-27
> **t1nm@n said:**
> the theme is called Victory ..... this is the link
[http://gnome-look.org/content/show.php/Victory+%28Strikes+Again%29?content=123936](http://gnome-look.org/content/show.php/Victory+%28Strikes+Again%29?content=123936)

what does the color chooser do..any way will try that when i get home thanks
It just appends a gtkrc file to your themes gtkrc and allows you to change
numerous colors and settings for your theme.
If you make a mistake or don't like the changes, just click the revert button.

The first pic is with the y padding set at 10.
The second pic is with the y padding set at 0.

The width of the menu is determined by the longest entry.
ie in the applications column, Ubuntu Software Center is the longest entry.
So if you right click on the menubar and select edit menus, click on Ubuntu Software Center > properties
and change the name to just "Software Center", the width will be reduced.

---

### Post by t1nm@n on 2010-06-27
thankyou stinkeye...

---

### Post by USERspooner on 2010-06-27
How about reducing the font size?

Reducing the font size also shrinks the menus... As the writing is smaller.

System (drop down menu) > Preferences > Appearance then Fonts tab in that box & Details in lower right hand corner & reduce Resolution (dots per inch)... I always have to reduce the font size like this or it all looks a bit Fisher Price to me.

---

### Post by calmsiva on 2010-06-28
forgive me for trying to clarify myself on this :  " do you want to compact the menu - like "applications" etc.

if so - try this :  Go to Systems -> Preference -> Main Menu

- in that you can "tick" the radio buttons - for several menus - and those applications which are there inside them.

- I generally 'untick' the Games, Other, Programming, etc.  - so that they are not always been shown in the  "Applications" menu - it is also sort of more compact.  

- You can also do more on each of the applications inside those menu.

Hope this is what you are looking for.:popcorn:

---

### Post by warfacegod on 2010-06-28
Another option is to disable "Show Icons In Menus". I'm not in my Lucid install at the moment so I'm not sure where that option is located. In 9.10 it's in Appearance Preferences> Interface tab but Lucid doesn't have that tab anymore.

---

