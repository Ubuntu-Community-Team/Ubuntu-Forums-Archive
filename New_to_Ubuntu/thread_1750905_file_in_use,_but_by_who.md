---
title: "file in use, but by who?"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by wlraider70 on 2011-05-06
I'm trying to change a file. it appears to be in use, but i can't tell by what process.


this is the code. as i understand it, it should change the text in the file to 0.


server@hyrule:/proc/sys/net/ipv4/conf$ sudo echo 0 > /proc/sys/net/ipv4/conf/all/secure_redirects
-bash: /proc/sys/net/ipv4/conf/all/secure_redirects: Permission denied

Am I missing something or is there a way to discover why i cannot have permission?

---

### Post by ohadcn on 2011-05-06
try runing
lsof |grep /proc/sys/net/ipv4/conf/all/secure_redirects
to see which process use this file

---

### Post by wlraider70 on 2011-05-06
that code gave no results

server@hyrule:~$ ls |grep /proc/sys/net/ipv4/conf/all/secure_redirects
server@hyrule:~$

---

### Post by The Cog on 2011-05-06
The problem with this line:
> sudo echo 0 > /proc/sys/net/ipv4/conf/all/secure_redirectsis that it doesn't do things in the order you want - it tries to open the file for writing, and **then** runs "sudo echo 0". But you don't have write access to the file - sudo does but you never get as far as running sudo.
The easiest way round this is to temporarily get a proper root shell. Use these three commands:
> sudo -i
echo 0 > /proc/sys/net/ipv4/conf/all
exit

P.S.
I don't think the file is in use - you just don't have permissions to write to it as yourself.

---

### Post by matt_symes on 2011-05-06
Hi

Or another method...

sudo bash -c "echo 0 > /proc/sys/net/ipv4/conf/all/secure_redirects"

The file is not in use as such (well it is but...) but you cannot modify it the way you are trying to. This is why you are getting permission denied because you cannot modify it that way.

Kind regards

---

### Post by wlraider70 on 2011-05-07
> **The Cog said:**
> The problem with this line:
is that it doesn't do things in the order you want .

 
that makes sense. Just for reference how do i know it which order a command is executed. What i mean is that I was thinking is "sudo" is the first statement then it is run first. 
 
Would i run into a similar problem if i was trying to do other "dual-action" commands?

Thanks

---

