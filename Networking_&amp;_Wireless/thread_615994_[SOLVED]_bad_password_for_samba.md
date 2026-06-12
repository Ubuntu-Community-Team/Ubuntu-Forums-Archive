---
title: "[SOLVED] bad password for samba?"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by Excalibre on 2007-11-17
I want to enable samba so that I can access a shared folder from within a virtual machine running Win2k but I don't seem to be able to do so. When I try to connect to my real computer from the 'network neighborhood' in Win2k it claims I have a bad username or password; I even tried creating a new user just for this purpose but it still complains, so I can't access the shared folder. :confused:

---

### Post by Excalibre on 2007-11-20
Okay, someone here HAS to have used this, and if they got it working they know more than me about it. Why won't anyone answer my freaking question?

---

### Post by jshurst on 2007-11-20
Can you explain the steps that you took to enable samba file sharing (sharing a specific folder, creating users, etc)?

I haven't enabled samba in a while, but I did a "sudo aptitude install samba".  Then use the terminal to create a new samba user, etc.

Samba users can be different from normal ubuntu users.

J

---

### Post by Excalibre on 2007-11-20
Wait, do I have to create a user specific for Samba, not just a user for my machine? If that's the case, I haven't done so. I've been trying to use the usernames and passwords of regular users.I installed it via one of the system administration doohickeys (forget which one) and set directories to be shared via the 'shared folders' one. I didn't have to install anything - I don't remember whether it launched synaptic or not, though I suppose it must have.

Note that my windows virtual machine has no trouble finding the shared folder, just logging in.

---

### Post by jshurst on 2007-11-20
Let's create a samba user.  Do the following.

sudo smbpasswd -a username  
Replace username with whatever username you want - you can use your regular Ubuntu user.  Then enter your password for the newly created user.  Then try to connect again...

J

---

### Post by Excalibre on 2007-11-20
Thanks! I knew it had to be something simple like that but I didn't know what. So I take it users for Samba have nothing to do with users for my computer? Anyway, it worked, the shared folder is now accessible from the virtual machine. Thank you!

---

### Post by jshurst on 2007-11-20
Correct, samba users are different than normal users.

NP, glad to help.

J

---

