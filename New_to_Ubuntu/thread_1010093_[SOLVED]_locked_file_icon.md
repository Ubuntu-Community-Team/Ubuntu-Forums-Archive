---
title: "[SOLVED] locked file icon"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by jesse c on 2008-12-13
I have an icon of a file labeled 'driver' with a closed lock superimposed on it on my desktop.It showed up when i was messing with trying to open a downloaded driver file.I got the file another way but want to know what this means and how to remove it.It wont go to trash like other icons

---

### Post by Paqman on 2008-12-13
Take a look at the permission of the file. You'll see that you aren't the owner and/or don't have the right permissions to change it.

To get rid of it open Nautilus as root with this command:
```
gksu nautilus ~/Desktop
```

Then delete it like normal. Make sure you close this version of Nautilus when you're done.

There's also an easy way to delete it from the command line, but it's a command that can cause a lot of damage if you get it wrong.

---

### Post by jesse c on 2008-12-13
thaks paqman is there anything i have to do to 'close out this nautulus' other than exiting the terminal screen?

---

### Post by Paqman on 2008-12-13
> **jesse c said:**
> thaks paqman is there anything i have to do to 'close out this nautulus' other than exiting the terminal screen?

You don't even need to do that, just click on the close button of your Nautilus window.

For single commands you don't necessarily need to use a terminal to launch them, either. You can just Alt-F2 and type it in. The main disadvantage of this is that you can't use tab to autocomplete file names.

---

