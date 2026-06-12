---
title: "unr wont load page unless i drag the mouse around on it."
date: 2009-07-12
forum: New to Ubuntu
---

### Post by djmh on 2009-07-12
sorry for the confusing title, but that is really what is happening... i really like the idea of unr, so i downloaded by following these instructions.

''First, bring up a terminal window and run this command:

sudo apt-get install go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet

When you enter your password, that command will pull in various dependencies required to make UNR work. Now reboot your PC, and you should come back to a desktop that has the two largest parts of UNR working - the netbook-launcher app (the thing that now owns your desktop) and maximus, the window maximiser. But this is only the beginning of the transformation - to get the full effect, you should do the following:

   1. Remove from the top panel the Ubuntu menu (Applications/Places/System) from the left and the switch user applet from the right, plus any app launchers you don't want. Just right-click on things and choose Remove From Panel to get rid of them.
   2. Right-click on the top panel, choose Add to Panel, then add Go Home and Window Picker, moving them to the left and centre of the panel respectively.
   3. Remove the bottom panel entirely - right-click and choose Delete This Panel.
   4. Now go to System > Preferences > Appearance and choose the Human-Netbook theme.''

it works decently, enough for me to get the idea of what it is, and i really like it. but when i would go to say, my documents the page wont load completely...there will be chunks, and it will load if i grabbed say a text document and dragged it all around the screen.
that really just killed unr for me, if i have to drag something around the screen to see a folder, then its not even worth it for me.

the other thing that i noticed was when i am in my home thing, like the place that has all your launchers etc etc. there is no top bar ... the bar that would have say my firefox running, its just not there....if i drag my mouse over it it will show firefox, only to disapear again though.


i have a dell mini 9 16 gig ssd ( 4 gig free right now) intel atom .
i was testing unr on an external monitor with my netbook screen off, could that make a difference ?
other than that, i have googled and not found any solutions, or even problems like mine.

if you can help i would appreciate it , thank you !!

---

### Post by earthpigg on 2009-07-12
i just installed ubuntu-netbook-remix today on my dell mini 9, but i installed it via:

> sudo apt-get install ubuntu-netbook-remix

after installing, i had the exact same problem as you. the solution was quite simple.

alt+f2 -> and enter 'metacity --replace'

that will temporarily get you fixed.

for the permanent solution, system -> preferences -> appearance -> visual effects -> _*none*_.

if appearance does not save the settings, then try work with the borked interface and get to that menu *before* doing 'metacity --replace'.

---

### Post by djmh on 2009-07-12
wow... it must be my lucky day someone got the same problem AND solved it :)
thanks bro, i really appreciate the help.

if appearance does not save the settings, then try work with the borked interface and get to that menu before doing 'metacity --replace'.

what do you mean by that though?
are you essentially saying to just turn off visual effects ?
or something else ?

---

### Post by earthpigg on 2009-07-12
> **djmh said:**
> 
what do you mean by that though?
are you essentially saying to just turn off visual effects ?
or something else ?

yes, saying turn off visual effects. i had a minor annoyance because i turned them off via 'metacity --replace' and then tried to do it via point-and-click.... it didn't save my changes at first because i confused the issue by doing both.

had to click around a bit, but it eventually stuck :D

i reported this as a bug, if you are curious:

[https://bugs.launchpad.net/netbook-remix/+bug/398534](https://bugs.launchpad.net/netbook-remix/+bug/398534)

---

### Post by djmh on 2009-07-12
uhhhm ok, so i turned visual effects to none, and then ran meatcity --replace

and uhhh i dont have any panels now ... 
lol, i went into my home folder and was able to launch firefox ..any ideas ?

---

### Post by djmh on 2009-07-12
oh, i got them back...forgot i had terminal as a hotkey ..so i just ran metacity ...
but do you know what that was?
like, is that what was supposed to happen ?

---

### Post by djmh on 2009-07-12
well, i closed terminal and it killed my panels...and my keyboard lol.
so i restarted, and ran metacity again...but i only have my X maximize and minimize back (those were taken away along with my panels) but the panels didnt come back when i ran metacity this time.

do you have any idea what i can do ?

---

### Post by earthpigg on 2009-07-12
> **djmh said:**
> oh, i got them back...forgot i had terminal as a hotkey ..so i just ran metacity ...
but do you know what that was?
like, is that what was supposed to happen ?

no, not really... turning visual effects to 'none' does exactly the same thing as metacity --replace.

thats what i was talking about above when thinks got a little funky for me due to telling it to do the exact same thing twice, once via two different methods.

the only reason i mentioned metacity --replace at all is because, for me, it was frustrating trying to even *get* to the system -> preferences menu with things all borked up due to compiz.

if you can get to the menu via pointing and clicking *without tearing your hair out*, then that would be the preferred method.

else, metacity --replace calms the insanity down a bit and allows you to get to the menus.

---

### Post by djmh on 2009-07-12
lol, well i ran metacity --replace ...and now i have no panels 
or the exit minimize and maximize for my browser.

if i open terminal and run "metacity"
it gives me back my browsers exit minimize and maximize.
but i cant close terminal or i will lose them again.

so do you know how to get my panels back ?
and my exit maximize and minimize without having to run terminal ?

---

### Post by earthpigg on 2009-07-12
try running 'metacity' from the alt+f2 thing.

try picking a different theme from system -> pref -> appearance -> themes.

---

