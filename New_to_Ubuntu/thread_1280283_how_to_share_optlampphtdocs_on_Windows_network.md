---
title: "how to share /opt/lampp/htdocs on Windows network?"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by flameproof on 2009-10-01
how to share /opt/lampp/htdocs/ on Windows network?

I like to edit php files from my Xp machine via the network on the Ubuntu 9.04/64 machine.

Tried so far:
gksudo nautilus didn't work
setting /opt/lampp/htdocs/ "share" didn't work (Xp will ask for a password which I don't have)

Accessing the /home/ directory is no problem read + write.

How can I edit files in /opt/lampp/htdocs ?

---

### Post by SoftwareExplorer on 2009-10-02
Did you set the share to have writing and did you allow Guest access? Because if you set it to use guest access, the password and username is 'Guest' for the username and a blank password.

---

