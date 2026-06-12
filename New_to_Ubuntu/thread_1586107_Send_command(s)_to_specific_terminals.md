---
title: "Send command(s) to specific terminals"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by Blutkoete on 2010-10-01
Hello!

I'm using a stand-alone MATLAB license at home and an account on a cluster at the university. I'd like to be able to program myself a MATLAB script to send commands directly from my home workspace to the cluster.

As I'm able to execute system commands from within MATLAB, the idea is the following:

a) open the SSH connection
b) send the commands

My question: Is it possible to open one terminal and send commands from there to a different terminal? 

This might be a little beyond the "absolute beginner" scope, but maybe someone can point me to a tutorial or a manual.

Thank you very much,

Blutkoete

---

### Post by luvshines on 2010-10-01
You can send the commands to an ssh terminal like:
ssh user@<ip/host-name> "command"

The command itself may consist of ssh again:

ssh user@<ip-1> "ssh user@<ip-2> <command2>"

---

### Post by Blutkoete on 2010-10-01
Thank you!

That's even easier than I thought. Now I just need a way to provide the password so that I don't have to type it everytime.

**EDIT:** "sshpass" does the trick.

---

### Post by luvshines on 2010-10-01
You can also setup 'password less' ssh between the machines to avoid using passwords as cleartext in the program itself

You have to google a bit though. If the cleartext password is not an issue, then sshpass is fine

---

### Post by Blutkoete on 2010-10-01
I think I should talk to the university's system admin about that. 

At the moment sshpass reads the password from a file to avoid simple "ps" attacks on it (well, nobody else uses my computer, but you never know).

Thanks for the hint with the SSH without passwords.

---

