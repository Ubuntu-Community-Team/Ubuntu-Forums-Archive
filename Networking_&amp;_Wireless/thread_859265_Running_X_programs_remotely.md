---
title: "Running X programs remotely"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by juaninse on 2008-07-14
I am having a bit of trouble running remotely X applications.  Several years ago I did manage to run programs on the university Unix system and displaying them on my local machine, and I am pretty sure I am following the sames steps, more or less (the main difference being that I used to log into the remote machine with telnet, while now I did it over ssh: could that be the problem?  Is there an additional step to take in this case?).

To clarify, I have my remote computer called "marco-polo" and my local computer called "the-cid".  Using "ssh -X " I login to "marco-polo" into which I type the following lines:

export DISPLAY=the-cid:0.0
xterm & 

and I get the following error message:

xterm Xt error: Can't open display: the-cid:0.0

I have tried all permutations of the hostname.  With and withoud domain name ".lan", and also simply using the IP address.  Also on the host machine I have run 

xhost +

I have also temporarily disabled the firewall on the DSL modem/router to make sure that it wasn't blocking the communication.  Nothing else occurs to me to let program run remotely.  I have even tried to loging using telnet instead of ssh and got the same error.  

Any help on the subject would be greatly appreciated.

---

### Post by timcredible on 2008-07-14
check to make sure the server knows where el-cid is.  from the server [code]ping el-cid[/quote]if that doesn't ping, then using your ip address instead.

---

### Post by juaninse on 2008-07-14
Yes, I have tried using the IP address instead of the server name.  I get exactly the same response.

---

### Post by juaninse on 2008-07-14
Problem solved.  Solution:

just log into the remote computer using ssh, and call the program from the shell.  Apparently, it is not necessary to set the Display variable when logging in via ssh.  At least with current Ubuntu distros.

---

