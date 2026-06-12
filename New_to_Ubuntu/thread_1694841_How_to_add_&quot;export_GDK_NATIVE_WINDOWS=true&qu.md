---
title: "How to add &quot;export GDK_NATIVE_WINDOWS=true&quot; into eclipse"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by 1dbzfanjake on 2011-02-24
I'm new to Ubuntu and coding in general, so sorry for this probably basic coding question. I am trying to play Minecraft on my computer and the keyboard buttons won't work. So I google, and found this thread [http://ubuntuforums.org/showthread.php?t=1316071](http://ubuntuforums.org/showthread.php?t=1316071). Except, I don't know how to "add" this line of code? to a folder and have no clue what is going on. By any chance, could someone explain? Thanks for the help.

---

### Post by Perfect Storm on 2011-02-24
Make a new launcher (eventually on your Desktop or in the Applications menu).

Fill in the info (icons, name etc.). In the command box, write;
```
sh -c "cd <path to minecraft> && export GDK_NATIVE_WINDOWS=1 <minecraft launch file>"
```

an example:
sh -c "cd ~/Documents/testgame && export GDK_NATIVE_WINDOWS=1 ./testgame.sh"


But I guess you need to use **java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame** where it says <minecraft launch file>.

---

### Post by 1dbzfanjake on 2011-02-25
Thanks

---

