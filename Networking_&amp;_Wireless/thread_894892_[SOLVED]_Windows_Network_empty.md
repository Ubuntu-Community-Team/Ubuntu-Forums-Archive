---
title: "[SOLVED] Windows Network empty"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by Alistair George on 2008-08-19
Earlier, networking worked really well. I just plugged in the wifi card, enabled Windows shares on another computer, and away it went.
Its just started showing nothing in the Linux Windows folder using Nautilus 2.22.3.
If I Go/Location smb://10.1.1.5 (external ip address) shared folders are then available.
If I go Places/Connect to Server/Windows Share 10.1.1.5 = can't display location smd://10.1.1.5/ No application is registered as handling this file

Post#2 typing Nautilus smb://10.1.1.5 brings up a window showing the shares.
I have reinstalled Samba as suggested on other threads.

Post#3 OK, I suspect Nautilus, as I had read somewhere it was a bit flakey, so installed GNOME commander and Voila, SMB shows all shares as before.

Post#4 It seems that Nautilus does not try Samba; when the Network Icon is clicked, there is no delay even on refresh. Remote desktop viewer I believe is used by Nautilus to view networks? If so, Remote desktop viewer cannot find the network either.

Post#5 What I've found is that with a relog on Ctrl-Alt-Backspace and same logon detail the shares become visible in Nautilus!!


I will not put FIXED on this thread till someone who has more clues suggests a fix for Nautilus.

This is a common problem as if you search for 'empty Windows shares' there are several hits all describing the same problem without any resolution.
Any advice please?
Thanks,
Alistair.

---

### Post by MaX on 2008-08-20
Write a detailed descrition of your network and steps to reproduce this in a buggreport on launchpad.
That's my advice.

---

### Post by Alistair George on 2008-08-20
> **MaX said:**
> Write a detailed descrition of your network and steps to reproduce this in a buggreport on launchpad.
That's my advice.

Done thanks BTW they reported back that its already been opened for fixing. No further comments are needed here.

---

