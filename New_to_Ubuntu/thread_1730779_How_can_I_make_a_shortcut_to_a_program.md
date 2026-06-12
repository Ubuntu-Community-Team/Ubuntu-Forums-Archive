---
title: "How can I make a shortcut to a program?"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by pete20r2 on 2011-04-16
I am relatively new to Ubuntu, but i know my way around.
I recently installed a .deb package of a program called linaxepad, It's a utility for programming picaxe chips. The problem is that I have to start it with the terminal every time because it did not make a link in the applications section. I know the executable resides at /usr/apps and is in fact the only thing in /usr/apps.
How can I generate the link or entry required to make it appear as any other application would, in the menu, etc.

Note: When it is running there is not option in the dropbox on the task bar to pin, as there normally is.

Also note: This is the aforementioned program [Linaxepad released as deb on Ubuntuforums.org]("http://ubuntuforums.org/showthread.php?t=1113839&highlight=linaxepad")

---

### Post by TeoBigusGeekus on 2011-04-16
Right click your menus> Edit menus
Go to applications, select an appropriate subcategory and click New entry.
Give it a name of your liking and give as its command
```
/usr/apps/whatevertheappropriatecommandis
```

---

### Post by pete20r2 on 2011-04-17
will try tomorrow, thanks for the help.

---

