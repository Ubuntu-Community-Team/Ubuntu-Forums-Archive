---
title: "wireless network without NetworkManager"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by MichaelBurns on 2009-12-28
Without using the NetworkManager Applet that appears on the upper panel, how would I find a list of available wireless networks and then connect to one?

I tried System > Preferences > Network Connections, but it does not list any networks.

Ideally, I want to find a network and connect to it from the command line.

---

### Post by spiky001 on 2009-12-28
whats wrong with network manager applet?

---

### Post by bkratz on 2009-12-28
> **MichaelBurns said:**
> Without using the NetworkManager Applet that appears on the upper panel, how would I find a list of available wireless networks and then connect to one?

I tried System > Preferences > Network Connections, but it does not list any networks.

Ideally, I want to find a network and connect to it from the command line.



Well you could drop to the terminal and enter

sudo iwlist scan

it should show any local AP's

---

### Post by MichaelBurns on 2009-12-28
Thanks, bkratz.  That command is pretty informative.  I'm confused by the address, though.  I thought that IP address should have 4 bytes, but the one that I see has 6.

Also, do you know how I can connect from the command line?

> **spiky001 said:**
> whats wrong with network manager applet?Nothing, if I can figure out how to use it (conveniently) without the mouse.

---

### Post by bkratz on 2009-12-28
> **MichaelBurns said:**
> Thanks, bkratz.  That command is pretty informative.  I'm confused by the address, though.  I thought that IP address should have 4 bytes, but the one that I see has 6.

Also, do you know how I can connect from the command line?

Nothing, if I can figure out how to use it (conveniently) without the mouse.

Try this one

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

