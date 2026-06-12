---
title: "is shell another word for terminal?"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by listerdl on 2009-11-13
is shell another word for terminal?

---

### Post by atomizer on 2009-11-13
nope. you use a shell in a terminal, but you can switch shells.
The most used shell is Bash.


[from about.com:linux :]("http://linux.about.com/od/linux101/a/desktop11.htm")
> 
The Linux/Unix shell refers to a special program that allows you to interact with it by entering certain commands from the keyboard; the shell will execute the commands and display its output on the monitor.

---

### Post by Spiritof76 on 2009-11-13
A terminal is the program that you type in to it It contains the software that that interperts the key strokes and places them on the screen.  
The Shell is a program that decides the form and style the commands take and are displayed.  
Things that are configured in the terminal might be the color, fonts and screen size.

Things that are configured in the shell are commands aliases and the prompts

---

### Post by listerdl on 2009-11-13
> **Spiritof76 said:**
> A terminal is the program that you type in to it It contains the software that that interperts the key strokes and places them on the screen.  
The Shell is a program that decides the form and style the commands take and are displayed.  
Things that are configured in the terminal might be the color, fonts and screen size.

Things that are configured in the shell are commands aliases and the prompts

So when someone says, 'type into shell the following command' what they mean is type the command into the terminal (which is the GUI for Shell?

---

### Post by ukripper on 2009-11-13
> **listerdl said:**
> So when someone says, 'type into shell the following command' what they mean is type the command into the terminal (which is the GUI for Shell?

By default they mean type into bourne shell aka Bash. Terminal usually starts on ubuntu with Bourne shell ( by default for users), unless specified during user creation or their shell is amended later on then it would be soem other shell.

---

### Post by Mornedhel on 2009-11-13
> **ukripper said:**
> By default they mean type into bourne shell aka Bash. Terminal usually starts on ubuntu with Bourne shell ( by default for users), unless specified during user creation or their shell is amended later on then it would be soem other shell.

Bash is the Bourne Again SHell. The Bourne Shell is sh.

---

### Post by ukripper on 2009-11-13
> **Mornedhel said:**
> Bash is the Bourne Again SHell. The Bourne Shell is sh.

thanks for pointing that out. i almost forgotten about the difference.

---

### Post by kaibob on 2009-11-13
> **Mornedhel said:**
> Bash is the Bourne Again SHell. The Bourne Shell is sh.
I was under the impression that dash is the Ubuntu system shell (/bin/sh). Perhaps I don't understand the terminology correctly. 

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

### Post by Mornedhel on 2009-11-13
> **kaibob said:**
> I was under the impression that dash is the Ubuntu system shell (/bin/sh). Perhaps I don't understand the terminology correctly. 

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

Yup, /bin/sh is a symlink to dash (/bin/dash). Dash implements a sh-like shell. Bourne itself replaced another shell as sh.

Dash as sh is distribution-specific, however. You should call 'sh' and use sh-only features for portability, as other systems may use other shells instead. The point is to rely on a subset of POSIX-compliant features. Some scripts written when bash was the Ubuntu system shell broke when the transition to dash was made, because they used bash features that were not in the sh feature subset.

As far as I know, you can't install ye olde Bourne shell on current Ubuntu versions.

I did word my previous post awkwardly. My point was that the Bourne shell only offers sh features.

---

