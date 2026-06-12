---
title: "Problem Black Screen after Game Install ?"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by Trolen on 2011-01-01
[CENTER][SIZE=3]**Problem Black Screen after Game Install ?**[/SIZE]

I have just installed Counter Strike with your help via *Wine & Steam.Everything ok,until the second time that i ran the game.*

When i press to launch it goes black the entire screen . **But i hear the sound from the click's in the options.So it doesn't show anything only i can hear.**

And , *_**the 1st time i opened it i changed the option's to D3D 1680X1050 16Bit,in Widescreen.**_*After that i restarted and gave me a black screen.
[B]
What can i do to fix it?[/B]
:lolflag:
[/CENTER]

---

### Post by blazemore on 2011-01-01
The -autoconfig launch option will allow Steam to configure the game with the best settings for use on your machine.

[LIST=1]
[*]Open Steam in Wine
[*]Go to the My Games tab
[*]Right-click the game which needs to be reconfigured
[*]Select Properties from the menu
[*]Click the Set launch options... button
[*]Add -autoconfig at the end of the line, be sure to include a space before the "-" and anything before it
[/LIST]

---

### Post by Trolen on 2011-01-01
OK because it is too late and i am really tired i will try it tomorrow 1st thing in the morning.

---

### Post by Trolen on 2011-01-02
I have just tested it out.

The game is opening but it LAGS tooooo much!

Something like 10 FPS.When i had windows i had 50-60 FPS.

So how can i fix it ? I think i don't have something ...

---

### Post by Trolen on 2011-01-02
Please help :) From everyone,you are all well-known and familiar with Ubuntu - Linux or so..but i am not.

So i need your desperate help for me to play the game :(

---

### Post by blazemore on 2011-01-02
OK don't panic. I get email alerts when someone posts in a thread I subscribe to. I was at work when I read your post on my lunch break, and didn't particularly fancy posting from my phone in the staff canteen.

Anyway I'm back now with the following suggestions:
Make sure you're running the most up-to-date graphics driver for your hardware. Make sure your system is fully updated in Update Manager, and all restricted drivers are installed in System -> Administration -> Additional Drivers.

Secondly, before you play the game, disable compositing (desktop effects) by setting your graphical effects to None in Appearance preferences.

Thirdly, don't use D3D in the game. While Wine technically supports Direct X, you're better off using OpenGL if it's available (I'm fairly sure the original Counter Strike uses the same engine as the original Half Life, so that should be an option)

I hope this helps.

---

### Post by blazemore on 2011-01-02
OK don't panic. I get email alerts when someone posts in a thread I subscribe to. I was at work when I read your post on my lunch break, and didn't particularly fancy posting from my phone in the staff canteen.

Anyway I'm back now with the following suggestions:
Make sure you're running the most up-to-date graphics driver for your hardware. Make sure your system is fully updated in Update Manager, and all restricted drivers are installed in System -> Administration -> Additional Drivers.

Secondly, before you play the game, disable compositing (desktop effects) by setting your graphical effects to None in Appearance preferences.

Thirdly, don't use D3D in the game. While Wine technically supports Direct X, you're better off using OpenGL if it's available (I'm fairly sure the original Counter Strike uses the same engine as the original Half Life, so that should be an option)

I hope this helps.

---

### Post by Trolen on 2011-01-02
Thank you really much mate,about that you are answering to me.

OK.I Must tell you all the games.

[B]1)Counter Strike
2)Alien Vs Predator 2
3)Left 4 Dead 2[/B]

This are the games.
But i see LAG to every single one of them.I most play LEFT 4 DEAD and Alien Vs Predator.

Also,i disabled the desktop effects,and additional drivers are all activated.

**Also,why not D3D ?**

**That should be right,correct my VGA to work probably ?**

SO.....In conclusion.

My drivers i think that they are up to date.But the Steam says that there is an update,it is downloading but it doesnt install it.

**So...this are all the options!**

---

### Post by Trolen on 2011-07-24
I haven't figure it out ,how to do it. 

But... i made Dual Boot to play my games so i left the Linux with no games at all :)

Thank you for your help BTW.

---

### Post by hakermania on 2011-07-24
Windows for games
Linux for real
&#960;&#945;&#964;&#961;&#953;&#974;&#964;&#951;!

---

### Post by pierreyy on 2011-07-24
> **Trolen said:**
> [CENTER][SIZE=3]**Problem Black Screen after Game Install ?**[/SIZE]

I have just installed Counter Strike with your help via *Wine & Steam.Everything ok,until the second time that i ran the game.*

When i press to launch it goes black the entire screen . **But i hear the sound from the click's in the options.So it doesn't show anything only i can hear.**

And , *_**the 1st time i opened it i changed the option's to D3D 1680X1050 16Bit,in Widescreen.**_*After that i restarted and gave me a black screen.
[B]
What can i do to fix it?[/B]
:lolflag:
[/CENTER]


How about you try "PlayONLinux" i think it should run the games fine( i havent tried it though) i know that there is a compatibility list so fgive that a try and let us know.

---

### Post by pierreyy on 2011-07-26
So it worked? great!

---

