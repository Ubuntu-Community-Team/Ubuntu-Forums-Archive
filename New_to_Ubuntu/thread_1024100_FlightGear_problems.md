---
title: "FlightGear problems"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by DucksAndDolphins on 2008-12-28
Yes, this is a duplicate. I had it in the Wine forum, but I wasn't getting an answer quick enough (which is relatively vital):

So I finally got FlightGear downloaded and installed correctly, however, the only way I seemed to be able to do it was through Wine. When I try and run FlightGear off of its icon on my desktop, all I get is a black screen that I can only get out of with Alt+F4. Ive only tried running the physical FlightGear Launcher out of Wine once and it seems to have worked alright, but I haven't actually tried playing yet out of Wine.

I wanted to know if downloading/installing/running it through Wine was the wrong thing to do.

---

### Post by adobrakic on 2008-12-28
Unless FlightGear can run natively in Ubuntu, then you did the right thing (by using Wine.)

--edit--
FlightGear seems to be in Synaptic, is there a reason you didn't use that one?

---

### Post by arubislander on 2008-12-28
Haven't seen your post in the Wine forum so don't know if you've mentioned it, but why wouldn't you just install FlightGear from the repositories?

---

### Post by DucksAndDolphins on 2008-12-28
I didnt know I could do it from the repositories or from synaptic.

Could you go into detail about either of those?

---

### Post by Joao Paz on 2008-12-28
I got my copy of flightgear through Ubuntu's Applications>Add/Remove applications (sorry if I'm translating it wrong from my PT setup) - is that what you Gents are calling "Synaptics"?

Anyway, I can run flightgear if in "small window" mode, as it is when I call it the first time, but if I try to maximize the window I'll get a black screen, too... the sim seems to freeze until I come back to the original (very small) window size.

Edit: this reply isn't meant to be a solution! :) just to add my share to the original problem.

---

### Post by arubislander on 2008-12-28
There are indeed a couple of ways to install flightgear from the repositories. Synaptic is one: (select System\Administration\Synaptic Package Manager from the menu).
The command line is another:
```
$ sudo apt-get install flightgear
```
But Joao's way might be more familiar (select Applications\Add/Remove... from the menu)

whichever way you choose, you'll get an entry in the Applications\Games menu for flightgear.

Let us know how you fare with that.

@Joao: Could the black screen be a video card issue? Do you have the right drivers for yours?

---

### Post by DucksAndDolphins on 2008-12-28
kay well i got it out of Synaptic, and i'll see how it works from there, but its in the Games menu now. So i'll update you on that.

---

### Post by arubislander on 2008-12-31
I was wondering if you already had a chance to try out the FlightGear from installed from the repositories...

---

### Post by marcgh on 2008-12-31
I have downloaded via the synaptic download manager.
Run a search for FlightGear and apply
( 220 + Mb to download )
all works well for me

---

