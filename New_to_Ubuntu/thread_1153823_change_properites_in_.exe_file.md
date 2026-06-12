---
title: "change properites in .exe file"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by LTFC2020 on 2009-05-09
Hi
I want to run my Football Manager game in windowed mode, to speed it up, but when I select this option I get a message saying make sure your system supports this.  I found these instructions:

1. Make sure your screen resolution is at a minimum 1024*768.
2. Right click then on the FM shortcut on your desktop and choose "properties" from the menu that appears.
3. In the field marked "target" write this "C:\Program Files\Sports Interactive\Football Manager 2008\fm.exe" -windowed -small_screen
4. Click apply then ok.
5. Start the game via that shortcut.
6. Go the game preferences screen and under display and sound, un-check the option to play in 'full screen' mode.

But am unsure how to do this in ubuntu
Any ideas?

---

### Post by Peter09 on 2009-05-09
Just to clarify - are you using Wine to run this game?

---

### Post by LTFC2020 on 2009-05-09
yes
I`m using wine

---

### Post by 3rdalbum on 2009-05-09
The instructions are basically getting you to pass extra command-line options to the Football Manager program on startup.

I'm assuming you have the Football Manager program's launcher on your desktop or in your menu? For the menu item, you'd right click the Applications menu and go to "Edit Menus". Navigate to the location of the Football Manager launcher, click it and click "Properties".

If it's on your desktop, right-click it and go to Properties.

At the very end of the "command" field, you'll see what looks like the file path  to the actual executable. After the end of the file path but BEFORE the quotation mark, add a space and:

```
-windowed -small_screen
```

---

### Post by LTFC2020 on 2009-05-09
ok
I did what you said and added to the menu plus followed your instructions however the game still runs in full screen from the original location (not on the menu) but from the menu launcher I get the following error message:
failed to execute child process *location* (no such file or directory) 
any ideas?
thanks in advance

---

