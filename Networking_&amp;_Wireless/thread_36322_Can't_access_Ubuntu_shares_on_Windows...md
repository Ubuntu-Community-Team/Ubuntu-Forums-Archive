---
title: "Can't access Ubuntu shares on Windows.."
date: 2005-05-22
forum: Networking &amp; Wireless
---

### Post by veraction on 2005-05-22
Just installed samba and shared a folder on one computer. Using my other Ubuntu computer, I can access the shared folder over the network, but Windows is having problems.

On the Windows computer, I can see that that the folder is shared, however when I try to access it, I am prompted for a username/pass. I tried entering a few different ones -- my Ubuntu username/pass. I don't remember setting up a username or password for the share when I did System -> Administration -> Shared Folders to add the shared folder.

Any ideas?

---

### Post by XDevHald on 2005-05-22
[QUOTE=veraction]Just installed samba and shared a folder on one computer. Using my other Ubuntu computer, I can access the shared folder over the network, but Windows is having problems.

On the Windows computer, I can see that that the folder is shared, however when I try to access it, I am prompted for a username/pass. I tried entering a few different ones -- my Ubuntu username/pass. I don't remember setting up a username or password for the share when I did System -> Administration -> Shared Folders to add the shared folder.

Any ideas?[/QUOTE]
 This might be a wrong answer, but have you tried using the root password and root as the username? or maybe your user name and your password that logs you into the GDM desktop?

---

### Post by veraction on 2005-05-22
Just tried using 'root' as the username. Still nothing.

After I click on [OK] at the login prompt, it just flashes but doesn't do anything. The username changes from 'root' (for example) to USER/root (where USER is computer's name)

grr.. very annoying. My other windows comp can't even see any other computers on the network

---

### Post by petehall on 2005-05-24
Did you add your user account as a samba user?

smbpasswd -a 'username'

---

