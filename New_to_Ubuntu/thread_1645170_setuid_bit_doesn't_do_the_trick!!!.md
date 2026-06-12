---
title: "setuid bit doesn't do the trick!!!"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by john77eipe on 2010-12-14
I have a folder "share"
```

eipe@eipe-john:~$ ls -l | grep share
drwxrwxr-t  2 eipe dev    4096 2010-12-13 21:07 share

```

and in share I have a executable file list.sh
```

-rwsr-sr-- 1 eipe egroup  3 2010-12-12 18:35 list.sh

```

There are 2 users in the picture - "eipe" and "tom". Both are member's of "dev" group.

I read that if setuid bit is set on a executable file it causes the program to run as it's owner, no matter who executes it. But when tom tries to run list.sh 
```

tom@eipe-john:/home/eipe/share$ ./list.sh
bash: ./list.sh: Permission denied

```

---

### Post by StephenDavison on 2010-12-14
Look at the group id for the directory and script, and group membership for the two users.  The users are group dev, but the script is owned by group egroup.  Change the group ownership on the script to dev or put your users in egroup.

---

### Post by john77eipe on 2010-12-14
yes it does work. 
```

tom@eipe-john:/home/eipe/share$ ls -l | grep list.sh
-rwxr-xr-- 1 eipe dev     3 2010-12-12 18:35 list.sh

```

After changing the group and making it group-executable, tom is able to run the file. 

But then what is the use of setuid?

---

### Post by StephenDavison on 2010-12-14
Setuid does what you think it does.  Your issue was not with the setuid, but with the ownership and/or execute permissions.  Making the script executable by all (rwxr-xr-x) would've allowed user tom to execute it with the script owned by group egroup (and tom in group dev).  In that case setgid would've made tom's effective group id egroup, and setuid would make tom's effective uid epipe.  

Your issue was that tom needs to be a member of the owning group (with execute permissions set for the group), or enable execute permissions for all users.

---

### Post by john77eipe on 2010-12-14
> In that case setgid would've made tom's effective group id egroup, and setuid would make tom's effective uid epipe. 

Hmm... I'm still confused with the real and effective user ID concepts. ](*,)

---

### Post by The Cog on 2010-12-14
I am under the impression that setuid doesn't work for scripts - only for binaries. I gather it's a security thing. I have in the past compiled small executables purely because a script with a one-line command in it won't do setuid.

---

### Post by StephenDavison on 2010-12-14
Edited to add:
Cog is right.  I missed that and was therefore wrong as can be!  I'm sorry for misleading and causing confusion.  Hopefully your confusion regarding effective and real id's was not caused by that.  Just in case not, the following was my original reply.  

Original post:
For example, look at /usr/bin/passwd which is owned by root with setuid  enabled.  The passwd command alters files owned and writeable by root  alone, but you as a regular user can alter those files through the  passwd command.

real:  your actual user/group ids
effective: the user/group ids you get for the duration of the process via setuid (root in the case of the passwd command)

This wiki entry includes an example showing real vs effective user id: [http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid)

---

### Post by john77eipe on 2010-12-15
Thanks... I'll post a example here.

---

### Post by john77eipe on 2010-12-15
I couldn't find any good resource googling that explains setuid well. Only one I found worthreading is,
[http://www.linuxjournal.com/article/7727?page=0,1](http://www.linuxjournal.com/article/7727?page=0,1)

> Now we come to two of the most dangerous permissions bits in the world of UNIX and Linux, setuid and setgid. If set on an executable binary file, the setuid bit causes that program to run as its owner, no matter who executes it. Similarly, when set on an executable, the setgid bit causes that program to run as a member of the group that owns it, again regardless of who executes it.

It seems it works on both executables and non-executables. I believe if setuid bit is set, then the file he is executing or opening to write should give him full privileges as that of the process.

Any thoughts :confused: ???

---

### Post by TeoBigusGeekus on 2010-12-15
["Setuid shell scripts are a major security hole, so that is not allowed by the kernel."]("http://aplawrence.com/SCOFAQ/FAQ_scotec1asroot.html")
You are [not]("http://www.dwheeler.com/secure-programs/Secure-Programs-HOWTO/avoid-setuid.html") encouraged to use setuid/setgid scripts.
There [are]("http://www.tuxation.com/setuid-on-shell-scripts.html") however workarounds if you insist.

---

### Post by john77eipe on 2010-12-16
Thanks. That explains everything. :P

---

### Post by john77eipe on 2010-12-16
> **john77eipe said:**
> 
It seems it works on both executables and non-executables. I believe if setuid bit is set, then the file he is executing or opening to write should give him full privileges as that of the process.


My bad! I didn't make any sense (above). 

It is true that the Linux kernel ignores the setuid and setgid bits on shell scripts. These bits work only on binary (compiled) executables.

---

