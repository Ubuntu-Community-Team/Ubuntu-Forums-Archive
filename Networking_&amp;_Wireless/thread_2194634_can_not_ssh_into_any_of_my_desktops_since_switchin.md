---
title: "can not ssh into any of my desktops since switching to 13.10"
date: 2013-12-19
forum: Networking &amp; Wireless
---

### Post by larka51-aol on 2013-12-19
All I get is a connection refused. They have changed ssh so I am not sure what to do. Oh! I did open port 22 on both computers.  Could it be aparmor?

---

### Post by tfrue on 2013-12-20
Just to be clear, you are trying to SSH into a Desktop from your PC that is running Ubuntu 13.10, right? Or is it the other way around were the desktops cannot SSH into your PC that is running 13.10? Try and be more clear, thank you. Also, post some pictures of the command you type and the error you are getting. Please and thanks!

---

### Post by Lars Noodén on 2013-12-20
What is the status of the SSH server on the machine you are trying to log into?

```

service ssh status
dpkg -l openssh-server

```

---

### Post by larka51-aol on 2013-12-24
[**[COLOR=#000000]chris_johnson2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1865338") it is from one 13.10 to another 13.10

---

### Post by Lars Noodén on 2013-12-25
Ok.   Can you show the output from [service](http://manpages.ubuntu.com/manpages/saucy/en/man8/service.8.html) and [dpkg](http://manpages.ubuntu.com/manpages/saucy/en/man1/dpkg.1.html) as shown above in #3 please?  Run them on the target machine so we can know the status of the SSH server.

---

