---
title: "Check where symlink points from command line?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by rhcm123 on 2009-04-26
This should be relatively simple (famous last words :) ) - I made a simple bash script once upon a time to check the permissions of my /share directory, to make sure that nobody was accessing things they shouldent be.

I put a symlink to the script as /bin/share-chk, so that typing simply share-chk at the command line went to the script and ran it. However... i have now forgotten where i put the script, and need to find it.... :)

Does anybody know a command to follow a symbolic link to it's actual path?

---

### Post by freak42 on 2009-04-26
ls -l in the symlinks directory will show the path the symlink points to behind the entry. There might of course be more elegant methods I am not aware of.

---

### Post by doas777 on 2009-04-26
I may be missing a nuance particular to sym links, but i believe that ls -al will show <link location> -> <real location>

```

alpha10@21of2:~$ ls -al /usr/bin/ | grep java
-rwxr-xr-x  1 root   root        3120 2008-04-29 16:25 dh_javadoc
-rwxr-xr-x  1 root   root        2506 2009-02-19 14:32 dh_nativejava
-rwxr-xr-x  1 root   root        4872 2009-03-17 07:35 gjavah-4.3
lrwxrwxrwx  1 root   root          22 2009-04-23 21:29 java -> /etc/alternatives/java
lrwxrwxrwx  1 root   root          23 2009-04-25 17:21 javac -> /etc/alternatives/javac

```

also, in nautilus, you can right click any link, and select properties. look for the attribute "Link Target"

good luck

---

### Post by rhcm123 on 2009-05-06
> **doas777 said:**
> I may be missing a nuance particular to sym links, but i believe that ls -al will show <link location> -> <real location>

```

alpha10@21of2:~$ ls -al /usr/bin/ | grep java
-rwxr-xr-x  1 root   root        3120 2008-04-29 16:25 dh_javadoc
-rwxr-xr-x  1 root   root        2506 2009-02-19 14:32 dh_nativejava
-rwxr-xr-x  1 root   root        4872 2009-03-17 07:35 gjavah-4.3
lrwxrwxrwx  1 root   root          22 2009-04-23 21:29 java -> /etc/alternatives/java
lrwxrwxrwx  1 root   root          23 2009-04-25 17:21 javac -> /etc/alternatives/javac

```

also, in nautilus, you can right click any link, and select properties. look for the attribute "Link Target"

good luck

sorry, i never got the email for this - thank you very much, that worked perfectly. Turns out, it was actually /bin/share-chk, and not symlinked at all :D

---

