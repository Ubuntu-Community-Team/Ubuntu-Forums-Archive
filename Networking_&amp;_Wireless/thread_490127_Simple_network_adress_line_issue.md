---
title: "Simple network adress line issue"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by mrgeesbigcircus on 2007-07-02
This is probably going to sound pretty dumb to most people on here, but here goes:

I have two Ubuntu machines sat on my home network. One is a wireless laptop, the other is wired into the wireless router.

Coming from a Bill Gates past, browsing the files on another machine on the network was a simple matter of browsing to "\\192.168.1.xx".

Can anyone suggest what syntax I need to use in Ubuntu to do the same thing? I've hit a brick wall.

I was fully expecting being able to go to "Network" and see my other machine sat there a la Windows, but there's nothing there except "Windows Network".

Many thanks in advance!

---

### Post by mrgeesbigcircus on 2007-07-02
Hmm, thought this might have been an easy one but obviously not! :(

---

### Post by Austin_KW on 2007-07-02
You can browse files that windows PCs are sharing but to turn on file/printer sharing you need to install samba. Use synaptic and search for samba

or from the command line "sudo apt-get install samba"

A search of the forums will yield lots of example howtos to configure samba,eg.  look at [http://ubuntuforums.org/showthread.php?&t=202605](http://ubuntuforums.org/showthread.php?&t=202605)

---

### Post by mrgeesbigcircus on 2007-07-03
Thanks Austin, but I already have Samba set up and able to see the files on the Windows machines on my network.

What I need is the correct syntax for browsing to the other Ubuntu machine. (i.e. the equivalent of the windows address line "\\192.168.1.xx\c$" for example).

---

### Post by kevdog on 2007-07-03
What does smbtree produce for output?

---

### Post by Austin_KW on 2007-07-03
Not sure I understand you problem,

Your file browser (nautilus for gnome, konqueror for kde) has an smb plugin that allows you to browse the samba network. Just go to places->network or places->remote places

Or install smbfs and mount the share "mount -t smbfs //192.168.1.xx/SHARE /path/mountpoint" Then browse /path/mountpoint

---

