---
title: "Networked Ubuntu computers can't find each other"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by KillerSponge on 2007-12-13
Hi,

I'm trying to make it possible to share files between my notebook and my desktop. Both are running Gutsy. They *can* ping each other, and both have shared samba folders, but when I go to "Network", all I see is an empty Windows-network. Also, when I try SSH (yes, the server is installed :P ) I get a time-out.

Could someone help me out with this? :)

---

### Post by hoppy on 2007-12-14
Hi KillerSponge,

Have you tried installing smb4k. I found that this made life a lot easier when using smb shares.

Hoppy

---

### Post by KillerSponge on 2007-12-14
Hi Hobby,

Thanks for the suggestion. But scanning the network doesn't find anything, and when I try to make a shortcut manually, it sais I don't have permission to acces the shared folder, and asks for a login (which doesn't let me in :P )...

:confused:

---

### Post by viking777 on 2007-12-14
Have you tried opening them via their ip address?

In other words go into konqueror or whatever you use and type in the address bar:

smb://192.168.1.1 

or whatever ip address they happen to be.

---

### Post by KillerSponge on 2007-12-14
I thought I already tried that, but it seems to work! At least, part of it. I can now SSH/SMB from my desktop to my notebook, but, my notebook still can't seem to connect in any way to my desktop. It can ping it, however :confused:

---

### Post by viking777 on 2007-12-16
You could try the suggestions in my post on this thread:

[http://ubuntuforums.org/showthread.php?p=3938016#post3938016](http://ubuntuforums.org/showthread.php?p=3938016#post3938016)

Post #6

I will be surprised if it does any good but if you are still stuck it might be worth a try.

---

