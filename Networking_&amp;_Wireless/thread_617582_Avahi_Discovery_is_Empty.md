---
title: "Avahi Discovery is Empty"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by roadcone on 2007-11-19
I found this problem while trying to use DAAP to share music with my Ubuntu lappy to my desktop. The desktop would not find the music. I opened Avahi Discovery to find that it cannot discover any services at all form my desktop; the music share, remote desktop, the workstation, etc. The desktop can get on the internet, but it does not seem to register in the network at all. Any ideas? The laptop I can shell into itself, and connect to itself with VNC, but the same things on the desktop don't work.

"
jared@zweitepanzer:~$ ssh localhost
Read from socket failed: Connection reset by peer
"

If that helps at all? The same services are enables, avahi-daemon is installed and running, just.. I get nothing.

---

