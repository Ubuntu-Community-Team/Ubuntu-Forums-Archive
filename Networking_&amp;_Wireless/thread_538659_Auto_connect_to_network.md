---
title: "Auto connect to network ?"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by waynep on 2007-08-30
I have Ubuntu 7.04 installed in a Parallels Virtual Machine. I used to have 6.10, but blew that away and installed 7.04.

With the new version, I have to use the icon on the upper right hand orner of the screen to manually connect each time I start the system. With 6,.10, I did not have to do that, it connected on it's own which I would prefer 7.10 do also.

I do have Network Manager 0.6.4-6 installed per my Synaptic Package Manager. 

I can't seem to find somewhere to set an Auto connect feature . . . 

Any ideas?

-wayne

---

### Post by bmartin on 2007-08-30
Feisty seems to auto-connect for me. Have you tried using a different wireless connection manager, like WICD or wifi-radar?

---

### Post by waynep on 2007-09-04
Have not tried that. Does Network Manager not have that option?

---

### Post by noob12 on 2007-09-05
Check that you have the interface in /etc/network/interfaces and have an **auto** line for it.  That should be sufficient. If it's a virtual interface bridged to a physical device on the host machine, you probably will want just to configure it in this file. See also **man interfaces**.

In this situation you may not need or want any connection manager around; it may just interfere.

---

