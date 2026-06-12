---
title: "Change shell background color on ssh"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by gizmobay on 2010-01-12
Does anyone know of a way to change the background color of the the Gnome terminal when I log into a remote host with ssh? I have a few tabs open and I forget that some are ssh logins.

---

### Post by duds2008 on 2010-01-12
Is "screen" any help? Try man screen to see if you have it installed. Good luck.

---

### Post by Hospadar on 2010-01-12
I usually just set a different color prompt for my remote hosts, I'm not sure gnome-terminal can change profiles automatically if you are logged in elswhere.  That said, you can make a profile you want to use (Edit->Profiles) for remote sessions, and just switch to it manually when you start a remote session in a terminal.  There's probably a keyboard shortcut to switch profiles (or you could make one)

---

### Post by jms1989 on 2010-01-12
try modifying your .bashrc file on the server to change the color. I can't help you on the syntax as I don't know myself. Try googling for some already made files.

---

### Post by gizmobay on 2010-01-12
I made a ssh profile and then I just manually change it. Probably can set a hotkey to change it.

Thanks

---

### Post by IanBlanes on 2010-11-01
I had a similar problem. Just not to write the same thing twice, I'm posting the link to my reply in another thread:[ http://ubuntuforums.org/showthread.php?p=10058620#post10058620]("http://ubuntuforums.org/showthread.php?p=10058620#post10058620")

---

