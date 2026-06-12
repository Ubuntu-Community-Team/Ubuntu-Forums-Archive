---
title: "working on screen resolution on an old laptop"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by romeug on 2010-04-22
I have been working with Ubuntu Studio dual boot on an old Sony Vaio laptop stuck in an 800x600 screen resolution Xconf obviously having a problem finding the proper drivers for the intel chip (82830).  There are numerous edits offered both on the forums and wiki for the (now optional) Xorg.conf file which i have tried, as well as a temporary fix for the Xrandr which also results in a blank screen.  Must say, i am getting pretty comfortable with the terminal.
This has not stopped me from using Ubuntu in the half screen, and i enjoy it immensely giving be quite a bit of more in program options than i could afford in Windows.
My reading has shown that there was a gui program called displayconfig-gtk which allowed the picking of drivers and screen resolution and generating an Xorg.conf file.  It seemed another option to try, I cannot find the program, I think it was offered in Hardy 8.04 and not in the karmic 9.10 program archives. 

does this seem a valid direction, is there any thought that the next 10.04 package may contain a fix, or is there any other suggestions to get this fixed?  I only see that nvidia cards have been addressed in the upgrade features.  

One of my primary uses of a computer is for graphics, so this is a bit of an impediment.

---

### Post by Temposs on 2010-04-22
I'm glad you're getting comfortable in the terminal!

You might try loading up Ubuntu 10.04 in a livecd to see if it gives you full resolution.

---

### Post by P4man on 2010-04-22
what does running xrandr show you?

I got a few people solving their resolution problem with older intel graphics in this thread:
[http://swiss.ubuntuforums.org/showthread.php?t=1313849&page=6](http://swiss.ubuntuforums.org/showthread.php?t=1313849&page=6)

Its rather long thread and difficult to follow, but The Cog turned in to a nice little script (that I havent tested):

```

#!/bin/sh

horiz=[COLOR="DarkGreen"]1360[/COLOR]
vert=[COLOR="DarkGreen"]768[/COLOR]
rate=[COLOR="DarkGreen"]60[/COLOR]
screen=[COLOR="Indigo"]VGA1[/COLOR]
modename="$horiz"x"$vert"_"$rate"


mode=$(cvt $horiz $vert $rate | grep Modeline | cut -d ' ' -f 3-)
#mode=$(gtf $horiz $vert $rate | grep Modeline | cut -d ' ' -f 5-)

xrandr --newmode $modename $mode
xrandr --addmode $screen $modename
xrandr --output $screen --mode $modename
```

Paste that in a text file,  Change [COLOR="DarkGreen"]resolution[/COLOR] and [COLOR="DarkGreen"]refresh[/COLOR] rate according to your monitor, make the script executable and run it.
You may also have to replace [COLOR="Indigo"]VGA1[/COLOR] with VGA.

---

### Post by romeug on 2010-04-22
Nice idea P4man, i will generate my xrandr on my other computer and have a look, there are some differences with the Cogs method than on the Xrandr modifications that i found on the wiki:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
perhaps it will be more successful

The entire thread will keep me busy for a bit, as i want a general understanding of Ubuntu...thanks, gabriel


> **P4man said:**
> what does running xrandr show you?

I got a few people solving their resolution problem with older intel graphics in this thread:
[http://swiss.ubuntuforums.org/showthread.php?t=1313849&page=6](http://swiss.ubuntuforums.org/showthread.php?t=1313849&page=6)

Its rather long thread and difficult to follow, but The Cog turned in to a nice little script (that I havent tested):

```

#!/bin/sh

horiz=[COLOR="DarkGreen"]1360[/COLOR]
vert=[COLOR="DarkGreen"]768[/COLOR]
rate=[COLOR="DarkGreen"]60[/COLOR]
screen=[COLOR="Indigo"]VGA1[/COLOR]
modename="$horiz"x"$vert"_"$rate"


mode=$(cvt $horiz $vert $rate | grep Modeline | cut -d ' ' -f 3-)
#mode=$(gtf $horiz $vert $rate | grep Modeline | cut -d ' ' -f 5-)

xrandr --newmode $modename $mode
xrandr --addmode $screen $modename
xrandr --output $screen --mode $modename
```

Paste that in a text file,  Change [COLOR="DarkGreen"]resolution[/COLOR] and [COLOR="DarkGreen"]refresh[/COLOR] rate according to your monitor, make the script executable and run it.
You may also have to replace [COLOR="Indigo"]VGA1[/COLOR] with VGA.

---

### Post by romeug on 2010-04-22
I am a bit on the edge of my seat waiting for the end of the months release, for both the upgrade (which i will do, repairing this issue or not), and setting up a large live persistent USB drive...I do some non profit work (computer literacy tutoring and IT) for a soup kitchen's computer room and have started introducing a few people to some open source like open office and gimp, and i honestly think that it empowers the less fortunate (only economically) with some rather powerful tools.  Linux may be a next step...
they have a band and i think that Ubuntu Studio can be a major asset...


> **Temposs said:**
> I'm glad you're getting comfortable in the terminal!

You might try loading up Ubuntu 10.04 in a livecd to see if it gives you full resolution.

---

