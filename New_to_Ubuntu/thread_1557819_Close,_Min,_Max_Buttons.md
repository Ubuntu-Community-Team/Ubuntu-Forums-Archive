---
title: "Close, Min, Max Buttons"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by hoosier1104 on 2010-08-21
I lost my all my close, min, max buttons on the top of all the windows.  How could I go about getting the back?

Justin

[IMG]http://i567.photobucket.com/albums/ss119/hoosier1104/Screenshot.png

---

### Post by jtarin on 2010-08-21
Run the command ```
gconftool-2 -t string --set /apps/metacity/general/button_layout menu:minimize,maximize,close
```

---

### Post by Frogs Hair on 2010-08-21
This thread may help as well.  [http://ubuntuforums.org/showthread.php?t=1526134&highlight=restart+window+manager](http://ubuntuforums.org/showthread.php?t=1526134&highlight=restart+window+manager)

---

### Post by nick_goodfate on 2010-08-21
it seems you have lost window decoration, not only close max min buttons ... i think you must run "matacity -replace" to get it back ?

---

### Post by hoosier1104 on 2010-08-21
No go.

justin@justin-laptop:~$ gconftoo-2 -t string --set /apps/metacity/general/button_layout menu:minimize,maximize, close
No command 'gconftoo-2' found, did you mean:
 Command 'gconftool-2' from package 'gconf2' (main)
gconftoo-2: command not found

---

### Post by hoosier1104 on 2010-08-21
> **Frogs Hair said:**
> This thread may help as well.  [http://ubuntuforums.org/showthread.php?t=1526134&highlight=restart+window+manager](http://ubuntuforums.org/showthread.php?t=1526134&highlight=restart+window+manager)


That worked thanks.

---

