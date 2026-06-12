---
title: "move mouse to the corner of screen to turn off monitor"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by ioasw on 2010-01-06
I'm using mac OSX and Ubuntu Karmic and I was wondering if there is anyway to, like in mac OSX, turn off only the monitor (keeping the computer on) by moving the mouse to the one of the four corners of the screen.

I use this when I'm in class and there isn't anything to type for a few minutes.  I currently have a custom launcher with the command: xset -display :0 dpms force off, in the right corner of my screen and when I want to turn it off I just click on it.  It works, but I would like to just move my mouse there without clicking, thanks for any feedback.

---

### Post by b0b138 on 2010-01-06
If you don't have it installed already, install compizconfig-settings-manager


Then, under general -> commands -> tab that says edge bindings

---

### Post by b0b138 on 2010-01-06
lol had to play with it myself since I didn't know it was there till I looked for it.

wow...its very time sensitive. Make your command ```
sleep 5 && xset -display :0 dpms force off
```


hmmm...well thats not working out very well either. If I move my mouse to the edge then go back to business, it still runs the whole command making the screen flicker.

---

### Post by Jenkins1 on 2010-01-06
Thanks so cool I am glad I stumbled across this thread.:) Screen flicker here as well.

---

### Post by ioasw on 2010-01-06
When I try to insert your command b0b138 I get the error: "not a valid edge mask"  what am I doing wrong?

---

### Post by b0b138 on 2010-01-06
The command goes on the first tab.1 tab has command, 2nd tab has key binding, 3rd mouse bindings, 4th tab screen bindings. 3 crazy ways to run some crazy command ie. 6 keys to "purge" the system ;)

---

### Post by ioasw on 2010-01-07
I got it.  I'm on a macbook pro 5.5 and with your command I don't get any flicker but the screen just turns back on blank after about 10 seconds as with my custom button.  I guess this is still pretty glitchy.  Thanks for the help though.

---

### Post by Jenkins1 on 2010-01-09
The flicker only happens if you leave the mouse in the corner of the screen. If you put the mouse in the corner and then take it out before the time out the flicker doesn't happen.

---

