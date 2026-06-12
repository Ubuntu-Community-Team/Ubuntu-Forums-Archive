---
title: "Couldn't parse the incoming data"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by Grayman on 2011-04-21
Been a while since I had Ubuntu on a system, finally decided to go back to this OS (10.10 release). I missed it, but feels like I'm starting over again. Anyway, here's my issue:

I have an LG Vortex android phone that I've paired with my Lenovo netbook via a Bluetooth connection. I can see the folders, and can send files to the phone and pull files from the phone for *most* of the folders on the phone. However, my Music folder gives me an error:

The folder contents could not be displayed.
Couldn't parse the incoming data

This happens on a couple of other folders, but the Music is the one I'm most concerned about. Any ideas what may be causing this and/or how to resolve it? Thanks for your time

-Gray

---

### Post by deathadder on 2011-04-21
A quick search found this bug report from [another thread]("http://ubuntuforums.org/showthread.php?p=9753374"). Can you check the characters in the file names like it says?

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/310231](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/310231)

---

### Post by Grayman on 2011-04-21
After searching through nearly a thousand folders, finally found one (1!!!) folder with the word "feat." 

Removed the period from that folder and everything works now. Thanks!!

---

