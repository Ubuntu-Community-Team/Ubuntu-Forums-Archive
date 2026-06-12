---
title: "turning on network manager"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by thorbs on 2010-08-30
I have 10.04 installed on my laptop. When I had installed it, it turned on my network manager automatically by startup. I was not interested in this, so I turned it off in the startup option. But now I dont know how to turn it on, when I want to. The only solution I have found so far, is to turn it on in the startup menu, and then restart the computer.

Can anybody help?

---

### Post by Iowan on 2010-08-30
I haven't tried this, so...
Alt-F2 should open up a Run Application window. You can try running **nm-applet** from there. (dunno if it requires **sudo**)

---

### Post by earthpigg on 2010-08-30
hi,

iowan's suggestion will indeed work, but you will have to do it every time you login.

try this:

system -> preferences -> startup applications

scroll to find the "Network Manager" entry that you un-checked before, and re-check it.

If it isn't there, you can re-add it from that window.

click 'add', and fill it in... below are the defaults taken from my system.
Name: Network Manager
Command: nm-applet --sm-disable
Comment: Control your network connections

the "Command" entry is the only really critical ones. the other two fields can read whatever you like.

---

