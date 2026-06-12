---
title: "what to do in case of a computer crash/freeze?"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by sallam on 2010-10-09
Greetings

In Win7, when a computer freezes, we press Alt+Ctrl+Del buttons.
Is there a similar shortcut in ubuntu to use when a crash/freeze prevents us from clicking any menu or sometimes even moving the mouse?

---

### Post by nothingspecial on 2010-10-09
To cleanly reboot your computer hold down Alt+SysRq

And press in this order

REISUB

---

### Post by sallam on 2010-10-09
Is there no way to bring up system monitor, to switch off the problematic application?

ps. Alt+SysRq didn't seem to do a thing..

---

### Post by bipin0013 on 2010-10-09
try alt+ctrl+F3. you get into virtual console,which is same as terminal.then type sudo halt..system should shutdown..to get out of virtual console alt+ctrl+F7..

---

### Post by nothingspecial on 2010-10-09
> **sallam said:**
> Is there no way to bring up system monitor, to switch off the problematic application?

ps. Alt+SysRq didn't seem to do a thing..

You have to Hold down both Alt and sysrq and while doing so press those 6 keys in the correct order.

Further to the post above, Ctrl  Alt F3 together

Then log in

type ```
top
```

The probamatic process will likely be at the top, look at it`s pid on the left hand side

type ```
kill pid
``` where pid is the number.

If you know what the probamatic process is then open a terminal and type ```
killall process
``` where process is the name of the process eg  ```
killall firefox
```

---

### Post by ulissipus on 2010-10-10
Alt + Sysrq = save screenshot screen.

In my case, at least.

---

### Post by sallam on 2010-10-10
> **nothingspecial said:**
> To cleanly reboot your computer hold down Alt+SysRq

And press in this order: REISUB
Thanks. I got it now.
How on earth are we as humans are supposed to memorize a whole essay to simply reboot?
Are we expected to actually memorize such hilarious key combinations? 
..it feels as if we are going to press them to launch the atomic bomb and put an end to planet earth :) :P when all I wanted was to simply end a single process.

---

### Post by Quackers on 2010-10-10
I wish I'd known about this long ago. It is preferable to losing your system through corruption caused by a power-button shutdown.

---

