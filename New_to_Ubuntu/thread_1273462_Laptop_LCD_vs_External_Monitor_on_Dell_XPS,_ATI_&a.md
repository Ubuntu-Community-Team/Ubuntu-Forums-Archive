---
title: "Laptop LCD vs External Monitor on Dell XPS, ATI &amp; fglrx"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by Remagen on 2009-09-23
Well,

What I want:
When I plug in my external monitor to my laptop, I want my laptop screen to go blank so I can close the laptop & not overheat it.  Meanwhile, I want the desktop to be a clone of the Laptop's LCD.

What I have:
I have to leave the laptop lcd on, if I turn it off, my external monitor goes blank too. 


I just don't like leaving my laptop LCD on when it's closed like that, all that heat can't be good for it.

My card is ATI, with fglrx drivers.
FYI, I have to press the fn + screen button for my external monitor to receive output, any way to automate this?

---

### Post by LewRockwell on 2009-09-23
> **Remagen said:**
> When I plug in my external monitor to my laptop, I want my laptop screen to go blank so I can close the laptop & not overheat it.  Meanwhile, I want the desktop to be a clone of the Laptop's LCD.

I have to leave the laptop lcd on, if I turn it off, my external monitor goes blank too.

turn off screen mirroring


> **Remagen said:**
> I just don't like leaving my laptop LCD on when it's closed like that, all that heat can't be good for it.

regardless of whether or not the LCD display is activated, having the lid closed will increase the heat build-up in the internal components of many laptops

.

---

### Post by Remagen on 2009-09-23
If I turn off screen cloning, I'm left with a blank external monitor...

---

### Post by LewRockwell on 2009-09-23
we've got a little Acer netbook hidden behind a 26 inch Samsung LCD so I just went and confirmed that both displays are registering and they both have all the same selections/options

we've turned off the screen mirroring and we've turned off the netbook display

the 26 incher is displaying properly

.

---

### Post by t0p on 2009-09-23
> **Remagen said:**
> Well,

What I want:
When I plug in my external monitor to my laptop, I want my laptop screen to go blank so I can close the laptop & not overheat it.  Meanwhile, I want the desktop to be a clone of the Laptop's LCD.

What I have:
I have to leave the laptop lcd on, if I turn it off, my external monitor goes blank too. 


I just don't like leaving my laptop LCD on when it's closed like that, all that heat can't be good for it.

My card is ATI, with fglrx drivers.
FYI, I have to press the fn + screen button for my external monitor to receive output, any way to automate this?

You should take a look at the programs **xrandr** and **grandr**, as I think they can do what you want.

xrandr is installed by default.  Check its manpage.  But if you want to use grandr, you'll need to install it - type into a terminal the command:

```
sudo apt-get install grandr
```Once it's installed, run it by hitting **Alt+F2** and typing into the box

```
grandr
```

For more useful info on this subject, look [here]("https://wiki.ubuntu.com/X/Config/Resolution").

---

