---
title: "Terminal/GUI &quot;slipstream&quot;"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by deviator on 2010-02-12
I don't know if slipstream would be the right term to use but am wondering if there is a way to get a terminal window to output the command when i do something the easy way through the GUI.

like when i right click to eject a cd for example it will output the terminal instructions.

just so it's easier for me to get familiar with using terminal commands :-({|=

---

### Post by skymera on 2010-02-12
I know what you mean, and i quite like the idea :)

I've never seen this question asked, hopefully someone else can help you :)

---

### Post by nothingspecial on 2010-02-12
I don`t know either, but I do have one tip for you...

Go system > preferences > main menu

choose any item in there and choose properties

That will tell you the command to launch it.

The apps are obvious, I mean in the system tab.

---

### Post by ibuclaw on 2010-02-12
I do (sort of) see what you mean, but I don't really see the point.
Besides, most things you do in GUI are handled by libraries, not external applications (forking to an application is a heavy duty business). :)

---

### Post by deviator on 2010-02-12
> **nothingspecial said:**
> I don`t know either, but I do have one tip for you...

Go system > preferences > main menu

choose any item in there and choose properties

That will tell you the command to launch it.

The apps are obvious, I mean in the system tab.

very nice, if nobody has a solution for this i might try to create something in the future

---

### Post by nothingspecial on 2010-02-12
> **ibuclaw said:**
> I do (sort of) see what you mean, but I don't really see the point.
Besides, most things you do in GUI are handled by libraries, not external applications (forking to an application is a heavy duty business). :)

Well said,

for example, to play/pause the highlighted track in guayadeque music player you would have to type

```

dbus-send --print-reply --type=method_call --dest=org.mpris.guayadeque /Player org.freedesktop.MediaPlayer.Play
```

Kind of easier to click play really.

---

### Post by deviator on 2010-02-12
> **nothingspecial said:**
> Well said,

for example, to play/pause the highlighted track in guayadeque music player you would have to type

```

dbus-send --print-reply --type=method_call --dest=org.mpris.guayadeque /Player org.freedesktop.MediaPlayer.Play
```

Kind of easier to click play really.

true, although i was thinking more along the lines of not being able to eject a cd (just read a thread on here and this popped into mind)

:-P

i think i get what you mean though by right clicking and selecting eject from the desktop would not be the same as <insert command here, i already forgot)

---

### Post by Hospadar on 2010-02-12
I think the short answer is, for the most part, no (unfortunately).

Some GUI applications can be controlled from the command line (mplayer or the above post would be good examples), but most cannot.  That said, some GUI applications (all cd burning software, almost all video transcoding software, etc) are just frontends for some command-line backend that does all the heavy lifting.  There's really no universal way to figure that out other than research.

Most GUI applications do not have controls which can be manipulated by command-line switch or dbus command (dbus is a cross-program message-passing protocol btw, it's the underlying protocol that facilitates those little update notifiers, among other things), simply because they were meant to be GUI programs and the programmer never built in that functionality.

That said, with the possible exception of editing photos there is almost nothing I can't do in the terminal, including (but not limited to): browsing the web, editing photos, transcoding video, checking email, programming, playing games, listening to music, watching videos, etc.

I think the best way to learn to do anything in the terminal is just to shoot it through the google.  if you were to google "linux command line <whatever that thing is you want to do>" if it was at all possible you'd probably get about a million hits of people who posted how to do just that on the website.  I do this almost every day at work to figure out some quicker way to do something or script something from the terminal.

---

### Post by deviator on 2010-02-12
> **Hospadar said:**
> I think the short answer is, for the most part, no (unfortunately).

Some GUI applications can be controlled from the command line (mplayer or the above post would be good examples), but most cannot.  That said, some GUI applications (all cd burning software, almost all video transcoding software, etc) are just frontends for some command-line backend that does all the heavy lifting.  There's really no universal way to figure that out other than research.

Most GUI applications do not have controls which can be manipulated by command-line switch or dbus command (dbus is a cross-program message-passing protocol btw, it's the underlying protocol that facilitates those little update notifiers, among other things), simply because they were meant to be GUI programs and the programmer never built in that functionality.

That said, with the possible exception of editing photos there is almost nothing I can't do in the terminal, including (but not limited to): browsing the web, editing photos, transcoding video, checking email, programming, playing games, listening to music, watching videos, etc.

I think the best way to learn to do anything in the terminal is just to shoot it through the google.  if you were to google "linux command line <whatever that thing is you want to do>" if it was at all possible you'd probably get about a million hits of people who posted how to do just that on the website.  I do this almost every day at work to figure out some quicker way to do something or script something from the terminal.

enlightening, thanks.:D

---

### Post by nothingspecial on 2010-02-12
What do you want to do? I use command line apps all the time.

Anything specific?

---

### Post by deviator on 2010-02-12
> **nothingspecial said:**
> What do you want to do? I use command line apps all the time.

Anything specific?

not really was just thinking it would be a useful learning tool (for myself anyway) untill you mentioned the whole library thing which gave me a better perspective on the situation.

as for googling, it usually leads me here anyway so i guess i'll be around more often:D

---

