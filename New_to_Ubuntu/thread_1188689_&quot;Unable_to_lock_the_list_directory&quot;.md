---
title: "&quot;Unable to lock the list directory&quot;"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by rhythmiccycle on 2009-06-16
i'm trying to run tor

i tryed following the steps on this page: [https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR) 

but when i made it to the last step, and when to the page: [https://torcheck.xenobite.eu/](https://torcheck.xenobite.eu/)

it says it not working.


so I decided to try the steps on this page:
[https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian](https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian)

when i type the code:
  $ apt-get update
it says:
"E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory"

what do i do?

---

### Post by laffinet on 2009-06-16
I believe you have to run this as root, in other words you should use
sudo apt-get update

---

### Post by SoftwareExplorer on 2009-06-16
It could also mean that some other apt (software package management) process is already running--only one can run at a time.

---

