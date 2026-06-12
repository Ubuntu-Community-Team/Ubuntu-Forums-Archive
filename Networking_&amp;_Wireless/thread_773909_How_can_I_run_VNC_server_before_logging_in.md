---
title: "How can I run VNC server before logging in"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by dickinsd on 2008-04-29
Hello,

I want to use my machine as a headless box.

I've got remote desktop working fine if I login to the ubuntu box and I have installed openssh-server which does let me connect to the Ubuntu box. The problem is that if I ssh to my ubuntu box I'm unable to start the vnc server.

ssh is working great for management - I can install and update remotely but when I want a GUI I need to hook a monitor, keyboard & mouse to my ubuntu box, login as me and then I can use remote desktop.

Basically I want to be able to start remote desktop or vnc server before the user login stage. I'm fairly sure this is possible as I did it a long time ago on a Fedora box but can't for the life of me remember how I went about it.

Cheers for any help.

Dave.

---

### Post by jtrindle on 2008-04-29
This thread is old but may be of help:

[http://ubuntuforums.org/showthread.php?t=191564](http://ubuntuforums.org/showthread.php?t=191564)

I haven't quite made this work yet.

A compromise would be to make sure you are using X forwarding in ssh, then you can run individual GUI apps that way.

---

