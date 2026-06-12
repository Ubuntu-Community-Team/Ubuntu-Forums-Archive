---
title: "Help. Please x11 and emacs"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by poundjd on 2008-12-04
All,
     I have an ubuntu server as my gateway running eBox on it and eth0-4.  I would like to be able to start an x windows session up displayed on my MS Vista box but running on the ubuntu server.
I want to run emacs in that x-Windows session but have it displayed on my VISTA machine.  I have already installed emacs, and I believe that I need to install x11 on the ubuntu server, but I am wondering what else would be needed.

Can someone please let me know what I have to install on the ubuntu server and on the vista to get this working?
-jeff

---

### Post by jpkotta on 2008-12-04
Actually the X server would be on the Windows machine.  The server is always on the machine that is displaying the graphics.  I always use cygwin for an X server on windows.  You will also probably want an ssh client.  PuTTY or the OpenSSH in cygwin both work.  

You will still have to install X on the server, because if you install anything graphical, it brings in X as a dependency.  This also means you don't have to install X explicitly.  Just install emacs22 (or xemacs21).  If you're using ssh, also install openssh-server.

Then you can use X forwarding.  In cygwin's xterm: ```
ssh -X user@linuxhost
```
Then when you're logged in, 
```
emacs file.txt
```

---

### Post by ja660k on 2008-12-04
use vim; dont need x11

[http://vim.wikia.com/wiki/Best_Vim_Tips](http://vim.wikia.com/wiki/Best_Vim_Tips)

---

### Post by jpkotta on 2008-12-04
Emacs doesn't need X11 either.  I just figured that OP would rather have X11 because they requested it.

```
emacs -nw file.txt
```

The 'X' in Xemacs doesn't stand for X11.  -nw works there too.

---

### Post by poundjd on 2008-12-04
you know I always was confusing which were the Clients and which were the servers...

---

### Post by poundjd on 2008-12-05
OK,
     I got the cygwin x stuff installed on the vista machine.  I also had PuTTy installed as well.
I use my vista machine as my main console because of the monitor.

issues:
      1) in putty (SSH) and xterm my mouse is useless in the window, I have to do all navigation via keyboard.  I have a simple text cursor but it has no effect.

      2) when in Putty (SSH) or Xterm and I do emacs -nw file I get the current window taken over by emacs.  A workable solution, but not able to spawn new windows with emacs running in them.

      3) when in putty (SSH) and xterm and I do ssh -X emacs file or ssh -X emacs file, nothing happens on the screen and in the window my cursor is on the next line.  I have to CTL-C to get the cursor back.

    Did something go wrong with the install or is my windows firewall causing this? 

Thanks for you help.
-jeff

---

### Post by jpkotta on 2008-12-05
> 1) in putty (SSH) and xterm my mouse is useless in the window, I have to do all navigation via keyboard. I have a simple text cursor but it has no effect.

You can't move the cursor in the shell with the mouse.  This is mostly OK because you can't edit anything other than the current line anyway.  You should be able to select text by left drag and paste with either middle or right click.  When something like emacs takes over the terminal, it might be possible to place the cursor with the mouse, depending on the app (it should work in emacs).

> 2) when in Putty (SSH) or Xterm and I do emacs -nw file I get the current window taken over by emacs. A workable solution, but not able to spawn new windows with emacs running in them.

C-z (control-z) will suspend emacs and give you your shell back.  Get emacs back with "fg" (put emacs in the *foreground*).  C-z is a common binding for suspending most text-mode apps.  Also have a look at screen, which enables several different sessions in the same terminal.

> 3) when in putty (SSH) and xterm and I do ssh -X emacs file or ssh -X emacs file, nothing happens on the screen and in the window my cursor is on the next line. I have to CTL-C to get the cursor back.

Did something go wrong with the install or is my windows firewall causing this?

It is possible that the fw is causing this.  Make sure the X server is actually started.  There should be a little X in the system tray, and you should be able to run xlogo on the Windows machine (i.e. from the xterm without sshing).

---

