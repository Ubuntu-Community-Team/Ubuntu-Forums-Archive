---
title: "vncviewer - syntax?"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by PiggiePaul on 2008-02-25
Pretty basic one this.

I'd like to make a file/icon which when double clicked runs the vncviewer and logs me into my remote PC running a vnc server.

The syntac would simply be:

vncviewer MACHINENAME PASSWORD

But I can't seem to get the syntax right for it to accept it.

And even if I could get it right (at the command line) I don't know how then to make it into a file I just double click on and it runs the command.

I know this is really simple (for someone who knows) but I've not done this type of thing before.

---

### Post by chewearn on 2008-02-26
Right-click on the gnome panel > add to panel > custom application launcher

Command: vncviewer <hostname>

E.g. command: vncviewer 192.168.0.2

Click OK to confirm.  An icon will appear on your panel, now when you click on it, you get a password prompt (dialogbox).

---

### Post by PiggiePaul on 2008-02-26
> **AstalaVista said:**
> Right-click on the gnome panel > add to panel > custom application launcher

Command: vncviewer <hostname>

E.g. command: vncviewer 192.168.0.2

Click OK to confirm.  An icon will appear on your panel, now when you click on it, you get a password prompt (dialogbox).

Thanks for that, will try later.

What I would really like though is no not have to enter my password every single time.
Hence I'm hoping the password can be part of the command syntax

---

### Post by PiggiePaul on 2008-02-26
Back home on my PC

Just to say, I have followed your example above and it works, great :)

If only I can get the password added to the command "vncviewer hostnamr" then that would be superb.

---

