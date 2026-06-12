---
title: "minimize new terminal windows"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by rgb96 on 2009-02-12
I'm writing a program in perl that has to call a whole bunch of other scripts to run at the same time. Right now I'm accomplishing that by sending the OS this command 

```
gnome-terminal --working-directory=./AsteriskPRI/zapX/channel_Y --title=Channel_Z --execute ./master.sh call 1000
```

Where X Y and Z differ depending on which config the user chooses to load. This all works fine, but I would like to know if there is another parameter I could pass to avoid having 30 new terminal windows popping up on me. Is there a way I could have the terminal windows just run in the background? Or at least be minimized when they start?

---

### Post by mttman on 2009-02-12
Hello,

If i understand this correctly you are running this command in the command line. try adding a "&", no quotes, to the end of the command and that will background it

<Mttman>

---

### Post by rgb96 on 2009-02-12
Yeah. I'm basically sending that command to temrinal. Tried putting an ampersand at the very, and 1 space after the very end, neither seemed to make a difference

Thanks for the response though.

---

### Post by kanikilu on 2009-02-12
If you do gnome-terminal --help, you'll notice it has an option for maximizing (--maximize) and fullscreen (--full-screen), but not minimizing :(

---

### Post by rgb96 on 2009-02-12
ah... lame. I guess I'll just have to deal with way too many terminal windows, lol.

---

### Post by mttman on 2009-02-12
you might try running your program through a different terminal program. can't think of one off the top of my head and i'm not at my ubuntu comp.

---

### Post by kanikilu on 2009-02-12
I've already checked xterm, rxvt and konsole, none have that option.

/EDIT - actually xterm, rxvt, eterm, etc. all have an "iconify" option to start iconified, but apparently metacity doesn't know what that is. It might be a bit drastic to switch window managers just for this, though ;)

---

### Post by donkyhotay on 2009-02-12
Yakuake is the best terminal program around IMHO. It's a KDE program but I consider it worth installing all the KDE libraries even though I prefer gnome. Essentially it gives you a quake style CLI with multiple tabs if you want them. Really nice for typing in some commands then shoving the terminal into the background so it's out of your way. It's in the ubuntu repositories if you want to check it out.

//edit: read the original post closer and I don't think is what you're looking for though, sorry. 

//edit edit: If you don't like the command switches current available in gnome-terminal you could always hack the code to implement the feature yourself. (c;

---

### Post by mttman on 2009-02-12
what if you were to put that command into a shell script and run that script in the background ex.

echo <command> > shell.sh
shell.sh &

would that stop the terminal cascade you get?

---

### Post by adam_kimber on 2009-02-12
I think this might help. You can start bash scripts that run in a terminal etc from a launcher. You can also string commands together in the launcher using the standard bash &&. In fact I think you could right some bash scripting straight into the launcher but I have not tried it yet. e.g.

```
bash -c "xterm && xterm"
```

The above launches an xterm and when that one is closed launches another! 

eg.2

```
bash -c "firefox www.ubuntu.com && firefox ubuntuforums.org"
```

---

