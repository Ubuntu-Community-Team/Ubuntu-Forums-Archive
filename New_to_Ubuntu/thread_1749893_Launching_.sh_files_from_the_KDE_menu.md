---
title: "Launching .sh files from the KDE menu"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by scared0o0rabbit on 2011-05-05
I'm having trouble getting .sh files to do anything when I add them to the KDE menu.  They work fine in the terminal, but if I add them to the menu nothing happens.  If I set it to run in a terminal this is the output I get:


Warning: Could not start program '/home/nicholas/Scripts/maptool.sh' with arguments '/home/nicholas/Scripts/maptool.sh'.

I know I haven't typo'd the name as I browsed to it.  I've tried setting the working directory to both the directory that maptool.sh is in, and to the directory it goes to before launching what it does.

Is there some trick that I don't know about to get this to work?  The contents of maptool.sh are:

```
cd ~/DnD/tools/maptool
./Launch_Maptool.sh
cd ~
```

Of course it never even fires off Launch_Maptool.sh, since it doesn't even run my script.

Any help would be greatly appreciated.

---

### Post by andrewthomas on 2011-05-05
> **scared0o0rabbit said:**
> I'm having trouble getting .sh files to do anything when I add them to the KDE menu.  They work fine in the terminal, but if I add them to the menu nothing happens.  If I set it to run in a terminal this is the output I get:


Warning: Could not start program '/home/nicholas/Scripts/maptool.sh' with arguments '/home/nicholas/Scripts/maptool.sh'.

I know I haven't typo'd the name as I browsed to it.  I've tried setting the working directory to both the directory that maptool.sh is in, and to the directory it goes to before launching what it does.

Is there some trick that I don't know about to get this to work?  The contents of maptool.sh are:

```
cd ~/DnD/tools/maptool
./Launch_Maptool.sh
cd ~
```Of course it never even fires off Launch_Maptool.sh, since it doesn't even run my script.

Any help would be greatly appreciated.Try this
```
#!/bin/bash

cd ~/DnD/tools/maptool
./Launch_Maptool.sh
cd ~
```and make sure that the file is executable.

---

### Post by scared0o0rabbit on 2011-05-05
Haha, that did it, thanks!

---

