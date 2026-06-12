---
title: "New user having heck of time with Enlightement"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by plencner99 on 2010-10-28
Install ubuntu maverick via wubi three days ago to replace xp on my old dell also installed enlightenment e16 and feels told old school for me so trying to get e17 when in use sudo vi /etc/apt/sources.list i get
E325: ATTENTION
Found a swap file by the name "/etc/apt/.sources.list.swp"
          owned by: root   dated: Wed Oct 27 20:52:39 2010
         file name: /etc/apt/sources.list
          modified: YES
         user name: root   host name: ubuntu
        process ID: 1710
While opening file "/etc/apt/sources.list"
             dated: Wed Oct 27 21:09:20 2010
      NEWER than swap file!

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/apt/sources.list"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/apt/.sources.list.swp"
    to avoid this message.
"/etc/apt/sources.list" 54 lines, 2964 characters
Press ENTER or type command to continue

What do i need to do from here also how do you save when using terminal I have tried ctrl x and ctrl o 
and and got a funny looking letter.Any help or walk through for this dummy would be appericated thanks in advance.

---

### Post by Windows Nerd on 2010-10-29
This sometimes happens when I close a terminal session or logout without saving in vi.

In the case of:
"(1) Another program may be editing the same file.
If this is the case, be careful not to end up with two
different instances of the same file when making changes.
Quit, or continue with caution."

If you are not also editing that file already in a different shell, just delete the .swp file:

```
sudo rm /etc/apt/.sources.list.swp
```

If you are editing the file already in a different shell, that error is happening because two different programs cannot edit the same file. Just edit it with the original file.

In the case of (2)

(2) An edit session for this file crashed.
If this is the case, use ":recover" or "vim -r /etc/apt/sources.list"
to recover the changes (see ":help recovery").
If you did this already, delete the swap file "/etc/apt/.sources.list.swp"
to avoid this message.

The reason saving with ctrl+x and ctrl+o is not working is because you are using vi. You likely should be using nano, as vi is more advanced and most more advanced users would probably figure out what these errors mean on their own.

To use nano:

```
nano <file>
```

---

### Post by ikt on 2010-10-29
> **plencner99 said:**
> Any help or walk through for this dummy would be appericated thanks in advance.

Why not get a little familiar with ubuntu and linux first and then go about changing config files and front ends?

It just seems like to me like you're jumping the gun just a tad.

---

### Post by HermanAB on 2010-10-29
Hmm, Enlightenment is not the default desktop - for many good reasons and you are about to discover them all. Having fun is what Ubuntu is all about, so good luck with your journey of discovery.  Be sure to write a howto guide for those who follow.

---

