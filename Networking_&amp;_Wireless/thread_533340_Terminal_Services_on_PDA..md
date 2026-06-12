---
title: "Terminal Services on PDA."
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by Roasted on 2007-08-23
Today my instructor showed us that he can use his pda/phone, using the program terminal services, to log into his server (located across the building) and navigate through as if he were actually sitting there. It worked nicely. His pda/phone has windows mobile 5.

I have a pda (not a phone combo) that has windows mobile 5 with terminal services preloaded.

How might I be able to wirelessly connect to my machine and do the same thing he did?

---

### Post by livestockPimp on 2007-08-24
I take it the server he logged onto was a windows server,
you need to firstly be running windows xp pro/win2003 and you enable "remote desktop" (right click on my computer, properties, remote tab). once this is done you can access it via its IP if you are inside the network, otherwise you will need to set up port forwarding rules and use your internet IP.

---

### Post by Roasted on 2007-08-24
Yeah. He was using server 03.

I was just curious if I could do that to my local Ubuntu machine, just to test it and see if it worked.

---

### Post by livestockPimp on 2007-08-24
rdp is a microsoft protocol! thats why linux users use vnc for remote desktop.
your best bet would be to try and find a vnc viewer for your pda.:guitar:[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)
:guitar:

---

