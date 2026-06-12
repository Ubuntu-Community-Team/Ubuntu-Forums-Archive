---
title: "X over SSH with Xming and PuTTY - Help me get it working again?"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Picklegnome on 2009-08-10
Hi,

(Wow, I just noticed that I've been a member since 2005. First post since then, I think.)

I have a headless server (literally headless - there's no VGA port to even connect a monitor to) which I managed to install Xubuntu (Jaunty) on. I don't want to use server edition because I'm not confident enough in my command-line-fu yet.

As my laptop is in the shop, I'm using a Windows computer with Xming and PuTTY to ssh to the server on my LAN. X over SSH was working fine last night, but I didn't log out, close PuTTY, or close Xming before disconnecting. Since then, I've gotten through various parts of solving the problem. Here's where I am at currently:

[LIST]
[*]When I log on, everything goes fine except for a message saying "/usr/bin/X11/xauth: ~/.Xauthority not writable, changes will be ignored"
[*]The first time I try to run an X application, I get the error "PuTTY X11 proxy: wrong authentication protocol attemptedError: Can't open display: localhost:10.0"
[*]Subsequent X applications give the same response, less the "localhost:10.0"
[/LIST]

Any thoughts? Help is greatly appreciated.

---

