---
title: "SSH/SFTP Log - BASH"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Aysah on 2009-06-22
Hello everyone... Just a quick question in regards to sshd log events in /var/log/auth.log.  I'm fairly new to BASH Programming and I'm creating a quick service to only extract the sshd lines from the most current log.

After digging around the net I have found that the following grep command gives me EXACTLY the results I want but I can't really figure out how to print the results to a new file.
```

grep -H "sshd" auth.log

```

Can someone at the very least point me in the right direction on how to do this?  Thank you for all your help in advance.

---

### Post by HDave on 2009-06-22
grep -H "sshd" auth.log > /home/myself/newfile.txt

---

### Post by Aysah on 2009-06-22
> **HDave said:**
> grep -H "sshd" auth.log > /home/myself/newfile.txt

So stupid, I need to go bed lol.  Thanks again man, it works now!

---

### Post by HDave on 2009-06-22
Don't feel bad -- you did the hard part!;)

---

