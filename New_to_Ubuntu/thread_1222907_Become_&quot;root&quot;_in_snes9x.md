---
title: "Become &quot;root&quot; in snes9x"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by SPARTAN-118 on 2009-07-25
Hi,

I need to know how to enable root privileges in snes9x emulator, so I can enter fullscreen.
Actually, I use the GUI frontend (snes9express), and in the Video options menu, many options are grayed out because I'm not "the owner".

I wish it was as easy as creating an Administrator account like in Windows, and just providing permissions when applicable, but, unfortunately, it is not.

So, how to become root? I won't edit anything that might provide a security problem, but I need those privileges for many things. 
Also, I am the only user on this computer, so I don't need to worry about other people's files being corrupted or something or other. ;)

Many Terminal commands require me to be root; for example, you have to type in "sudo" to use most of the commands I use.

Is there a way to make me permanently root? Or root for some files?
Because I need to make snes9x (or the GUIs of other programs) to recognize me as root.

SPARTAN-118

PS Don't give links to the Ubuntu Help, since it is very complex.
Tell me how to give Super User permissions in a way a newbie would understand, please. :P

---

### Post by cariboo on 2009-07-25
Use sudo/gksu. Press alt-F2 and type:

```
gksu <application name>
```

> Is there a way to make me permanently root? Or root for some files?
Because I need to make snes9x (or the GUIs of other programs) to recognize me as root.

use sudo -i

---

