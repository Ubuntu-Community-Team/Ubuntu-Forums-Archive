---
title: "Stop gnome-session, kill x-server from tty1 How?"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Anaphylaxis on 2009-12-19
UNIMPORTANT BACKGROUND HISTORY: Setting up ubuntu, and copying over the fedora-home folder gave me some permission-problems, and removing my user, and adding it again with useradd, left me with a frozen screen upon logging in. 

PROBLEM: Pressing Ctrl + Alt + Delete doesn't do jack. I can enter the virtual terminals. I would like to log out my user with the frozen session and login as another user, then start gnome session for another user. How can I do this from a virtual terminal?

---

### Post by nerdy_kid on 2009-12-19
sudo service gdm restart
or if you are using jaunty
sudo /etc/init.d/gdm restart

---

### Post by Anaphylaxis on 2009-12-19
Thanks a lot. Beats restarting the computer any day.

---

