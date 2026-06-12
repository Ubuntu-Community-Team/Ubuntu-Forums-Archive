---
title: "Can't minimize fullscreen game"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by robro on 2011-01-28
Hello,
I play a game called teeworlds but i can't minimize it in Ubuntu. in windows i could Ctrl + escape. i have tried to start a new x session and start the game from there but its a network game and when i switch to the home(?) session it disconnect after 10 seconds. i have tried using etswitch but i cant get the thing to compile, i have tried to use all the shortcuts i could find but still no luck, i really need help i love this game but i want to be able to check things like my email.

---

### Post by davidmohammed on 2011-01-28
try CTRL+ALT+D

---

### Post by robro on 2011-01-28
Nope that dosnt work ether :(

---

### Post by davidmohammed on 2011-01-28
are you using maverick?  Try Windoze key + D

Have a look at Preferences - Keyboard Shortcuts

look at the list - I think the one you want is "Hide all normal windows and give focus to desktop"

---

### Post by robro on 2011-01-28
windows + D doesn't work ether although it works great for minimizing everything else (non fullscreen)

---

### Post by davidmohammed on 2011-01-29
ok,
  the following is not pretty - but it works for me

1. Use the Me Menu to switch to a "Guest Session" and run your full screen game from there.
2. When you want to switch back to your desktop - CTRL + ALT + F7.
3. When you want to switch back to you guest session - CTRL + ALT + F8


****** just re-read your first post - you had already tried that 

in that case - I'm out of ideas ******

---

### Post by davidmohammed on 2011-01-29
just reading around.

The key issue is that the standard network manager requires an X-session to run - as you have found - switching X-sessions, breaks that connection.

An alternative is wicd - what I read, is that is should be able to configure wicd to connect even if there is no X-session.  To my mind, I would read that to mean, it is possible to use the same connection between sessions.

I dont have another test computer to figure this out the instructions for you  - hope that gives you something to investigate further.

---

### Post by robro on 2011-01-29
Thanks for the info,
I have installed wicd but it doesn't let me connect :(
*sigh* well i'm too tired to investigate this right now ill try again later and see what i can find out.

---

### Post by robro on 2011-02-04
I have been trying to get wicd to let me connect,
I have a Verizon usb760 modem,
i dont have much internet experience in terms of how it works and etc.

one problem leads to another *sigh*

---

### Post by robro on 2011-02-05
I googled a bit and found out that wicd doesn't support the exact type of internet connection i have :evil:

is there anything else that can support what i need?

---

### Post by davidmohammed on 2011-02-05
Have you come across this [thread]("http://ubuntuforums.org/showthread.php?t=1002262&highlight=verizon+usb760")?

---

### Post by robro on 2011-02-07
> **davidmohammed said:**
> Have you come across this [thread]("http://ubuntuforums.org/showthread.php?t=1002262&highlight=verizon+usb760")?
erm... that has nothing to do with being able to connect with wicd, does it?

---

### Post by davidmohammed on 2011-02-07
> **robro said:**
> erm... that has nothing to do with being able to connect with wicd, does it?

... absolutely true! - was a response to another thread. Sorry.

Any luck with this issue?

---

### Post by robro on 2011-02-07
Nope -_-
Y U NO MINIMIZE!!!

---

### Post by davidmohammed on 2011-02-07
hmmm ... maybe [this thread]("http://regnumonlinegame.com/forum/showthread.php?t=22211") could help - basically fooling the fullscreen game to run in windowed mode.  In that way you should be able to use shortcut keys such as discussed previously, or short-cut keys such as CTRL+ALT + LEFT/RIGHT ARROW to move between different workspaces.

---

### Post by robro on 2011-02-07
Thank you! that worked great :)

---

### Post by robro on 2011-02-13
Well after playing around for a few days i have noticed that if i quickly move my mouse up or down it takes focus off of the game and on to the panel :|

Any help on this? :(

---

### Post by robro on 2011-02-13
Well after playing around for a few days i have noticed that if i quickly move my mouse up or down it takes focus off of the game and on to the panel :|

Any help on this? :(

edit: idk how i triple posted :|

---

### Post by robro on 2011-02-13
Well after playing around for a few days i have noticed that if i quickly move my mouse up or down it takes focus off of the game and on to the panel :|

Any help on this? :(

---

### Post by robro on 2011-02-13
Well after playing around for a few days i have noticed that if i quickly move my mouse up or down it takes focus off of the game and on to the panel :|

Any help on this? :(

---

### Post by robro on 2011-02-14
bump

---

### Post by JKyleOKC on 2011-02-14
Best start a new thread to ask about the new problem. Once you're marked the thread as "solved" most folk will skip over it unless they are having the same kind of problem described by the thread title.

---

### Post by robro on 2011-03-30
[angry]
ok after about 2-3 weeks of kubuntu I can't stand it anymore!
I love gnome and it dosn't look like windows with some crappy special effects :evil:
but kubuntu with the settings "keep above others", "no border" and for the panel: "windows can cover" work perfectly with what I want to do, i'm about ready to nuke my computer :evil:
[/angry]

although I have come across someone saying theres a patch for sdl to not grab alt+tab,
so that I can switch back and forth to another program, though sadly I cant seem to locate it :(

so once again please if someone has any ideas at all please post them :cry:

---

### Post by robro on 2011-03-30
FINALLY! I figured it out! the problem was compiz so now all I have to do is disable compiz when I play :D

---

