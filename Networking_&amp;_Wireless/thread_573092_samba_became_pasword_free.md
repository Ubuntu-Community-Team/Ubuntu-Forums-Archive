---
title: "samba became pasword free"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by Hellaxe on 2007-10-11
Hello people:

I've searched for an answer to this stupid issue but had no lucky so I ask for some help.

For some reason, about 3 months ago, wen i try to view my shares on the desktop, from my laptop, I can enter in the directories but can't see files on them.
The strange thing is that I'm not prompt with the authentication window. It just enters the Desktop shares and nothing after that.
This happens also in the ClackConnect server. I do the ```
smb://x.x.x.x
``` and then it goes just to the shared directories (no authentication is prompt), then no acces dto the files.
It just happens from one day to another and i don't remenber having done any change to any file.

The Laptop is linked by a wireless router that have diferente range of IP then the range of the rest of the IP network privided by the server.
EX: Wireless 10.x.x.x; server 192.x.x.x

Is there any file the store the user passwords of Samba?? I don't think so but i don't know everything.

Thanks

---

### Post by Hellaxe on 2007-10-12
Anyone..Pleaseeeeeeeeeeeeeeee.

Thanks

---

### Post by cwhitehouse on 2007-10-12
I was just reading this thread.  It may help you out some.  [http://ubuntuforums.org/showthread.php?t=23616](http://ubuntuforums.org/showthread.php?t=23616)

If not, try searching around to confirm you have samba configured correctly.

---

### Post by Hellaxe on 2007-10-12
Thanks for the link but i think it has nothing to do with my problem.
This issue just started from one day to the other.

---

### Post by Hellaxe on 2007-10-12
Thanks for the link but i think it has nothing to do with my problem.
This issue just started from one day to the other.

If i do ```
smb://user@server/share
``` work perfectly. Shows a window with the authentication requirement and then it shows all the files.

---

