---
title: "Basic Console Tutorials?"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by fallofshadows on 2011-03-05
Hey folks,

I've been using linux for a few months now, and I've realized that I still haven't learned much about the console. I would love to learn to use it more, but I can't find any good tutorials/beginner guides for learning stuff you can do with it. Can anyone help?

I realize the console isn't technically needed, but I love the power that you have with it (isn't that the point of linux? : D) so I really want to learn to use it more, in particular for working with .tar files (I'm still hate them) or setting up keyboard shortcuts that correspond the console commands.

Thanks!

---

### Post by mikewhatever on 2011-03-05
Here you go.
[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)

---

### Post by ksprasad on 2011-03-05
Hi,

 I found the below link as a good one.
 
 [http://info.ee.surrey.ac.uk/Teaching/Unix/](http://info.ee.surrey.ac.uk/Teaching/Unix/)

Regards,
ksprasad

---

### Post by oldos2er on 2011-03-05
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[http://ss64.com/bash/](http://ss64.com/bash/)

---

### Post by towheedm on 2011-03-05
This IMHO is great for starters:

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Then there's the bash reference manual at:

[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

---

### Post by fallofshadows on 2011-03-11
Thanks guys for all the support, I've learned a lot over the last few days. The fact that I can control files and directories without ever clicking on them thrills me for some reason...

One more question: Does anyone have any idea how I would go about writing a script that changes an option in a window? Like, I usually click on keyboard preferences>keystroke repeats if key is held and then close the window. I'd love to assign this a quick keyboard shortcut to toggle this option, but I have no idea what the script would be.

Thanks again for all the help!

---

### Post by towheedm on 2011-03-17
There is no need to create a script file to do this.  This can be done by creating a keybinding that toggles the key repeat.

The key-repeat value is stored in the **/desktop/gnome/peripherals/keyboard/repeat** key of the gconf database.  The value can be toggled with the command:
```

gconftool-2 --toggle /desktop/gnome/peripherals/keyboard/repeat
```Now all you need to do is bind a key to this command.  Since you enjoy using the command line, enter these 3 commands in your terminal.

Create an entry in the gconf database for the binding and name it **Toggle Key Repeat**:
```
gconftool-2 --type string --set /desktop/gnome/keybindings/repeat/name "Toggle Key Repeat"
```Now assign the first line of code above to the binding:
```
gconftool-2 --type string --set /desktop/gnome/keybindings/repeat/action "gconftool-2 --toggle /desktop/gnome/peripherals/keyboard/repeat"
```Finally, bind a key to it.  Let's say we will use Control-R:
```
gconftool-2 --type string --set /desktop/gnome/keybindings/repeat/binding "<Control>r"
```You can test it by opening the Keyboard Preferences and pressing the Control-R key.  Every keypress should toggle the repeat checkbox.

You can also checkout the keybinding by opening the Keynoard Shorcuts and scrolling down to custom.  It should be listed there.

Hope this helps.

---

### Post by fallofshadows on 2011-03-19
Hey, thanks for that. I've run into a problem though.

I entered the code you listed, except I changed "<Control>r" to "<Control><Super>"

It messed with my appearance settings though, taking away my Macbuntu icons. I tried to change it back, but it displays this warning before opening up the appearance manager...

"Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with DBus, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."

How do I fix this? I'd like to use the themes I like, rather than the one it jumped to...

EDIT: Fixed this problem by setting the keyboard command to Control+r instead of Control+Super. Apparently gconfig dislikes it when you just use that combo... I figured I'd keep this up for documentation though, it seems like a pretty unique problem haha.

---

### Post by towheedm on 2011-03-19
Possibly <Control><Super>r was already assigned by some other app, maybe compiz?  Also, the order of <Shift>, <Control> and <Super> are important.  For example:  Assign Shift-Control-r must be <Shift><Control>r and not <Control><Shift>r.

---

### Post by fallofshadows on 2011-03-24
I think my problem was that I didn't use <Control><Super>r, but rather I left out the R. I think using pure command keys like that was what made it upset :P

---

