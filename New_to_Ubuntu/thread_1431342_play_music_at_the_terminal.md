---
title: "play music at the terminal"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by computerguts on 2010-03-16
How can you open music that is stored in a directory on your computer in the terminal 
and play it?

---

### Post by era86 on 2010-03-16
> **computerguts said:**
> How can you open music that is stored in a directory on your computer in the terminal 
and play it?

You can just run the command for your media player from the terminal.  For example, if you use xmmp, you just type
```

xmmp mymusicfile.mp3

```

If you want to run a CLI media player to save on resources, check this thread here: [http://www.linux.com/archive/feature/124907](http://www.linux.com/archive/feature/124907)

I've used xmp on the CLI and it works just fine.

---

### Post by mcduck on 2010-03-16
There's plenty of command-line music players available, with different types of features. So it pretty much depends on what kind of player you want (for example do you want to run a command to play a file, or actual music player application, or perhaps some library-based music player usable from command-line).

For apps that can simply play a file you give in the command itself you can try **mplayer** or **sox**, for example. (and to run them you'd run "mplayer *nameofthefile*" or "play nameofthefile".

For actual music player made for CLI environment give **cplay** a try.

Or if you want a fill-featured library-based player you could try **MPD** with **ncmpc** as client. As a bonus the same player and library would then be usable through graphical clients on your desktop or even through network.

---

