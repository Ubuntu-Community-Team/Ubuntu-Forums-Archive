---
title: "Why can't I open Nautilus with a keyboard shortcut?"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by zcacogp on 2010-05-18
Chaps, 

I'm hoping this is a simple one. 

I am used to Win+'e' as a shortcut to open Windows explorer. The equivalent in Ubuntu would be to map Win+'e' to open Nautilus. 

If I look in "Keyboard Shortcuts" there is no existing shortcut to open Nautilus. But I know that if I type "Nautilus" in a terminal it will open nautilus. 

So, in Keyboard Shortcuts I create a new shortcut, called "Open Nautilus", with the command being just 'nautilus' (without the 's). I map this to Win+'e', but it doesn't work. Neither does it work when I try and map it to any other key combination (or even something simple like F11 - which isn't mapped to anything else either.) 

This suggests that I am putting the command in wrongly. (Or that it is, for some reason, impossible to create a shortcut to open Nautilus - is it?) 

Any ideas where I am going wrong? 

Thanks for your help. 


Oli. 

P.S. FWIW, this is 10.4 Lucid, but I have tried this in every version of Ubuntu since 8.4, and never made it work. And I'm only asking the question now ...

---

### Post by r-senior on 2010-05-18
Try setting the command as:

```
/usr/bin/nautilus --no-desktop --browser /home/yourUsernameHere
```

---

### Post by aysiu on 2010-05-18
Not sure why ```
nautilus
``` isn't working. Could be that Win+E is already mapped to something else (like Expose)--you might want to scroll through the list of existing keyboard shortcuts to make sure it isn't already taken.

**Edit**: I double-checked. It's not in System > Preferences > Keyboard Shortcuts.

You have to Alt-F2 and then ```
gconf-editor
``` and then go to the Compiz settings to get rid of the Expo keyboard shortcut.

---

### Post by zcacogp on 2010-05-18
r-senior, 

Thanks. That worked. (Out of interest, why didn't it work with just "nautilus"?) 

I say it worked; but I don't understand why. There is another keyboard shortcut listed called "Home Folder", but that has never worked, despite having the same key combination set for it. Now that I added the command you gave me to the list of custom shortcuts, with the same key combination listed for both (that is, for both the "Home Folder" one and the custom "Run Nautilus" one), it opened two Nautilus windows at the same time. 

Thinking this may be because the same key combination called two sets of commands, I have removed the custom shortcut, leaving just the original "Home Folder" one, which now works perfectly. 

Why is this? Why does one shortcut that has never worked spring into life when another shortcut is changed, and then carry on working when the second shortcut is then deleted? 

(Did this explanation and question make a shred of sense? :( )

Thanks again for your help. 


Oli.

---

### Post by zcacogp on 2010-05-18
Aysiu, 

You posted while I was typing ... 

Yes, I figured out the conflicting shortcuts thing - I did have that key combination set up for Expo, but removed it before I started playing around with it. 

I didn't know you could change things in gconf-editor tho', so thanks for that. (gconf-editor seems new to me; was it around in earlier versions of Ubuntu?) 

Thanks for your input. 


Oli.

---

### Post by r-senior on 2010-05-18
It could be related to this ... (start reading from the bottom upwards)

[https://bugs.launchpad.net/do/+bug/387723]("https://bugs.launchpad.net/do/+bug/387723")

I didn't just dream up that command you know chaps! ;) I had to make a similar change to get the home folder to come up with gnome-do. In that case I changed /usr/share/applications/nautilus-home.desktop as described in the bug report.

---

### Post by zcacogp on 2010-05-18
Hmmm. Not quite sure that I follow all that. But >SticksHeadInSand< I'm happy that my system now works as it should - thanks. 

(Now works as I want it too ... solved in 30 seconds after having suffered for 2 years! The number of times I have pressed Win+'e' on one of my Ubuntu machines and quietly cursed it ... but I'm happy now!) 

Thanks again. 


Oli.

---

### Post by ruhtranayr on 2010-06-01
Hey thanks for the tip!

I was using thunar instead but was having some issues... I like to set filebrowser to alt+z and terminal to alt+x

And I usually set firefox to WindowsKey + f

Makes life easier :) Thanks again

:guitar:

---

