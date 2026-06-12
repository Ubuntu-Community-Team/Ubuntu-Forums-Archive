---
title: "firestarter/security question"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by dj22g on 2009-01-16
Hello. I am using Hardy and have firestarter installed. I noticed under active connections that a program called "sh" was maintaining an active connection. Is this typical? What is this program and why would it need an active connection? 

What is a good way to determine if spyware is installed on my computer? How can I determine if an active connection is suspicious?

Thanks

---

### Post by zzHanks on 2009-01-16
Hi.
This is maybe not the answer you are looking for but Ubuntu has a built-in firewall with all ports closed by default. To enable it type ```
ufw enable
```You need to be root to do that. Type ```
sudo -i
```

---

### Post by Paqman on 2009-01-16
> **dj22g said:**
> 
What is a good way to determine if spyware is installed on my computer?

If you've only ever installed software from the repos, you don't have spyware. Guaranteed.

---

### Post by jerome1232 on 2009-01-16
@zzHanks: Both ufw and firestarter configure the same thing, iptables...

@dj22g: Is this a program that's listening for connections or just maintain an active connection?

sh is the default shell, say I wanted to run a script with ubuntu's default shell (which happens to be bash btw) I would run the script in a terminal like this "sh scripttorun"

Did you perhaps run script that need to open up a connection?

---

