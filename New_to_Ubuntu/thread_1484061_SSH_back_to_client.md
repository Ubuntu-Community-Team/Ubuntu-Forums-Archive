---
title: "SSH back to client?"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by m0116815 on 2010-05-15
Hi all,

I suspect what I want is not possible :)

First a tad of background: I'm using a tiny netbook (running Ubuntu netbook remix) to log in to a cluster (running Debian) where I run simulations, using MATLAB. I move around a lot so sometimes the connections is slow, so I'm always looking for bandwidth-efficient solutions.
I map my home folder on the cluster to my netbook with sshfs and use Geany for file editing. I'm really enjoying the terminal that's in the Geany interface because it allows me to run MATLAB on the remote cluster in the same window. So far, everything runs smoothly. One pet peeve was that I couldn't use that terminal to open files for editing in Geany while I'm logged on to MATLAB, so I wrote a function that uses ssh to let the cluster tell my netbook to open a file (from the sshfs folder) in Geany. This works only if I know which public port on whatever router I'm behind forwards to my netbook. Problem is that I don't always know that. I can see the IP of the ssh client of course, but not how to access the ssh server running on the client (netbook).

So, the question is: given that
1) I'm ssh'ing from A to B
2) I have admin access rights on A (but not on B)
can I ssh into the client from the server if I don't know what port to use?

I don't know what the security issues here could be, so I don't know if it is possible, but the fact that the env variables "SSH_CLIENT" and "SSH_CONNECTION" seem to contain more info than just the IP gives some hope...

Thanks in advance!

---

### Post by slibuntu on 2010-05-15
It's likely there's a firewall restriction that is blockling you from SSH'ing back to the client. Can you check is port 22 open on your end and that the Netbook IP address is visible to the cluster?

---

### Post by m0116815 on 2010-05-16
> **slibuntu said:**
> It's likely there's a firewall restriction that is blockling you from SSH'ing back to the client. Can you check is port 22 open on your end and that the Netbook IP address is visible to the cluster?

Hi, thanks for replying. Port 22 is open, and **if** I'm at home I know that port 22 is open on my own router, and then the ssh'ing works without a problem. Also, another public port (2022) forwards to my home desktop, and I can get the cluster to ssh back to that just fine. The problem occurs when I'm **not** at home (but, say, at the airport) and don't have access to the router to set port forwarding.

---

### Post by m0116815 on 2010-05-26
:)

---

