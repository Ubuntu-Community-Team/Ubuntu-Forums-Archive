---
title: "Function keys under SSH"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by isecore on 2007-09-29
First off, I've searched the forums and Google to no avail. It's just really difficult to phrase the search terms right when it comes to my specific problem. Secondly, if this is in the wrong section, maybe a moderator can move it.

Now, my problem is that gnome-terminal doesn't forward function keys (F1, F2, F3, etc) during a ssh. I run a Debian server besides my Ubuntu-desktop, and depend heavily on SSH for control of it. I'm also a long addict of the Midnight Commander which uses the function keys extensively.

However, these don't work when connected through SSH. They work fine locally, so I assume that there's something that needs tweaking with SSH. However I haven't managed to figure out what that is yet...

If anyone has a clue, please let me in on how to make SSH forward the function keys from gnome-terminal as well. It'd be very nice to be able to properly use MC again :)

Thanks!

---

### Post by MobiusNZ on 2007-09-29
Edit->Keyboard Shortcuts.

Remove/reassign any shortcuts that conflict with your usage

---

### Post by isecore on 2007-09-29
Believe me, if it was that simple I would've done it. 

There are no keys there that conflict with my usage. Everything works perfectly when I'm in a terminal locally on my desktop-machine. However, if I ssh into my server all of a sudden they either don't work or act as other keys (example: F3 takes on the functionality of the insert-key).

---

### Post by MobiusNZ on 2007-09-29
Interesting. I just quickly installed mc on my server, and the f keys are working fine through ssh.

Maybe check on the remote machine for keybindings?

---

### Post by isecore on 2007-09-30
> **MobiusNZ said:**
> Interesting. I just quickly installed mc on my server, and the f keys are working fine through ssh.

Maybe check on the remote machine for keybindings?

It's just a terminal running bash there. No keybindings to check.

---

### Post by MobiusNZ on 2007-09-30
Hmmm, maybe try a different terminal?

---

