---
title: "Share file from ubuntu desktop to laptop?"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by joey-elijah on 2008-11-22
How would i go about setting this up? Both run Ibex. (Yes i have wifi lol)

ALSO!

I used to easily be able to access files on Vista via my ibook, is it possible to do the same but with Ubuntu in place of Vista?

i'm a bit of a n0ob when it comes to networking, so be gentle!

---

### Post by eks on 2008-11-22
There are lots of solutions for your question. The one I use is:

. install openssh-client on both computers
. type sftp://<othercomputerip> on Nautilus address bar

That's it :)

This is the most simple to setup, but not the most "pretty".

If you need more detailed explanation, for the first step you go to System/Administration/Synaptic Package Manager and search for that package (or just for 'openssh', or even just 'ssh', but use SEARCH, not quick search). Mark it and click Apply.

For the second step, Nautilus is the file manager for Gnome, the one where you browse the files. There's a button, generally bellow the "back" button, that toggles between a text-based and button-based location bar. Make it text based and type sftp://<othercomputerip>, you will be asked a login/passwd for the other computer and that's it.

To find out the computers ip right click over the network icon and select connection information. Or open a terminal and type "ifconfig".

---

### Post by joey-elijah on 2008-11-22
wow. it was all too easy! thanks for ur reply, but i stumbeled upon sorting it out by accident.

just right clicked a folder i wanted to share, clicked share - et voila! tiger picks it up, xp picks it up and ubuntu picks it up! 

sooooooo much eassier than sharing thru windows aswell!thanks!

---

