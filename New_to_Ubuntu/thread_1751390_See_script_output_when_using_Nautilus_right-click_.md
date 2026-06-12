---
title: "See script output when using Nautilus right-click custom-command"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by curbuntuforums on 2011-05-06
Hi,
If I run my script from the Nautilus right-click 'custom command' line I don't see it run in a terminal window.  Adding a pause command in the script doesn't help.

Same script works as drag-n-drop-zone if I make a Gnome panel custom application launcher with "Type: Application in Terminal" vs "Application"... but that's not what I'm after.

This is a newb's first script - so please be gentle and explain "as you would a child"...
:wink:

---

### Post by curbuntuforums on 2011-05-06
ah ha 
use this format for Nautilus "right-click custom command"-line
```
gnome-terminal -x /path/to/your/bash.sh
```and you'll get your window.
[SIZE=1]
[/SIZE]

---

