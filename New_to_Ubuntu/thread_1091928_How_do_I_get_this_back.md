---
title: "How do I get this back?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by 3wells on 2009-03-09
1) I deleted the bottom panel ---- not good! How do I get it back?

2) O don't seem to have permission to open the lost and found folder. How do I get in?

3) I can't log in as 'root - I get a username and password error? What am I doing wrong?

3

---

### Post by saxofoner on 2009-03-09
You don't want to log in as root.  We append "sudo" to the beginning of a command to do stuff as root.  I'm not sure about L&F.  For the bottom panel, run "sudo gconf-editor" and go to apps, panels, toplevels, and edit those parameters as you see fit.  They're pretty straightforward.  Also, if you still have one panel, right click on it and just click add new panel.  Then you can add stuff back to make it like default.

---

### Post by phaze_1 on 2009-03-09
for the bottom panel just right click on your top panel and click ' new panel '

---

### Post by 3wells on 2009-03-09
Got that.... however, if I minimize a progy, it's gone? I think? ie Firefox, I have to restart a new session...?

---

### Post by Kareeser on 2009-03-09
Right click the bottom panel -> Add to Panel -> Window List

---

### Post by UbuntuNerd on 2009-03-09
> **3wells said:**
> Got that.... however, if I minimize a progy, it's gone? I think? ie Firefox, I have to restart a new session...?

can you try this command in a terminal, it should restore your panels to default like they were before:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by Miljet on 2009-03-09
Why would you want to get into the lost+found folder? It is my understanding that it is just a place to store orphaned file fragments found during file system checks. It probably doesn't contain anything, and even if it does, it won't be anything usable.

If you are determined to see what, if anything, is there you can use the following command.

```
 sudo ls /lost+found 
```

---

### Post by 3wells on 2009-03-10
> **Kareeser said:**
> Right click the bottom panel -> Add to Panel -> Window List

That was easy! That was just about the only button I didn't add!

Thanks!

3

---

### Post by 3wells on 2009-03-10
> **Miljet said:**
> Why would you want to get into the lost+found folder? It is my understanding that it is just a place to store orphaned file fragments found during file system checks. It probably doesn't contain anything, and even if it does, it won't be anything usable.

If you are determined to see what, if anything, is there you can use the following command.

```
 sudo ls /lost+found 
```

Nuhin'?

ross@ross-desktop:~$ sudo ls /lost+found
ross@ross-desktop:~$ cd /lost+found
bash: cd: /lost+found: Permission denied
ross@ross-desktop:~$ 


What am I doing wrong? I can't open the folder directly either?

3

---

### Post by skymera on 2009-03-10
> **3wells said:**
> Nuhin'?

ross@ross-desktop:~$ sudo ls /lost+found
ross@ross-desktop:~$ cd /lost+found
bash: cd: /lost+found: Permission denied
ross@ross-desktop:~$ 


What am I doing wrong? I can't open the folder directly either?

3

That shows there is nothing in the folder.
And no, you don't have access to open the folder.

---

