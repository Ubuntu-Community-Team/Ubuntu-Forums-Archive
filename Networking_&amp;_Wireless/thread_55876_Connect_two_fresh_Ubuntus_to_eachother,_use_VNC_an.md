---
title: "Connect two fresh Ubuntus to eachother, use VNC and SSH"
date: 2005-08-10
forum: Networking &amp; Wireless
---

### Post by mikuskuikku on 2005-08-10
Here's the thing.
I have 2 fresh Ubuntu machines. ('Uhamn' and 'ismh')

'ismh' need to use the modem to connect to 'Uhamn'.
'ismh' should be able to use 'ssh', 'scp' and 'vncviewer'.

What to do?
I have modems in both of them (they are right here beside me).
I have 2 telephone lines to test with.

I figured out to use 'System'>'Administration'>'Networking' and activaded the modems (and typing down the telephone numbers).

I've been reeding about wvdial, pptp, pppd and a lot of other ways to connect 2 computers to each oteher... ITS A JUNGLE!

Is there a easy whay?  :roll: 
<<mikuskuikku>>

---

### Post by nat on 2005-08-11
sudo apt-get install mgetty

is a good start

Then you have to add a line in /etc/inittab to connect the serial line to mgetty.

Then you connect mgetty to ppp.

Take a look at the examples/documentation found in the mgetty package.

---

