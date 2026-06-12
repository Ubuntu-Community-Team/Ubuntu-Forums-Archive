---
title: "Help with deleting files with an x on them"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by max00355 on 2010-12-28
i have this folder in my opt folder that i installed called Planeshift. its a game i installed and i need to get rid of it but i cant launch the game or unisnstaller because it says the file is untrusted. so i need to get rid of it but when i try to move it to trash it says it will be deleted but its not deleted. i also used the rm command in terminal which did nothing. can someone help me delete it and also for the future tell me how to get full root access and how to turn it off.

---

### Post by withnail420 on 2010-12-28
To get root access, in a terminal type "sudo su" and press enter. Then enter your login password and press enter again. You are now root.
You should try the rm command again as root.
If that doesn't work, maybe the drive is a little buggered and has gone into read-only mode (can't change anything on it). This happens occassionally. Try rebooting and trying again.

---

### Post by stmiller on 2010-12-28
max00355, simply preface your command with sudo:

```
sudo command
```

etc. Or better yet, try doing 'sudo uninstaller' whatever that may be called. Just deleting a directory may not in fact remove everything.

If you genuinely need a root shell, use

```
sudo -s
```

or 

```
sudo -i
```

---

### Post by max00355 on 2010-12-28
i tried all this but it says it cant delete it still

---

