---
title: "update killed visual eye candy in Maverick Meerkat"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by noo 2 ubun2 on 2010-12-14
What I did:

[LIST=1]
[*]downloaded 64-bit Ubuntu 10.10 from _[here]("http://www.ubuntu.com/desktop/get-ubuntu/download")_
[*]installed it (w/out the updates)
[*]right click on the desktop --> "Change Desktop Background" (can also go to System>Preferences>Appearance)
[*]go to "Visual Effects" tab
[*]select the option "Extra"
[*]click "close"
[/LIST]
:D now  the effects work as they should (ie wobbly windows and stuff)

next I perform the update (through System>Administration>Update Manager)

:confused: now the effects are broken (they are no longer working)

I retry steps 3 through to 5

:confused: here comes another problem - when I do step 5, the program ?freezes/crashes? (not sure what its called... it's like when a program "greys out" on you and won't let you select anything) [COLOR=Gray]and most of the time, does a search for drivers (usually the first time you click it, after updating) the search for drivers doesn't last long though, when it's done, it just disappears without any messages saying whether-or-not it found any or what up[/COLOR]

it's kind of like it's going to do something and you just have to wait while it attempts to resolve some issue

after a while, it reverts the choice back to "None", and is no-longer "greyed out" (I have also tried selecting "Normal", but it's just the same as clicking on "Extra")

I have done this a few times over, with the same thing happening every-time (even going so far as to do a re-download from the link at step 1)

[COLOR=DarkRed]any suggestions/fixes to this problem?[COLOR=Black]

also tried checking for further updates ...none so far :(
[/COLOR][/COLOR]

---

### Post by noo 2 ubun2 on 2010-12-14
ok so I tried selecting "Extra" again, and it worked :D... but it was short-lived :(

this time when I selected it, the whole screen changed (blinked/flashed - like when you change the resolution... it even asked to keep the changes made)

:mad: afterwards, when I went to check the settings, it had automatically reverted back to "None" again :mad:

---

### Post by noo 2 ubun2 on 2010-12-14
[U][B][COLOR=Black][SIZE=2]found the problem![/SIZE]
[/COLOR][/B][/U]
cause of bug:

[LIST=1]
[*]right click "Workspace Switcher 2.30.2" (panel applet)
[*]select "Preferences"
[*]click & hold the up arrow for "Columns" - this will change the preference box for the panel app
[/LIST]
now the visual effects break

it takes a while of (going through what I did above) clicking "Extra"

but after a while it'll eventually give in

but it will automatically change the "Workspace App" back to the way it was

[I][COLOR=DarkRed]unfortunately there is another bug - unless you don't do step 3, it is no-longer possible to click and drag things to another workspace... you have to close it and open it up from within the desired workspace

[/COLOR][/I][COLOR=DarkRed][COLOR=Black]guess you can only have one or the other?...

starting to looks like it
[/COLOR] [/COLOR]

---

### Post by noo 2 ubun2 on 2010-12-14
I'm not sure how to report bugs

...I think I'll let someone else do it (unless it gets resolved)

---

