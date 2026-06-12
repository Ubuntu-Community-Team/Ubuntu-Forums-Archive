---
title: "shortcut to open a terminal"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by sallam on 2010-10-16
Greetings

What is the shortcut to open a terminal please?
And if I'm pressing that shortcut while I'm in a specific folder, does it start in that path?

---

### Post by Joshwaa on 2010-10-16
I'm not the most experienced Ubuntu user, but you can always add the Terminal to your top Panel which contains your menu etc.
Just go to Applications, go to Accessories and right click the terminal and click Add To Panel.
This doesn't start the terminal in the current directory opened but you can always do a quick cd (extremely powerful, relative and absolute).

---

### Post by sallam on 2010-10-16
Just found it:
System > Preferences > keyboard shortcuts
run a terminal: Ctrl+Alt+t

But it opens with no path to where I was when I launched it..
How to do that please, without having to type the path?

edit:
Thanks Joshwaa, we posted at the same time.

---

### Post by MooPi on 2010-10-16
Try this terminal ```
sudo apt-get install nautilus-open-terminal
```

---

### Post by ubunterooster on 2010-10-16
> **MooPi said:**
> Try this terminal ```
sudo apt-get install nautilus-open-terminal
```
[s]What's that do?[/s]

Edit:  D'oh; I use it all the time

*facepalm*

---

### Post by sallam on 2010-10-16
> **MooPi said:**
> Try this terminal ```
sudo apt-get install nautilus-open-terminal
```Thanks. Is that another terminal tool? what advantage do I get from it please? Does it open in the path it was opened from?

---

### Post by ubunterooster on 2010-10-16
> **sallam said:**
> Thanks. Is that another terminal tool? what  advantage do I get from it please? Does it open in the path it was  opened from?
You can right-click a folder and it gives the option to "open terminal here"

---

### Post by asmoore82 on 2010-10-16
Big +1 for "nautilus-open-terminal"

After installing it, you have to log out and back in for it to take effect.

OR, you can run `xkill` and click the desktop or a nautilus window.
nautilus will close and automatically restart.

---

### Post by Isyaltut on 2010-10-17
> **asmoore82 said:**
> Big +1 for "nautilus-open-terminal"

After installing it, you have to log out and back in for it to take effect.

OR, you can run `xkill` and click the desktop or a nautilus window.
nautilus will close and automatically restart.

Or you just can type nautilus -q in terminal to restart only nautlus, no need to log out.

---

