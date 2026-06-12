---
title: "How can I access a .Private folder from another system?"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by Afanluc on 2009-12-11
I have installed Ubuntu on a pendrive (complete install, not just livecd). There, I took the option to use a encrypted home folder. It is Ok when I log in with the pendrive, but I want to know if there is a way to access that same folder, when I log in at the ubuntu I have installed on my Desktop computer, and then I plug in the usb. Obviously, I know the password for the encrypted folder, I just dont know how to mount it. I tried "encryptfs-mount-private" but it says "ERROR: Encrypted private directory is not setup properly". How can I mount it from the other system???
Thanks in advance

---

### Post by abeisgreat on 2009-12-11
That is a fantastic question, which I don't know the answer to.

I had the encrypted dir setup on a machine awhile back, but I can't recall anything about how it's setup, or if you could theoretically issue the command from a third party. But it must be possible. I'm curious what other people will say.

---

### Post by joes7 on 2009-12-11
Log in as "root".

```

Log In: Root
Password: the one you indicated during the installation process

```

---

### Post by SaintDanBert on 2009-12-11
> **Afanluc said:**
> 
...
I took the option to use a encrypted home folder. It is Ok when I log in with the pendrive
...
How can I mount it from the other system???


Access to anything always boils down to permissions or the associated feature access control lists (ACL).  Let's ignore ACLs for now.
Here is a situation so that we have something to talk about.

You login as user 'afanluc'.  Open a shell and type the 'id' command.
You will see something like this:
```

... login as afanluc
user@host:~$ id
uid=1001(afanluc) gid=1001(afanluc) groups=1001(afanluc)
user@host:~$

```

Every process, even those run as system services has its own ident information because of the associated "uid" (user id) and "gid" (group id). You can see these with the 'top' 'htop' or 'ps' commands. By default you see process that your login "owns". Use 'sudo ps' or similar to see all of the processes on the running system.

Now every device, folder, and file has associated ownership and permissions.  Use the 'ls -l' command to see the owner and permission information.

To access file on computer-B from a process on computer-A, you must arrange so that your process on computer-B arranges to run a program on computer-A that has the correct permissions to read, write, or execute the files over there somewhere.

Take a look at permissions and ask more questions.  I suggest that you create a unique "group id" for your files. Put your user into this group on both computers and arrange for your utilities to run as a member of that group.

Cheers,
~~~ 0;-Dan

---

