---
title: "some questions"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by SKhan on 2010-05-16
1. how to find out the size of an ext4 partition?

2. how to see file extension of a file?

3. can we install an application in a custom folder? is yes, how?

4. can we install an application in any partition we prefer? if yes, how?

5. how to restore default keyboard shortcuts?

6. what's the path of "keyboard shortcuts" file?

---

### Post by ssj6akshat on 2010-05-16
1.System>Administration Disk Utility

2.By default it shows you,but if there is no extention then it simply can't

3.No 

4.No,This is not windows

---

### Post by baddnady23 on 2010-05-16
I don't know the answers to all of these but here is what I know:

> 1. how to find out the size of an ext4 partition?


In the terminal, type:  ```
df -h
```

This will give you the size of your partitions. 


> 2. how to see file extension of a file?

Doesn't it show you after the name of the file??  Example, mypic.JPG

> 3. can we install an application in a custom folder? is yes, how?

I believe so, I just don't know the specifics.

As far as the keyboard shortcuts go, I know under System > Keyboard Shortcuts is where you can edit them but I don't know there the defaults are or the file in which they are stored.  Hope this little bit helps  Good luck!

---

### Post by 3rdalbum on 2010-05-16
> **SKhan said:**
> 1. how to find out the size of an ext4 partition?

System > Administration > Disk Utility

> 2. how to see file extension of a file?

That's just part of the filename and it is never hidden. Files on Linux do not need to have extensions, and many don't. If you want to know what type a file is, you can right-click it and choose Properties, or use the File command in the terminal:

```
file <drag the file into the terminal>
```

> 3. can we install an application in a custom folder? is yes, how?

Not really. Debian packages and the repositories actually specify what folder each file should go into. Everything has its place. Some programs that are distributed as "binary installers" will give you an option of where to install them, but it's not practical and not widespread, and you're probably inviting trouble by changing the directory.

> 4. can we install an application in any partition we prefer? if yes, how?

It's possible to have the /usr directory in a different partition, but it's a bit unconventional these days; I'm not convinced of any benefits there. You can have the /home directory in a different partition; there are HOWTOs online. If in doubt, don't try it.

> 5. how to restore default keyboard shortcuts?

6. what's the path of "keyboard shortcuts" file?

I'm not sure exactly what you mean - if you mean System > Preferences > Keyboard Shortcuts, the settings appear to be in Gconf. Gconf is sort of like the Windows registry in its format, but it's just a way of storing settings. You can take a look at the Gconf; hit Alt-F2 and type:

```
gconf-editor
```

The settings for keyboard shortcuts are under /apps/gnome-settings-daemon/keybindings, but I don't know how to put them back to defaults sorry.

---

### Post by HermanAB on 2010-05-16
Howdy,

Yes you can install stuff anywhere you want, but it is not recommended. Stuff supplied by the distro house normally goes into /usr/bin and stuff installed by the user goes into /usr/local.  Some systems like to install stuff in /opt.  This is defined by the Linux Standards Base (LSB).

If you really need to put a program in a special place, simply copy it there and make it executable.

---

### Post by SKhan on 2010-05-16
Thank you guys.
Here are some clarifications for the questions asked above. I hope this will make you understand my problem more precisely.

1. disk utility only tells the size of partitions. I also want to know how much free space is there in an ext4 partition.

2. Ok ubuntu shows me extensions, but i want to find out the exact location of Opera browser.
If i open terminal and type "locate opera", it shows a lot of results.
While typing "locate opera.exe" in terminal doesn't show any result. which means that opera browser doesn't have .exe exntension under ubuntu. So the actual problem is "how to locate opera browser?"


3 & 4. I was just wondering If we can't install programs to prefered folder or partition then what will happen if the default partition doesn't have any free space? Although personally i don't want to install a program on a custom location.

4 & 5. I know "keybaord shortcuts" are under system > preferences > keyboard shortcuts
but i actually want to backup my custom shortcuts for future use that's why i asked for the path. and i also want to know, how to restore default shortcuts if anything goes wrong while editing default shortcuts. In fact i have edited default keyboard shortcuts but now i want to restore the defaults.

---

