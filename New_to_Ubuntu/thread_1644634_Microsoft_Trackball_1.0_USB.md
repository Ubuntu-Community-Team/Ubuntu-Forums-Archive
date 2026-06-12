---
title: "Microsoft Trackball 1.0 USB"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by KWLLC on 2010-12-13
I use a trackball from MS called an trackball optical 1.0 connected via USB. It has 4 keys on top, a scroll wheel that also contains a key if you push the wheel to the right. Due to physical limitations, I love this trackball but I don't understand how to create keybindings so that the various keys work consistently across the Linux apps that I use. 
For example, Firefox executes the correct function on all 4 of the keys on top of the unit. Left to right they are back 1 page, enter/select, context menu and forward 1 page. The wheel scrolls up and down as expected. The wheel key doesn't function. 
But in the Synaptic app, neither page keys function.
I used to be able to click with the wheel and the icon would change to the scroller icon and by moving above or below the icon it would line-scroll at a speed proportional to the distance you moved from a horizontal imagined from the icon.
Could anyone provide doc to me that would allow me to roll my own key bindings for this or find a prewritten that does what I am looking for? Taksumikka

[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]file:///tmp/moz-screenshot-2.png[/IMG][IMG]file:///tmp/moz-screenshot-3.png[/IMG]

---

### Post by fly-by-night on 2010-12-13
I have a "plain and simple" HP mouse with no special buttons.  In Synaptic when I press the scroll button I too don't get that "icon" you mentioned (but in Firefox - yes).  Normal scrolling with the scroll button work, but that's not what you're after. 

The back/forward options don't work on the keyboard (alt+left/right or backspace), so I don't think it will work with your mouse either (Synaptic).  There is also no back/forward option in the menus - which make key bindings for that unlikely.

---

### Post by khelben1979 on 2010-12-14
I would recommend that you try with [xmodmap]("http://linux.die.net/man/1/xmodmap"). Read on at [Custom Keybinding]("http://scrolls.mafgani.net/2005/08/custom-keybinding-gnome/") (GNOME).
```

sudo apt-get install xmodmap
``` The above code installs the application. 

Then run the command and click on the different buttons on your trackball mouse there and you'll see different values. These values can you use when you create keybindings for what you want the buttons to do.

---

