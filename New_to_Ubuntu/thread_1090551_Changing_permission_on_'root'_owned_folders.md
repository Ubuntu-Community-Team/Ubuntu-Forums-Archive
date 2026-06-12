---
title: "Changing permission on 'root' owned folders"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Grynch108 on 2009-03-08
Hi All,

I've started using Ubuntu for the first time on my new Netbook. I'm on longtime Mac OS X user, but I'm finding the jump to Ubuntu quite difficult.

At the moment, I'm customizing my desktop (if anyone has some good step-by-step guides by the way, they'd be most useful!), and I'm downloading some wallpapers.

I'm trying to copy the jpegs from the desktop to the /usr/share/backgrounds foler, but I'm unable to because I cannot change folder permission on 'root' owned folders. Any ideas on how I can do this? Or will I have to create a new 'wallpaper' folder to put them in?

Off topic, I'm having trouble when using the GIMP image editor, because certain windows are actually longer than the 600 pixel height of the screen, and I can't resize or move the window above the top panel. Can I zoom the desktop out or scroll the desktop?

Many thanks!!!:D

---

### Post by taurus on 2009-03-08
If you need to move or copy something outside of your $HOME, run nautilus with root privilege.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Paqman on 2009-03-08
> **Grynch108 said:**
> 
I'm trying to copy the jpegs from the desktop to the /usr/share/backgrounds foler

First question: why?

You've got full permissions on anything within your /home folder, why not just put them in there?

Regarding windows being too big for the screen, you can hold down ALT and click on any part of a window to drag it to somewhere better.

---

### Post by hexanol on 2009-03-08
Well, you can use the "sudo" command to execute command as root. This way, you'll be able to change the permissions of a file owned by root.

Example
```
/var/www$ ls -l index.html
-rw-r--r-- 1 root root 234 2008-12-16 10:32 index.html
/var/www$ chmod a+w index.html
chmod: changing permissions of `index.html': Operation not permitted
/var/www$ sudo chmod a+w index.html
/var/www$ ls -l index.html
-rw-rw-rw- 1 root root 234 2008-12-16 10:32 index.html

```

---

### Post by Yashiro on 2009-03-08
Open the wallpaper chooser. 
Leave your pictures in your home folder.
Drag and drop your wallpapers onto the chooser dialog.

It is quite Mac like is it not?

---

### Post by Grynch108 on 2009-03-08
Thanks all for the help.

> **Paqman said:**
> First question: why?

Because that is where the desktop wallpapers were located by default. I wanted to put them all in one place rather than have two different locations. It's all useful information for me to know anyway.

---

### Post by blueridgedog on 2009-03-08
> **Grynch108 said:**
> I wanted to put them all in one place rather than have two different locations. It's all useful information for me to know anyway.

I like that answer.  Good luck.

---

