---
title: "Enter extended characters"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by pmooney78 on 2008-12-29
I've been using Xubuntu for a while now and love it ... I practically never boot Windows anymore. But there are a few skills that I haven't yet mapped over to Ubuntu. One is the ability to easily enter characters not on my keyboard. On Windows, I could just hold down the Alt key and type a four-digit hexadecimal code for the character.

Is there an Ubuntu equivalent? I'm tired of copying and pasting characters from the character map.

---

### Post by Michael.Godawski on 2008-12-29
Try this:


[LIST=1]
[*]press and hold down Shift and Ctrl together
[*]type in u, followed by the four-character unicode value for the character
[*]release Shift and Ctrl
[*]½˜&#30805;&#17715;, it is working for me.
[/LIST]

---

### Post by pmooney78 on 2009-01-19
Sorry, doesn't work for me. Nothing happens when I try to type CTRL+SHIFT + u + 4-digit code (hexadecimal, I assume? from the character map?), although some programs (OpenOffice.org word processor, f'r instance) intercept the ctrl + character combinations.

---

### Post by casperl on 2009-03-10
(Subscribing to this thread)

I have been searching for a solution to this for years and years.

There is a very effective mechanism for entering extended characters in Ubuntu/Gnome.  However, the same functionality does not seem to exist in Xubuntu.

Does anyone know?

---

### Post by casperl on 2009-03-12
Success! :popcorn:

I had an earlier post concerning compose keys as used in Ubuntu:

[http://ubuntuforums.org/showthread.php?t=296087](http://ubuntuforums.org/showthread.php?t=296087)

Unfortunately, many weeks after I stopped viewing that thread, a mistake was pointed out in my /etc/X11/xorg.conf file and until yesterday, I never returned to view that reply.  <eating humble crow - :( >

Here is my /etc/X11/xorg.conf file that does work for entering (some) characters not on the keyboard:
```

Section "InputDevice"
        Identifier "Generic Keyboard" 
        Driver "kbd"
        Option "CoreKeyboard"
        Option "XkbRules" "xorg"
        Option "XkbModel" "pc105"
        Option "XKbLayout" "us"
        Option "XkbOptions" "lv3:ralt_switch,compose:lwin"
EndSection

```
In a terminal, first make a backup of your working xorg.conf with: 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

Edit your present xorg.conf file with:

sudo mousepad /etc/X11/xorg.conf

The "inputdevice" section displayed above works though you may already have parameters that differ.  Apply the changes, save the file and restart XFCE (logging out and back in should do the trick, a system restart will also work.)

In the case of the above setup pressing the following keys in succession: <**left-windows-key**> <**"**> <**e**> returns the **ë** character. (That is the "compose key", the left-windows-key followed by a " and an e keysroke.  While this probably only provides access to acceneted characters and not the full character set as in Windows, this is exactly what I need for often used characters such as ë ö ô ô è é &#324; ï ½ &#8531; ¾ 

As pointed out in the thread referenced above, alternate compose keys may be used such as  ralt, rwin, lwin, caps etc.

---

