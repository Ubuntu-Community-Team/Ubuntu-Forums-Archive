---
title: "[SOLVED] Remember Root Password Forever?"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by efexD on 2009-01-03
Is there a way to either remove the password, or just make ubuntu remember it forever? It's very annoying when things get permission denied all the time and i have to put in the password every time.

---

### Post by adult swim on 2009-01-03
you are going to have to google.  its against forum rules to discuss this.

---

### Post by efexD on 2009-01-03
oh... didn't know it was against the rules... sorry

---

### Post by thomas228 on 2009-01-03
> **adult swim said:**
> you are going to have to google.  its against forum rules to discuss this.

Hi
Please link or quote the specific rule or policy (policies) as I can't seem to find them.

Thanks and no disrespect intended

Tom

---

### Post by Cypher on 2009-01-03
Disabling the root account and making the regular user account use SUDO to access system level commands is there for your protection. Each time you have to enter the password, it's a reminder to check to see what command it is you are running and if it's safe.

You can certainly disable that layer of protection and deal with any bad consequences yourself by modifing the /etc/sudoers file.

You'll see a commented section towards the bottom that is
```

%sudo ALL=NOPASSWD ALL

```

This allows you to run system commands with the SUDO command without requring you to enter the password. The commands you run will be logged in /var/log/auth.log so you can keep track, but no other checking is done.

Use at your own risk..

---

### Post by efexD on 2009-01-03
Thanks, but now i don't want to pay the consequences of screwing my system up :P

---

### Post by Sef on 2009-01-03
For anyone who wants to read up on [root and sudo]("https://help.ubuntu.com/community/RootSudo").

> You'll see a commented section towards the bottom that is
 	Code:
 	%sudo ALL=NOPASSWD ALL 
This allows you to run system commands with the SUDO command without requring you to enter the password. The commands you run will be logged in /var/log/auth.log so you can keep track, but no other checking is done.

That and this is from [Root Sudo]("https://help.ubuntu.com/community/RootSudo") in the community documents:

> 
[LIST]
[*]**This method is NOT suggested nor supported by the designers of Ubuntu.** 
[*]Please do not suggest this to others unless you personally are available 24/7 to support the user if they have issues as a result of running a shell as root. 
[/LIST]
These instructions are to remove the prompt for a password when using the **sudo** command. The **sudo** command will still need to be used for root access though

---

### Post by Cypher on 2009-01-03
> **efeXor said:**
> Thanks, but now i don't want to pay the consequences of screwing my system up :P
Wise decision. :) As cumbersome as it might seem to have to enter your password with SUDO/GKSU and so on, it's really there to protect you..

---

### Post by Captain_tux on 2009-01-03
> **efeXor said:**
> Is there a way to either remove the password, or just make ubuntu remember it forever? It's very annoying when things get permission denied all the time and i have to put in the password every time.

Yes... just run Windows :biggrin:

---

