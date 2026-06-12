---
title: "Suspend sudo"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by ahmed.hameed on 2011-05-11
Hi every one 

I am using eclipse in compilation and run mpi. 

so i have to make a make file write in it some command like 
mpicc -o myfile.o myfile.c 

I got some errors because i have to make sudo in the make file and when i made it i got anther one because eclipse have no program to automatic set sudo password. 

so my question about if there are any way to disable sudo for some commands or some programs ? 
That's all :D

---

### Post by Buntumatic on 2011-05-11
Yes, and it's all described in sudo man page.

---

### Post by ahmed.hameed on 2011-05-11
I read it but i didn't get what i need :(

---

### Post by wilee-nilee on 2011-05-11
> **ahmed.hameed said:**
> I read it but i didn't get what i need :(

sudo su

Use at your own risk, and read this link if you can it is informative.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Buntumatic on 2011-05-12
> so my question about if there are any way to **disable sudo** for some commands or some programs ? 
I misread your original post, you can enable passwordless commands in sudo, but you cannot **disable sudo**, because it is a nonsense. Sudo is to allow otherwise denied root access, not to restrict access to otherwise allowed access.

---

### Post by Buntumatic on 2011-05-12
> **wilee-nilee said:**
> sudo su

**su** is a command that allows to switch to another user, **su -** will switch also the environment.
It is not needed to gain root access, though.
[B]
sudo -i[/B] will log you on as root
**sudo -s** will give you root shell

Once more, it's all in **man sudo**

---

### Post by wilee-nilee on 2011-05-12
> **Buntumatic said:**
> **su** is a command that allows to switch to another user, **su -** will switch also the environment.
It is not needed to gain root access, though.
[B]
sudo -i[/B] will log you on as root
**sudo -s** will give you root shell

Once more, it's all in **man sudo**

Oh thank you oh so enlightened one what would I do without you.;)

---

### Post by Buntumatic on 2011-05-12
> **wilee-nilee said:**
> Oh thank you oh so enlightened one what would I do without you.;)
I'm sure you could do fine without me. People who ask their questions here are entitled to have the correct picture, though.
But if you wish me to stop posting on these forums your wish is granted. 
See, I was thinking these forums are about learning and improving Linux skills, and POSIX skills in general.
OTOH, if someone with so many posts thinks my quest for knowledge is a joke then I obviously misunderstood the very purpose of this site, it is just another social network, right? Bye ...

---

