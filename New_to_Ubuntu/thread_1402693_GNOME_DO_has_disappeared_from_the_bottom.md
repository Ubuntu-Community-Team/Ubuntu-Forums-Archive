---
title: "GNOME DO has disappeared from the bottom?"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by verachion on 2010-02-09
I have been using GNOME DO as a dock, but since I restarted the PC It has disappeared? if I click on the application nothing happens? where on earth has it gone?

---

### Post by nhasian on 2010-02-09
did you set it to auto-hide?  by default its at the bottom of the display and if you move your cursor down there it should appear again.  you can verify your gnome-do is running by pressing Super+space.  Personally i never used the gnome-do's shortcut keys to start applications, i only ever used it as a dock, so i ditched gnome-do in favor of the new docky from the same people.

EDIT: oh it occured to me that you may have trouble launching gnome-do from the applications->accessories menu?  If thats the case, try launching it from a terminal instead so you can see what error messages its outputting.

---

### Post by verachion on 2010-02-09
> **nhasian said:**
> did you set it to auto-hide?  by default its at the bottom of the , i only ever used it as a dock, so i ditched gnome-do in favor of the new docky from the same people.
.

Hi thanks for your help, I managed to get it back up and running by pressing super and space, however. if I pointed the mouse over it nothing would happen. 

Do you know how to get more docklets for it or can you point me in the right direction of another dock, one that is better than gnome do. I am a beginner.

---

### Post by nhasian on 2010-02-09
sure thing.  open up a terminal from applications->accessories.
to get rid of gnome-do enter:

```
sudo apt-get remove gnome-do
```

Now lets add the docky PPA:

```
sudo add-apt-repository ppa:docky-core/ppa
sudo apt-get update
```

finally we can install docky:

```
sudo apt-get install docky
```

its easy to add items to your new dock.  just launch a program like normal, lets say Calculator for example from Applciations->Accessories.  then on your dock right click on the calculator icon and select "Pin to Dock"

there you go.  enjoy your new dock and play around with the options.  you can even have more than one docky dock if you want to :)

---

### Post by verachion on 2010-02-09
> **nhasian said:**
> sure thing.  open up a terminal from 
there you go.  enjoy your new dock and play around with the options.  you can even have more than one docky dock if you want to :)

I am speechless, thankyou so much for helping me out nhasian, I have learnt so much in the last few days because of members like you thankyou.

---

