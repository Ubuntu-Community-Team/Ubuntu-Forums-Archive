---
title: "Connecting to VNC without logging into gnome first"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Michael Deats on 2010-10-24
Hi all,

I've got an ubuntu 10.04 (desktop) box standing in the corning with no screen attached to it. Before I removed the screen - I enabled remote administration and installed open-ssh server so I could connect to it.

Now I've noticed that remote admin doesn't start unless I log into gnome first. Is there anything I can install or change from the command line that can circumvent this or work as a work around?

---

### Post by msmx5s on 2010-10-25
See the following thread: [http://ubuntuforums.org/showthread.php?t=1562263](http://ubuntuforums.org/showthread.php?t=1562263)

It is mainly about Teamviewer, but one of the solutions could apply to VNC...

---

### Post by Michael Deats on 2010-10-25
> **msmx5s said:**
> See the following thread: [http://ubuntuforums.org/showthread.php?t=1562263](http://ubuntuforums.org/showthread.php?t=1562263)

It is mainly about Teamviewer, but one of the solutions could apply to VNC...

Thanks :) I hope there is a way to set it to auto-log in from from the command line - so I don't need to find a screen to connect to it first.. :)

---

### Post by HermanAB on 2010-10-25
Howdy,

Since you already have SSH installed and working, just use that:

$ ssh -X -C -c blowfish user@serveripaddress gnome-panel

Now you can go click happy and any remote program will run transparently on the local desktop.

---

### Post by Michael Deats on 2010-10-25
> **HermanAB said:**
> Howdy,

Since you already have SSH installed and working, just use that:

$ ssh -X -C -c blowfish user@serveripaddress gnome-panel

Now you can go click happy and any remote program will run transparently on the local desktop.

Cool, thank you - will try that when I get home from work..

---

