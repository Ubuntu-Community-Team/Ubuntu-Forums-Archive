---
title: "Sharing without a password"
date: 2005-09-13
forum: Networking &amp; Wireless
---

### Post by cbudden on 2005-09-13
hello.  How can i allow sharing of a folder without a password being needed, as when i try to access my Ubuntu shares using samba but 98 asks for a password and is connecting using IPC$.  How can i prevent a password being needed?

---

### Post by s_p_a_r_k_y on 2005-09-13
look in your samba config file nano /etc/samba/smb.conf and look for security
I think by default its set to user and you'll want to change it to share (someone correct me if I'm wrong). Then restart samba /etc/init.d/samba restart

You will need to edit the file and perform ther restart command from the command line as root, so preface each one with sudo and type in your pass

---

