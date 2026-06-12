---
title: "can't turn off password for SSH"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by mgm2rr on 2008-10-17
Hey, I have SSH set up on my Ubuntu machine, and I just set up public and private keys to login so I could have better security than just passwords.  The key-based login works, but I can't seem to turn off the password based login.  If I remotely log in, I can get in without using any key if I enter my name and password.  I edited the /etc/ssh/ssh_config and /etc/ssh/sshd_config to say "PasswordAuthentication no" and UsePAM no, but I still am able to log in with username and pw.  Any ideas?

---

### Post by mgm2rr on 2008-10-17
Never mind, I just had to restart ssh.  I am a lazy bum.

---

