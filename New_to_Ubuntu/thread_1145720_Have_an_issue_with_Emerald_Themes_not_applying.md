---
title: "Have an issue with Emerald Themes not applying"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by xjjjay on 2009-05-01
I just installed Emerald using synaptic on Linux Mint 6. In Emerald, I googled it up and read that I could click a theme and open a terminal and type "emerald --replace". I did so and the theme applies, but when i close the terminal window borders disappear. How can I make them stay or at least default back to the original?

Thanks

---

### Post by Kareeser on 2009-05-01
Append an amperstand (&) to the end of the command. That'll let it run in the background, meaning you can close the terminal window.

For future sessions, you'll want to make emerald your default window decorator. You can add "emerald --replace &" to a startup script in System -> Administration

---

### Post by xjjjay on 2009-05-01
Thanks, that's just what i was looking for!
EDIT: Even with the &, after i close the terminal the borders disappear :[

---

### Post by xjjjay on 2009-05-01
Help!

---

### Post by MontelEdwards on 2009-05-01
please do not bump a thread within 7 minutes.
bumping is to done after one day


open  a terminal and type
```
sudo apt-get install fusion-icon 
```then go to applications>compiz fusion icon.
Then in the notifaction area in Gnome [right hand corner of screen] right click the blue box.
Then go to select window decoder, and check emerald.

then go back to the emerald manager and click your theme
it will instantly load...permanently

---

### Post by Kareeser on 2009-05-01
Furthermore, don't X out of the terminal window. Type "exit" instead.

---

### Post by xjjjay on 2009-05-01
Still no good, same problem. The theme did not instantly load--instead, emerald locks up.

---

### Post by MontelEdwards on 2009-05-01
What do you mean emerald locks up??? elaborate.


Try selecting your theme, closing emerald, and then select emerald as the window decoder

---

### Post by vonti on 2009-05-01
xjjjay, maybe you should switch to a OSX :D, it has a gnome-type looking desktop just like Ubuntu and is much easier to configure.

---

### Post by MontelEdwards on 2009-05-01
> **vonti said:**
> xjjjay, maybe you should switch to a OSX :D, it has a gnome-type looking desktop just like Ubuntu and is much easier to configure.
what???

---

### Post by vonti on 2009-05-01
Oh yes it is, even my 70 year-old grandmother could configure a Mac, come on man, get down to earth -.-

---

### Post by MontelEdwards on 2009-05-01
> **vonti said:**
> Oh yes it is, even my 70 year-old grandmother could configure a Mac, come on man, get down to earth -.-
naw, i was just wondering why you posted something irrelevant, obviously he does not have a mac and is trying to configure Mint

---

### Post by vonti on 2009-05-01
yup, well I had the same problem with my Gentoo, and that(and many others) made me switch to Ubuntu, where everything works just fine, the same as the > emerald --replace & command, xjjjay, that should work perfectly for you.

---

### Post by Redundant Username on 2009-05-01
After you set it up as a startup process through system->preferences->start up applications log lout and log back in and see if it works.

---

### Post by vonti on 2009-05-01
If it doesn't you can do what my friend did, download Tilda, bind grave for using Tilda and type in >  emerald --replace & that way you'll never hit the X button ^^

---

### Post by cybergalvez on 2009-05-01
install fusion-icon by far the simplest way to start emerald, it will also have a link to the emerald config program

---

### Post by pi.boy.travis on 2009-05-01
If you hit Alt+F2, then type your command in, you should be set.

---

