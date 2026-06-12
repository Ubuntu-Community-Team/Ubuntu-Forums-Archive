---
title: "Altering ttys"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by P.ap G on 2011-02-20
On entering Ctrl+Alt+F4 say , I get tty4 .
 Two questions  how can I increase the font size ?
and is it possible to reverse the background colour ?
Thanks in anticipation.

---

### Post by Keiran230 on 2011-02-21
```
gedit ~/.bashrc
```
This contains the configuration for bash, so you can change some things in there, but it'll change the behavior *after *you login to the tty terminal. As for changing it beforehand, I don't think so, but it'll be somewhere in /etc/ if you can.

---

### Post by deconstrained on 2011-02-21
If you were using a terminal emulator inside of X11, changing these things would be a trivial matter (in the profile settings of the terminal emulator). 

However, since you're referring to literal teletype consoles instead of the text inside a terminal emulator, what I assume you're asking is how to change the console font and color of the non-X-windows command interface. Changing the console font can be done by editing /etc/kbd/config or /etc/console-tools/config;
[http://www.debian.org/doc/FAQ/ch-customizing.en.html](http://www.debian.org/doc/FAQ/ch-customizing.en.html)

However, I don't know if you can change the background color; you'd probably have to do some sort of kernel tweaking in order to get the TTY's to display on top of a framebuffer.

---

### Post by P.ap G on 2011-02-22
Keiran230 ,Thanks for your reply , No bash wouldn't help in this case , anyway I would be working with GUI and what I need to do is at a lower level methinks , so that were I to enter a rescue situation it would lessen the chances of errors . I don't know what other users think but the size of the font is what one would expect in a ' a dodgy sales document ' , for which one would need a magnifying glass  !

deconstrained, Thanks also for your response, I'm looking into your suggestion.

---

### Post by deconstrained on 2011-02-22
> **P.ap G said:**
> anyway I would be working with GUI and what I need to do is at a lower level methinks
If you're working with a GUI...then why tell me **WHY** are you looking into changing the system console font, when you can just use a terminal emulator and have pretty fonts/backgrounds? If (for example) you're using gnome-terminal you can just change the way the terminal looks by right clicking on it, going to "Profiles->Profile Preferences" and changing everything around the way you like it.

---

### Post by P.ap G on 2011-02-23
Deconstrained , as I said "No bash wouldn't help in this case anyway I would be working with GUI and what I need to do is at a lower level "

I was speaking , nay writing , in the conditional tense. Perhaps I should have phrased it differently : No .bashrc wouldn't help , for  [COLOR=Red]were[/COLOR] I to use bash in the way Keiran230 suggested I would be using GUI (which is [COLOR=Red]not [/COLOR]what I want ) , but what I need is at a level below GUI. 

When I started using Linux , Suse 9.2 the fonts were a reasonable size .

As far as terminal / konsole is concerned , changing fonts etc. is as easy as falling off a log .

---

### Post by deconstrained on 2011-02-23
Yeah, I didn't manage to infer that.

So it seems you are working without xorg at all, i.e. on Ubuntu Server? I assumed you hadn't thought of changing it at the emulator level because you posted this in the 'absolute beginner talk' forum...

---

