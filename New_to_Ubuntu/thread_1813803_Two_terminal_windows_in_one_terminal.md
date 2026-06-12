---
title: "Two terminal windows in one terminal"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by lordievader on 2011-07-28
I have a question, I watch Hak5, and every time Darren's terminal is shown I wonder how he does it. He has two terminal tabs/sessions, one on top and one below.

I know how to get multiple tabs in one terminal window, but I don't know how to get them above one another.
-Lordievader.

---

### Post by nothingspecial on 2011-07-28
Type ```
screen
```

Install it if you don't have it.

Press Ctrl-A then C to create a second session

Ctrl-A then Shift-S to split your screen horizontaly

Ctrl-A then 1 to move the screen to the other session.

Ctrl-A Tab to switch between them.

Any questions, post back

---

### Post by lordievader on 2011-07-28
That seems to work, thank you. Shortcuts are still a bit strange, but I guess that is just getting used to, thank you!

---

### Post by nothingspecial on 2011-07-28
You could try byobu, which simplifies some of the short cuts although not the splitting ones or the Tab one.

F2 creates a new session
F3 switches to the left
F4 switches to the right
F7 enters copy and paste/scroll mode
F8 lets you rename the window

There is also a funky status bar

[ATTACH]198705[/ATTACH]

---

### Post by malspa on 2011-07-28
Also, Konsole in KDE4 has the split screen feature, without having to install anything. You don't have to use shortcuts, the feature's available right from Konsole's View menu.

---

### Post by lordievader on 2011-07-28
This doesn't seem to be exactly what I want, unless it could divide the screen with in the upper 50% terminal 1 and in the bottom 50% terminal 2. That screen program did that quite well.

@nothingspecial: That is awesome, could you explain how to enable the sidebar?

@malspa: I'm on Ubuntu/Gnome, so thank you, but it isn't very useful.

---

### Post by nothingspecial on 2011-07-28
> **lordievader said:**
> 

@nothingspecial: That is awesome, could you explain how to enable the sidebar?


It's not a sidebar, rather 4 "windows" within screen/byobu.

It's difficult to explain but here goes.....

```
byobu
```

Make another 3 "windows"

F2 F2 F2

you'll see them listed on the bottom bar

Split the screen vertically

Ctrl-A then | 

Then resize the right hand window (you'll have to play with this a bit)

Ctrl-A then : (this puts screen in command mode)

type

resize n

where n is the size, my left is 110, so I would type resize 110, like I said you'll have to experiment.

Then move to the right

Ctrl-A then Tab

split the screen vertically twice

Ctrl-A then Shift-S (x2)

Then resize them vertically as before. Resizing vertically take precedence over horizontally. This is why we do the width resizing before we create vertical splits.

Then in each "window" (remember Ctrl-A then Tab to move), press F3 or F4 untill you have one of your 4 sessions in each one.

I am running elinks (web browser) on the left, then top to bottom on the right......

squeezeslave (that's a whole other issue, unless you are running it go with a different cli music player - mplayer, cvlc, nvlc, moc, cmus etc etc)

alpine, a mail client

irssi, an irc chat client.

Hope that explains it. You can set all this up so it all launches automatically like that, but you need to know what you want first.

Have fun.

Oh, and you can change the layout of the bottom bar and other stuff with F9, you can even have notifications in it aslong as the gui is running, even if you are on tty1-6.

Have fun. :popcorn:

---

### Post by lordievader on 2011-07-28
Wow, thank you! This is awesome. I'm gonna play with this some more, thank you.

Little fun fact, alpine is also the default password for an iphone/ipod.

---

### Post by malspa on 2011-07-28
> **lordievader said:**
> @malspa: I'm on Ubuntu/Gnome, so thank you, but it isn't very useful.

Well, for anyone that finds it useful, I've got Konsole installed in Ubuntu 11.04 (which your sig says you're using, by the way -- but since neither the thread title nor the original post specified any particular DE, I thought I'd mention it), and the split view works quite nicely here in Unity.

Of course, I know that many people are averse to running KDE apps in GNOME or whatever. Never quite understood that one.

---

### Post by tyoli on 2011-08-01
> **nothingspecial said:**
> It's not a sidebar, rather 4 "windows" within screen/byobu.

It's difficult to explain but here goes.....

```
byobu
```

Make another 3 "windows"

F2 F2 F2

you'll see them listed on the bottom bar

Split the screen vertically

Ctrl-A then | 

Then resize the right hand window (you'll have to play with this a bit)

Ctrl-A then : (this puts screen in command mode)

type

resize n

where n is the size, my left is 110, so I would type resize 110, like I said you'll have to experiment.

Then move to the right

Ctrl-A then Tab

split the screen vertically twice

Ctrl-A then Shift-S (x2)

Then resize them vertically as before. Resizing vertically take precedence over horizontally. This is why we do the width resizing before we create vertical splits.

Then in each "window" (remember Ctrl-A then Tab to move), press F3 or F4 untill you have one of your 4 sessions in each one.

I am running elinks (web browser) on the left, then top to bottom on the right......

squeezeslave (that's a whole other issue, unless you are running it go with a different cli music player - mplayer, cvlc, nvlc, moc, cmus etc etc)

alpine, a mail client

irssi, an irc chat client.

Hope that explains it. You can set all this up so it all launches automatically like that, but you need to know what you want first.

Have fun.

Oh, and you can change the layout of the bottom bar and other stuff with F9, you can even have notifications in it aslong as the gui is running, even if you are on tty1-6.

Have fun. :popcorn:

hi, this is awesome but i got a problem with the resize command when i type:
```
resize 110
```
it prints out this:
```
Usage: resize [-u] [-c] [-s [rows cols]]
```
so what to do here.
thanx.

---

### Post by lordievader on 2011-08-01
I figured this out, what you need to do is the following:

You have byobu running and you have split the screen.
Ctrl-A and then you type
```
:resize 110
```

It took me a while to to see the :, but it is needed.

---

### Post by nothingspecial on 2011-08-01
> **lordievader said:**
> I figured this out, what you need to do is the following:

You have byobu running and you have split the screen.
Ctrl-A and then you type
```
:resize 110
```

It took me a while to to see the :, but it is needed.

Correct, Ctrl-A then : puts byobu in command mode, then you type resize.

Typing resize at the bash prompt is something else.

---

