---
title: "Keyboard layout switching ?"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by Triple-H on 2011-08-23
Hello,

I installed Xubuntu 11.04 on my desktop PC, and I have two keyboard layouts [languages] that I need to switch every now and then.

I can't find an option to set a keyboard shortcut to do so, and I can't find the layout switcher icon in the status bar.

Please help!

Thanks :)

---

### Post by Triple-H on 2011-08-23
Updates:
I installed a random app from the package manager to switch keyboard layouts, and then I could add an icon to the top panel that switches languages.

However, I still can't figure out how to set a custom keyboard shortcut to do the job

---

### Post by papibe on 2011-08-23
I have two keyboards layouts too. There's a default shortcut to change keyboards but I don't remember it. Any way, you can set it up to the commonly know Windows shortcut Alt-Shift this way:

Open Keyboard Preferences. Go to the Layout tab. Press 'Options'. Look in the list presented for 'Key(s) to change the layout'. Open that option by clicking on the plus symbol. There, they are predefined shortcuts you can choose. Check it, and you're ready to go.

Hope it helps,
Regards.

---

### Post by Triple-H on 2011-08-23
That solved it! 

Thanks a lot!

---

### Post by Ashraf_2003 on 2011-09-04
don't have options button in the layout tab ????

---

### Post by lykeion on 2011-09-04
What Ubuntu version are you running? 10.04 do have an Options button (see screenshot)

Okay, I missed this is a Xubuntu-specific issue: This might solve it: [http://ubuntuforums.org/showthread.php?t=1098848](http://ubuntuforums.org/showthread.php?t=1098848)
or you could try this: [http://superuser.com/questions/155758/how-to-change-keyboard-layout-change-shortcut-in-xubuntu](http://superuser.com/questions/155758/how-to-change-keyboard-layout-change-shortcut-in-xubuntu)

---

### Post by mikewhatever on 2011-10-06
Perhaps you guys should remove the false info including the useless screenshots, the thread comes up on the first page of Google search.

_Solution_
Oddly enough, there is no graphical way to switch keyboard layouts in Xubuntu. You need to install the panel plugin - **xfce4-xkb-plugin** - and then add it to the panel.

If you don't want the applet, but just want some ways to switch layouts, use the setxkbmap command with the desired layout, for example:

setxkbmap it (to switch to Italian)

setxkbmap pl (to switch to Polish)

It's a good idea to assign keyboard shotcuts to these commands because once you've switched out of the Latin alphabet to something like Russian, there would be no way to type them.
To set the shortcuts, open the Settings Manager from the menu, select Keyboard, Application Shotrcuts tab. Use Super+1, Super+2, etc.

---

