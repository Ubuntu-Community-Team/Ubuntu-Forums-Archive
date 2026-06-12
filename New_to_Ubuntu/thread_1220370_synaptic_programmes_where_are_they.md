---
title: "synaptic programmes where are they?"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by albert s on 2009-07-22
ive lost a few programmes that i have showing as being installed using synaptic installer.
some simply show up in accessories etc, but some dont, I can find the files, 
and have even used the build-apt and get the reading that they are installed but i cant find them, just the files.!
I am really really new to all this and want to do the swap but am finding it increasingly difficult right now due to my lack of knowledge.
the main programme i am trying to locate is aircrack,(long story on another thread of mine), should i just try downloading again?
is there a way of getting these to set up on my desktop automactically?
the other file i need is some form of music player, also it shows totem as being installed,
but i cant play music CDs.........
the remainder that i have lost/cant access i can mess about trying to find,
gives me something to learn from,!
but these two are a bit incidental in getting my girlfriend convinced that i have done the right thing by wiping windoze off both the laptop and my other old PC and using ubuntu.
my Girlfriend uses the laptop in various locations and Ive wiped out all her wifi passwords!
(including the home one!) during the change. she is impressed with the speed though.!
UBUNTU 9 Jaunty

---

### Post by mike555 on 2009-07-22
Very often the executable can be searched for ,( places > search for files) by just putting in the name of the app ,setting the look in folder to "file system"... if that doesn't work click for more options and type the name in there ...

---

### Post by t0p on 2009-07-22
Don't download aircrack again!  If it's installed, it's installed.  You can check if it's there by typing into the terminal

```
which aircrack-ng
```

If it is installed, you'll get a response something like 

```
/usr/bin/aircrack-ng
```

Aircrack-ng is a command-line program.  To run it, you need to type the appropriate commands into the terminal.  To discover what commands you need to run, you have to consult the documentation - you can't just type "aircrack" and expect a gui to pop up.  Look at the man page - you do this by typing into the terminal

```
man aircrack-ng
```

Then again, the man page may be a little too dry.  If so, check out [www.aircrack-ng.org]("http://www.aircrack-ng.org").  You'll find docs there.

Concerning your music CD problems: you should be able to play them. You might have to open the app called **Brasero** first (**Applications > Multimedia > Brasero Disc Burning**) first... I can't remember, it's been a while since I played a CD through my computer.

As for your girlfriend's wifi passwords - you should have backed up that stuff before you installed ubuntu.  Everything that was on the hard drive before you stuck ubuntu on there is now gone, never to be seen again!

---

### Post by albert s on 2009-07-22
excellent,
I now have music.! just trying to use the wrong program perhaps!?
so one down one to go,
I'll have a go at the other tomorrow evening on my old pc which is upstairs in spare room,
dont want to mess up the GFs laptop any more at this stage.!
thanks for all the help so far, 
I'll let you know how i get on.

---

