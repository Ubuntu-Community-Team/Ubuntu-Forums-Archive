---
title: "Ssh&amp;vnc"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by dmitrijledkov on 2007-10-28
I followed [https://wiki.ubuntu.com/VNCOverSSH](https://wiki.ubuntu.com/VNCOverSSH). And did everything for the Ubuntu Host. It is fresh Gutsy-desktop.

Now from my laptop at home (also Gutsy-desktop) trying to connect to ssh (just ssh ip) it sais. Well now it doesn't work at all but before it was saying Enter password, then I entered it, and then it sais access denied.

if i did vncviewer -via ip host:0 it was asking for ssh again. and then saying access denied.

did just vncviewer host:1 and it popped up with authentication with username grayed out entered password only and it opened just huge gray window.

What did I do wrong or how to test it?

In the end I just want to be able remotely login into my account and do everything with the computer (I'm "administrator").

---

### Post by evilregis on 2007-10-28
Is there a particular reason you chose to use that guide as opposed to using the default remote desktop solution (vino) in Ubuntu?

I've got two Ubuntu machines talking through VNC over SSH.

System -> Preferences -> Remote Desktop
Check: Allow others to view your desktop
Check: Allow other users to control your desktop
Uncheck: Ask you for confirmation
Check: Require the user to enter this password:
Enter a password.

Make sure routers/firewalls are allowing SSH traffic (port 22 by default).

On the client machine I simply enter in terminal:

```
vncviewer-via usernam@host localhost:0
```

It asks for the password of username and then prompts me for the password required to complete the VNC connection.

---

