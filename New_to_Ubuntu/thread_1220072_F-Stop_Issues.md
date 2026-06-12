---
title: "F-Stop Issues"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Kidzndogz on 2009-07-22
I am completely green here and not a computer geek at all just so you know from where I come! I just downloaded Ubuntu two days ago, I have had several problems with f-stop. First it will freeze for no apparent reason, it's done this several times and never while doing the same task, very random. How to fix this, and how do I get out of it when it happens? The only thing I can do is shut the computer off as no commands work nor does the mouse. 

Second when using the soften application I can't seem to get it to move to any specific area in the photo. No matter what I do the center is always clear and the rest blurred. I can't make the clear part larger/smaller nor can I move it to a different part of the photo to focus on another area. 

There....sorry if I'm too wordy:-s

---

### Post by Stebalien on 2009-07-22
First, instead of just holding down the power button, try pressing '<alt><Print Screen>k'. This will kill the X server and put you back at the login screen. If that fails to work:
> Hold down the Alt and SysRq (Print Screen) keys. 2. While holding those down, type the following in order. Nothing will appear to happen until the last letter is pressed: REISUB 3. Watch your computer reboot magically.  --fosswire

Second, F-Spot does not let you change the blur center for a soft focus.

Third, the crashing is probably a [mono]("http://en.wikipedia.org/wiki/Mono_%28software%29") problem (f-spot uses mono) and is most likely hardware specific. I would just use a different photo manager (In my opinion, f-spot really sucks). Alternative photo managers are digikam (for KDE but works in gnome) and Google's Picasa (Closed Source). You can also use gthumb to organize photos but it is less powerful.

---

### Post by directhex on 2009-07-22
Which version of Ubuntu is this?

---

### Post by mjheagle8 on 2009-07-22
if you try running F-Spot from the terminal, you can see if it produces any errors that you can search for to find a solution. also, as stebalian said, it is much more efficient to simply restart the X server instead of restarting the computer.

---

### Post by sandyd on 2009-07-22
Can you do this?
the info given by doing this might be meaningless to you, but we might be able to fix it from this info

Go to Applications -> Accessories -> Terminal

type this in
```

f-spot

```

F-spot will then start. Use it until it freezes.
Then go to the terminal, and copy out the entire thing, from bening to end.

---

