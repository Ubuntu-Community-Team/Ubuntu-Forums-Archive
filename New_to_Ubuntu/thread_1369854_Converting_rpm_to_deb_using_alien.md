---
title: "Converting rpm to deb using alien"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by ReZeeR on 2010-01-01
rezeer@rezeer-desktop:~$ sudo alien -k /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
error: incorrect format: unknown tag
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
Warning: Skipping conversion of scripts in package MySQL-server: postinst preinst prerm
Warning: Use the --scripts parameter to include the scripts.
warning: /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm: Header V3 DSA signature: NOKEY, key ID 5072e1f5
chown: cannot access `MySQL-server-5.5.0//etc/my.cnf': No such file or directory
failed chowning /etc/my.cnf to 0:0: Illegal seek at /usr/share/perl5/Alien/Package/Rpm.pm line 265, <GETPERMS> line 3.
 

Still new to linux :)

---

### Post by CharlesA on 2010-01-01
The switch is -i to convert an rpm to a deb.

```
sudo alien -i --scripts /home/rezeer/Desktop/MySQL-server-5.5.0-0.glibc23.i386.rpm
```

Also: Why aren't you installing MySQL from the repos?

---

### Post by ReZeeR on 2010-01-01
tried using -i instead of -k still got 

chown: cannot access `MySQL-server-5.5.0//etc/my.cnf': No such file or directory
failed chowning /etc/my.cnf to 0:0: Illegal seek at /usr/share/perl5/Alien/Package/Rpm.pm line 265, <GETPERMS> line 3.

at the end


sorry mysql from repos ???:confused:
newbie to linux

---

### Post by CharlesA on 2010-01-01
Strange. Sounds like a permission thing, but if you are in your home directory, that shouldn't be a problem.

Try this instead: Go to Synaptic and search for mysql-server.

or

run this in a terminal:
```
sudo apt-get install mysql-server
```

---

### Post by LuisGMarine on 2010-01-01
```
sudo apt-get install mysql-server
```

Run that bad boy in a terminal =)

---

### Post by ReZeeR on 2010-01-01
ok that was easy ^^ Thanks!
New question though: How do i configure it to be a multi transactional,dedicated server. It supposed to be used for a gaming. I know how it works on windows but no idea here

---

### Post by CharlesA on 2010-01-01
That I don't know.

---

### Post by cocodude on 2010-05-05
> **ReZeeR said:**
> chown: cannot access `MySQL-server-5.5.0//etc/my.cnf': No such file or directory
failed chowning /etc/my.cnf to 0:0: Illegal seek at /usr/share/perl5/Alien/Package/Rpm.pm line 265, <GETPERMS> line 3.

at the end

Although I know this thread is a few months old, I noticed this error in Lucid, and the patch at [https://bugs.launchpad.net/ubuntu/+source/alien/+bug/507326](https://bugs.launchpad.net/ubuntu/+source/alien/+bug/507326) helped me out.

---

