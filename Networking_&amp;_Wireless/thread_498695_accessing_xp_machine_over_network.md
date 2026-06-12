---
title: "accessing xp machine over network"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by libertyblues on 2007-07-11
Is there a way to pull up a screen of a windows machine on my network from Ubuntu? I am using 6.06.1 on my laptop and would like to be able to fiddle around with music on the machine across the way running xp, as that's where the real speakers are.

If there's more information required to understand the situation I'll be happy to provide it


"in the mountains of norway were the weather is cold, there's not much to do but kill each other and play guitar in the snow"

:guitar:

---

### Post by solar george on 2007-07-11
You can enable remote desktop (I think that's what it is called) in XP and use  the terminal server client applet from ubuntu to connect - use the rdp protocol.

N.B. the user on the XP machine *must*  have a password set.

---

### Post by libertyblues on 2007-07-21
thanks, i'll try that

---

### Post by jay019 on 2007-07-21
Hi,

You could also try [vnc]("http://www.realvnc.com/"). Install the server on windows, set a password.

Than on your linux box type vncviewer "ip address of other computer" in an xterm. (You may ned to install vncviewer if its not on your linux box, but it should be)

Then you get a screen that is the desktop of your main computer. I use it at home here and its great. It's as if you were on that windows box direct!

Jay

---

