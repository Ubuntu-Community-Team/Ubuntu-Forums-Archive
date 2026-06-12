---
title: "Samba smbpasswd location"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2010-11-18
Hey,

I'm setting up a samba server, nad I am in the process of adding users via the ```
smbpasswd -a USERNAME
``` command. It then automatically prompts for passwords.

Where is this information saved? I'd like to find out two things:
[1] What are my users? I need to be able to list the samba users
[2] Are the passwords kept in a safe place or are they accessible to users of the machine other than root?

All help is appreciated.

Thanks,
Kurt

---

### Post by jkurtisr32 on 2010-11-18
[http://ubuntuforums.org/showthread.php?t=363675](http://ubuntuforums.org/showthread.php?t=363675)

Found that, but I need to test.

---

### Post by jkurtisr32 on 2010-11-18
I found out that the passwords are kept safe. In my case, they are kept by some backend:
```
# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam
```
I still cannot find out how to list the users in the system, which should be easy. I tried the following:
```
pdbedit -Lw
```
in terminal, but it returns an error:
```
~$ pdbedit -Lw
tdbsam_open: Failed to open/create TDB passwd [/var/lib/samba/passdb.tdb]
tdbsam_getsampwnam: failed to open /var/lib/samba/passdb.tdb!
User Search failed!
```

So tell me... What should I do?
(please say above line in LeBron James's voice)

-Kurt

---

### Post by I8NY on 2010-11-20
Did you try running it with sudo? That fixed the problem for me.

---

### Post by endotherm on 2010-11-20
you can also always cat /etc/passwd, but you would have to filter out the service users.

---

### Post by jkurtisr32 on 2010-11-20
> **I8NY said:**
> Did you try running it with sudo? That fixed the problem for me.

My retardation has been taken to a whole new level. Wow... just wow.

As you may have guessed, this worked for me as well.

Thanks, man.

-Kurt

---

### Post by I8NY on 2010-11-20
Well we all do it some time. (i know i have) Your thread also helped me get samba users working for me so i'm glad we both learned something.

---

