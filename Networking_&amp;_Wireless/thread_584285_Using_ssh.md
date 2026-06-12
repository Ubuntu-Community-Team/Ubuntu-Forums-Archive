---
title: "Using ssh"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by kwandar on 2007-10-20
I have two computers, that I'm trying to establish an SSH connection on, in the far fetched hope that I can figure out how to run VirtualGL.  If it works, the plan is to buy a server that can be accessed from everywhere, and my wife can have her Windows for school, via a virtual machine.  Our current computers couldn't handle virtualizing Windows.

As I mentioned, I need to establish an SSH connection, and being an absolute beginner in this area and only limited networking knowledge, the learning curve is steep - help! :)

I installed open SSH from the Ubuntu repositories on the server and client on both machines.  I then went into a terminal window and did 

sudo ssh -w geek@192.168.0.105 from the second computer

I got a message back about "no tun".  Do I have to configure the SSH after it is installed?  Can anyone give me (or direct me to) dumbed down instructions on how to do this?  

Has anyone else got VirtualGL working?

---

### Post by ubernoob on 2007-10-20
"-w" means you have to tunnel som ports, which you havent. Beside, you don't need to "sudo" when you use ssh.

Have you installed ssh server?

Try: ssh geek@192.168.0.105

---

### Post by khaije1 on 2008-05-25
> **kwandar said:**
> I have two computers, that I'm trying to establish an SSH connection on, in the far fetched hope that I can figure out how to run VirtualGL.  If it works, the plan is to buy a server that can be accessed from everywhere, and my wife can have her Windows for school, via a virtual machine.  Our current computers couldn't handle virtualizing Windows.

As I mentioned, I need to establish an SSH connection, and being an absolute beginner in this area and only limited networking knowledge, the learning curve is steep - help! :)

I installed open SSH from the Ubuntu repositories on the server and client on both machines.  I then went into a terminal window and did 

sudo ssh -w geek@192.168.0.105 from the second computer

I got a message back about "no tun".  Do I have to configure the SSH after it is installed?  Can anyone give me (or direct me to) dumbed down instructions on how to do this?  

Has anyone else got VirtualGL working?
kwandar, I'm trying to figure how to get started with virtualGL as well (my [plea]("http://ubuntuforums.org/showpost.php?p=5036824&postcount=8"))

---

