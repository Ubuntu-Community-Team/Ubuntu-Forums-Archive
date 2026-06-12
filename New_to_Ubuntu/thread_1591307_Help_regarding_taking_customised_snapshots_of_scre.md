---
title: "Help regarding taking customised snapshots of screen"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by simar.mohar on 2010-10-09
Hi all,
I want to take customised screenshots. What I want is that after pressing a key say ctrl-alt-PrntScr I can drag with my mouse to get the required area as a snapshot and get it coppied in the clipboard as I can do in most of the PDF readers.

---

### Post by xircon on 2010-10-09
Not sure about all of what you want but I use shutter:

```
sudo apt-get install shutter
```

It does most of what you want.  You can set the hotkey up in the Gnome control panel.

---

### Post by robert shearer on 2010-10-09
You have it now.   It comes as part of the standard install.
Applications>Accessories>Take screenshot

choose 'grab after a delay of.... (2 ?) seconds'

choose "select area to grab"

'Take screenshot' will then give you a cross-cursor to select the area with.

select and when you take you finger off the mouse the screenshot is made.

In the save window select 'copy to clipboard'


Edit... well trying it in **Maverick** I can't seem to make it save to the clipboard and paste.
However,  if, when the save window opens, I hold down the left mouse button I can drag the image shown in the save window into other apps like Gimp.

---

### Post by simar.mohar on 2010-10-09
Thanks robert
I tried that but I want to have it with some shortcut key. I tried to bind a key in System>Prefrences>Keyboard Shortcuts . There adding a custom shortcut, I added the command gnome-screenshot --area --delay=2 but it does not work and the program rather takes a screenshot of the whole screen. However executing this in terminal make it work fine.

---

### Post by robert shearer on 2010-10-09
> System>Prefrences>Keyboard Shortcuts . There adding a custom shortcut, I added the command gnome-screenshot --area --delay=2 but it does not work and the program rather takes a screenshot of the whole screen. 

Edit...in keyboard shortcuts...using your command 'gnome-screenshot --area --delay=2'  I made a custom shortcut called 'screen' and set a custom key combo using shift+Print ie clicked on the right input box and pressed 'shift' and 'print' keys 

Just tried it and it works. I can take screenshot by pressing shift and print together .This brings up the cross cursor and I can use the mouse to select an area.

If you are trying to set it to use the **print key only** then you will have to disable the printscreen option that already exists in Keyboard shortcuts. That is why you can't bind the key and when you use it you get a whole screen shot. ('print' and 'alt+print' are already assigned that is why I used 'shift+print')

---

### Post by xircon on 2010-10-09
shutter --selection assigned to a hotkey definitely works.  I could not get gnome-screenshot to play ball, but did not disable the pre-existing hotkeys.

---

### Post by simar.mohar on 2010-10-09
Thanks for that

---

