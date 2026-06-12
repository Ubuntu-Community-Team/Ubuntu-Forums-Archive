---
title: "Setting up Wireless Networking - Strange behavior in feisty"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by Ubempi on 2007-05-14
I've installed Ubuntu and it has recognized my wireless card and I've configured it with the correct IPs the Internet Provider gave me, but:

-Each time I start Ubuntu:

... 1 - internet is not working (Mozilla, Synaptic, nothing)...

... 2 - I then click in "Static configuration..." (this opens the Static configuration dialog):  ... [look at the animated gifs]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32591&stc=1&d=1179167209[/IMG]

... 3 - I disable the network:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32592&stc=1&d=1179167209[/IMG]

... 4 - Un-check and then re-check my wireless card's checkbox on the "Static configuration" dialog:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32593&stc=1&d=1179167209[/IMG]


... 5 - Internet now works.


Notice that I have "disabled" network in step 3, Internet keeps working until I enable the network again or restart the computer.

Step 4 is mandatory for Internet to work, and step 3 is necessary for step 4 


Info - My Hardware and Software:
 --- x86 architecture (mb: Asus P4V8XMX, p: Pentium 4)
 --- RaLink Wireles Card (PCI)
 --- Ubuntu 7.04 Beta

Any help on this issue?

---

### Post by Ubempi on 2007-05-28
Finally, this is the solution:

*  - Update from internet:
*             * any package beginning with networkmanager (networkmanager-gnome, and so on)

Thanks :)

---

