---
title: "Bottom task bar"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by numbness05 on 2009-01-19
I have stupidly managed to delete my bottom task bar I have been all through out the systems preferences and administration menus but am not seeing how I can restore this...

Any body have any advice in return you can have mine.....Dont leave the mouse on you lap whilst typing it may just drop off and decide to delete you task bars! 

Many thanks in advance! :)

---

### Post by emarkd on 2009-01-19
if i understand, you still have the top panel, right?  just right-click on it and select "new panel"

---

### Post by numbness05 on 2009-01-19
Ok thats great thank you but now for some reason none of the windows that I have open on my screen are displaying on the panel now I have added it..Any Idea there?

Again many thanks

---

### Post by RomeReactor on 2009-01-19
Hi. You created an empty panel; you need to add all the items that were there. You can do that like this:
```
gconftool-2 --shutdown
```
then:
```
rm -rf ~/.gconf/apps/panel
```
and lastly:
```
pkill gnome-panel
```

This will restore both panels to their defaults.

---

### Post by numbness05 on 2009-01-19
It's ok panic is over! :) I have manged to figure it out with a little perseverance.

Many thanks again Support like this does not exist in Window! :guitar:

---

### Post by mvalviar on 2009-01-19
Right click on the taskbar (otherwise known as panel) and select "Add to panel". A dialog will appear find and select "Window list". Your open windows should appear on the panel.

---

### Post by emarkd on 2009-01-19
glad we could help.  welcome to the community!

---

### Post by kneedragger on 2009-01-19
> **numbness05 said:**
> Ok thats great thank you but now for some reason none of the windows that I have open on my screen are displaying on the panel now I have added it..Any Idea there?

Again many thanks


I think I had the same problem as you yesterday. Try this..

right click on panel-> add to panel-> add window list.
 
That should show the windows your using.After trying this I ended up trying the " add window selector"

This option takes up less space on the bar. Give it a try.

---

