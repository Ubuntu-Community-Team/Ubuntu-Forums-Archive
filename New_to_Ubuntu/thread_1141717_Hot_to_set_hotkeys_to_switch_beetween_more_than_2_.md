---
title: "Hot to set hotkeys to switch beetween more than 2 workspaces ?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by rizork on 2009-04-28
Hello! I am user on Ubuntu 9.04 machine.

I'd like to switch between workspaces using hotkeys and I am using minimum 4 workspaces constantly. I've checked "Keyboard hotkeys" preferences but unfortunately there is only options to set hotkeys for 2 workspaces. 

My questions is how to add more workspaces there for hotkeys?

ctl+alt+arrow not an option I want to switch fastly.

Regards.

---

### Post by Tibuda on 2009-04-28
Yes. Have you installed compizconfig-settings-manager? If so, you have a "Desktop effects" entry in your system menu, where you can edit the shortcuts.

---

### Post by rizork on 2009-04-29
No, unfortunately I have not  compizconfig-settings-manager installed. And I am not admin, I don't have access to root account. 
Is there any other way to add keyboard shortcuts to switch between workspaces ?

---

### Post by kanikilu on 2009-04-29
Not sure if this is what you are looking for, but, [this post]("http://ubuntuforums.org/showpost.php?p=3561425&postcount=6") suggests a program called **wmctrl**.

I've never used it, so can't personally say if it will work or not, but if it does work, then I think you could assign a new keyboard shortcut to the command to switch to a specific workspace...

// Edit - I just tried wmctrl and it works fine in XFCE, so I imagine it will work in Gnome...

---

### Post by rizork on 2009-04-29
it seems I don't have wmctrl installed either

wmctrl -s 1
The program 'wmctrl' is currently not installed.  To run 'wmctrl' please ask your administrator to install the package 'wmctrl'

thanks for trying to help BTW

---

### Post by rdjack21 on 2009-05-01
You can do this without installing any additional software. I like you prefer to hot key switch between workspaces so I figured this out a while back. 

1) you must enable 'Configuration Editor' 
1.1) System->Preferences->Main Menu
1.2) In the new window select System Tools then check the checkbox next to 'Configuration Editor'
1.3) Close the Menu editor 

2) Applications->System Tools->Configuration Editor
NOTE: The stuff below is for the tree control in the left pane of the Configuration Editor
2.1) apps->metacity->global_keybindings
2.2) In the right hand pane you will now see your current key bindings for the window manager scroll down and find the ones labeled switch_to_workspace_? where ? is the workspace number counting from left to right down left to right. So for instance lets say you have setup your switcher to have 4 workspaces as a 2x2 box. Then the workspace numbers would be:

| 1 | 2 |
---------
| 3 | 4 |

So to assign the key for workspace 1 find 'switch_to_workspace_1'. Then click on the text that will either say 'disabled' or your current hot key. This will allow you to edit it. The pain part is that you have to enter the key name for your hot key. So for instance I have mine setup to be F9, F10, F11, F12 so I would enter F9 for 'switch_to_workspace_1' for key modifiers use <Super> <Control> <Alt> then the key name. You should be able to figure out the names for most of the keys as they are pretty intuitive. Once you have your hot keys set the way you want just exit the application. Also these Hot keys go into effect as soon as you hit enter on the field you are editing so you can test your hot keys as soon as you set them to make sure they are right. 

EDIT: Oh forgot to add you can do this with out sudo rights as long as your admin has not removed the Configuration Editor tool. Which they should not have done. The Configuration Editor tool allows you to edit your preferences only. Also don't go mucking around in other areas unless you read up on what you are changing as you can screw up your desktop playing around with this tool.

---

### Post by words1 on 2009-05-01
None of this should be necessary.  I just upgraded from 8.04, and I'm sorry I did.  In 8.04, you can assign at least four key shortcuts, and show only the current desktop in the taskbar.  This is the kind of nonsense "improvement" that really ticks me off.

---

### Post by rdjack21 on 2009-05-02
Actually this was changed in 8.10 that was when I first encountered it. And it is most likely a gnome regression.

---

### Post by rizork on 2009-05-02
**rdjack21**
Thanks for providing detailed instruction. It works!

---

### Post by mdhicks1 on 2009-07-06
Actually, I'm running a fresh install of Jaunty and mine works by pressing Ctrl+Alt+(left/right arrow key).

Didn't have to install a thing.

---

