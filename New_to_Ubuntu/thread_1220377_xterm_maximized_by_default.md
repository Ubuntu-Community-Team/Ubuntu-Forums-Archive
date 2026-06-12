---
title: "xterm: maximized by default"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by crowhill on 2009-07-22
hi there

i'm using vim in xterm. therefore, i want xterm to open in a maximized window by default. however, when i add 

> xterm*maximized: true

to my .Xresources file, xterm does not startup fully maximized. i always have to hit <alt+space> to open the window menu, followed by hitting <x> to get it nicely maximized. [COLOR="Red"]**how can i make xterm to open in a maximized window?**[/COLOR]

by the way, typing

```
xterm -maximized
```

in a gnome-terminal (or in xterm) does not give me a fully maximized xterm window either.

some help would be fantastic.

thanks a lot in advance,
cheers,
crowhill.

---

### Post by kerry_s on 2009-07-22
the **~/.Xresources** is
```

**XTerm*Maximized: true**

```

make sure you run-> **xrdb -merge $HOME/.Xresources**
i suggest putting the command in ~/.profile so it can be loaded when you log in.

can't say about the command line it works for me.

---

### Post by crowhill on 2009-07-22
the .Xresources file is not case sensitive, as it seems ... your line made no difference (after logging out and back in to restart the x-session).

i also run xrdb -merge $HOME/.Xresources but i get the output

> /home/usr/.Xresources:1:3: error: invalid preprocessing directive #File

take a look at my screenshots. the first shows how xterm looks before i do the <alt+space> followed by <x> and the second after i've done it. the difference is small but it bothers me ...

---

### Post by kerry_s on 2009-07-22
the first is maximized, what its doing is keeping the proper row to column ratio. 

try reading: [http://invisible-island.net/xterm/xterm.faq.html#setup_resize](http://invisible-island.net/xterm/xterm.faq.html#setup_resize)

from here, in case you want to learn other stuff:
[http://invisible-island.net/xterm/xterm.faq.html](http://invisible-island.net/xterm/xterm.faq.html)

---

### Post by crowhill on 2009-07-23
thank you very much for your effort. however, the link you sent me contains information that is too advanced for me.

i tried to add something to my **.vimrc** file so that vi starts up in a maximized window when i call it from xterm. i tried to use the *set columns* and the *set lines* but it didn't really work (the adjustments seem to happen inside the given xterm window).

what are the commands behind the window menu entries (you get the menu by hitting <alt+space>)? if i knew them i might be able to put the one for the maximization in either **.Xresources** or **.vimrc**. another option would be to write a bash script that'd start xterm and then execute that unknown metacity-window-maximizing/fullscreening-command. any ideas on that?

i really hope i can fix this.

thank you very much,
cheers,
crowhill.

---

### Post by poosietgp on 2009-07-23
how about...
```
xterm --geometry 1280x1024
```

---

### Post by crowhill on 2009-07-23
nope, still the same window size, which you get from

```
xterm -maximized
```

and that is not fully maximized ...

---

### Post by crowhill on 2009-07-23
i figured out a solution. however, it's not perfect (i guess, this is because neither any x-session nor metacity are perfect).

first, i installed devilspie. second, i wrote the script

```
(if
	(is (application_name) "xterm")
		(fullscreen)
)
```

saved it under xterm_start.ds, which i put in a new folder /home/usr/.devilspie. finally, i made devilspie to start automatically when ubuntu fires up. now, hitting my preferred <ctrl+alt+t> gives me not only an xterm but also a maximized one!

i would be much happier though if this could be done without having to install additional stuff.

anyways,
thx a lot for all your help.

cheers,
crowhill.

---

### Post by poosietgp on 2009-07-24
did you type xterm -maximized in cli?

---

