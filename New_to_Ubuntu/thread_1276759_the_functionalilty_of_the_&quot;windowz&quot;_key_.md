---
title: "the functionalilty of the &quot;windowz&quot; key in my laptop..."
date: 2009-09-27
forum: New to Ubuntu
---

### Post by heyyy on 2009-09-27
im just curius if there's a function of the "windowz" key on my keyboard?

---

### Post by LewRockwell on 2009-09-27
[http://lifehacker.com/software/how-to/configure-custom-keyboard-shortcuts-on-ubuntu-256955.php](http://lifehacker.com/software/how-to/configure-custom-keyboard-shortcuts-on-ubuntu-256955.php)

.

---

### Post by Schendje on 2009-09-27
On Ubuntu it's called the "Super" key. You can use it for shortcuts, for instance Super+Tab on my machine gives me Compiz's window chooser.

---

### Post by drs305 on 2009-09-27
LewRockwell gave you a link that discusses the gconf-editor. You can use it to set key/command combinations. 

From the command line, it can be as simple as running these two commands. This example sets the left Super key (windows) to open gedit. 
Note: There are 12 default keybindings available. You might want to open gconf-editor (see last command in this post) to check if any are entered in Command 10 before running these.

```

gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_10 "gedit"
gconftool-2 --set --type string /apps/metacity/global_keybindings/run_command_10 "Super_L"

```

To actually see what is already assigned to keys, you can run this to open gconf-editor to the appropriate location:
```

gconf-editor /apps/metacity/global_keybindings

```
You assign the key to "global_keybindings" and the command to execute to "keybinding_commands".

---

