---
title: "LTSP problem?"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by sunnydevirus on 2008-10-21
I have an LTSP installation hardy 8.04. Yesterday.and i make sure i follow all the steps started in ubuntu web site and it was sucessful on the server side  I've not been able to login on the thin clients. I've run ltsp-update-sshkeys and ltsp-update-image i even used a third
machine to insure that users could perform an ssh login to
the server. initially it was this work station is not authorize to connect to server after much work arround is showing this. After entering the user's id and password on
the client I get "Verifying password, please wait". After a
few minutes the prompt for a user login id reappears. I've
tried generating new keys with ssh-keygen but that didn't
help. I can find no error messages in /var/log files. I
tried to a "failsafe xterm session" on the client but that
hasn't worked wither. Anyone have any ideas?
Please someone should please help/

---

### Post by faustino on 2009-01-15
I have the same problem with LTSP in 8.10. I've upgraded it from 8.04, where it worked fine and now i can't login from the thin clients. But my var.log has the following errors.

Jan 15 09:43:24 ubuntu-servidor sshd[7888]: Failed password for root from 192.16
8.0.250 port 38048 ssh2
Jan 15 09:43:24 ubuntu-servidor last message repeated 2 times
Jan 15 09:43:57 ubuntu-servidor sshd[7890]: Invalid user exp from 192.168.0.250
Jan 15 09:43:57 ubuntu-servidor sshd[7890]: Failed none for invalid user exp fro
m 192.168.0.250 port 38049 ssh2
Jan 15 09:43:57 ubuntu-servidor sshd[7890]: Failed password for invalid user exp from 192.168.0.250 port 38049 ssh2
Jan 15 09:43:57 ubuntu-servidor last message repeated 2 times

Can anybody help me please?

---

