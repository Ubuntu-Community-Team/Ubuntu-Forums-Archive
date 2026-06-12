---
title: "Where did it install to?"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by Von-Dyke on 2009-03-07
Just ran the line;
sudo apt-get mednafen

It installed but where is it? How do i access it?

---

### Post by Rolcol on 2009-03-07
If the program is GUI based, it should show up in your Applications menu.  If it isn't, you can probably run it from the command-line by typing "mednafen".

---

### Post by lindsay7 on 2009-03-07
try usr/bin. When you find the start command, you can right click on application, edit menu, and add it to the menu list you want. Just fill in the boxes with what you want and the start command.

---

### Post by ekaqu on 2009-03-07
> **Rolcol said:**
> If the program is GUI based, it should show up in your Applications menu.  If it isn't, you can probably run it from the command-line by typing "mednafen".

like rolcol said, both ways should allow you to run the program.

If you still need to know where it is and the command to run the program is mednafen, then type whereis mednafen.  it will show every place the file is at.

---

### Post by Von-Dyke on 2009-03-07
Thanks guys.
I ran 'mednafen' in the terminal, found its location then realised that it doesn't just boot up by itself; it needs a rom file to load.
So i changed the startup application of a .zip to mednafen, opened it and voila; the emulation runs.

---

