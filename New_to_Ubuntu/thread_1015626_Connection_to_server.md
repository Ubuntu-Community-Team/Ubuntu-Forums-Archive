---
title: "Connection to server"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Archer Troy on 2008-12-19
Hey all,

Im trying to share hard disks between my wired network computers, 1 running Kubuntu 7.10 and the other running ubuntu 8.10. Whenever i attempt to connect the 2 computers it gives me an error. Im trying to connect through the "connect to server" option in Ubuntu. Ive triple checked that all the info im putting in is correct. the error i recieve is 

Cannot display location "sftp://username@192.168.1.101/" Timed out when logging in. 

Would really appreciate a few pointers, Thanks guys

---

### Post by iaculallad on 2008-12-19
Using the Nautilus location bar as an alternative, try to input the following string below and press the Enter key.

> smb://192.168.1.101

It will prompt you to enter your valid username, password, and domain.

---

### Post by Archer Troy on 2008-12-19
roman@roman-desktop:~$ smb://192.168.1.101 
bash: smb://192.168.1.101: No such file or directory

this is what i get. any idea?

also. something i just thought of. both usernames for both computers are the same...could that be causing the problem?

---

### Post by iaculallad on 2008-12-19
The command, **smb://192.168.1.101**, I suggested on my first post was not intended to be executed on the terminal. Use/Open a Nautilus window and place that **string** on the location bar.

---

### Post by Archer Troy on 2008-12-19
I dont think I have nautilus, but i input smb://192.168.1.101 into firefox and pressed enter and it loaded for a while, then nothing happened. where do i find nautilus?

---

### Post by Archer Troy on 2008-12-19
nevermind, figured out what nautilus is, still nothing shows up tho...

gives me the same error

Cannot display location "sftp://Roman@192.168.1.101/"

---

### Post by Kareeser on 2008-12-19
... Do you have an sFTP server running on the Xubuntu box?

If so, please tell us about your config, posting config files as necessary :)

---

