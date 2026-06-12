---
title: "Disable password prompts?"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by yellowstoned on 2009-11-08
Can you disable all password prompts in linux? I am trying to work my way around getting a tx1000 hp laptop set up and I really tire of typing my password over and over for each step.
Thanks :D

---

### Post by 3rdalbum on 2009-11-08
Not in any safe manner.

---

### Post by KeiththeMusic on 2009-11-08
Yeah i'm not sure you want to do that.

---

### Post by The Funkbomb on 2009-11-08
That's a very important security feature.  I'm sure it's possible but I wouldn't do it.

---

### Post by 3rdalbum on 2009-11-08
You only need your password to elevate to root. Once your system is set up the way you like it, there's very little that needs to be run as root, so you'll only rarely be asked for your password.

---

### Post by perixx on 2009-11-10
isn't there a new feature in the password dialog in karmic, which will remember your password for gui apps per session or forever?

there's also the possibility to open a terminal and enter
```
sudo -i
```
and password ONCE, leaving the terminal in superuser-state. 
very handy for installation procedures.

---

### Post by alphaniner on 2009-11-10
You can modify your sudoers file with **sudo visudo** to disable prompts *almost* universally.  I do this at work where security is not really a concern.  No way would I do it on a personal machine though.

---

### Post by SunnyRabbiera on 2009-11-10
Passwords are there for a reason, wonder why windows has a million viruses and security issues?
well having no passwords is a good start.

---

### Post by perixx on 2009-11-10
passwords alone won't make a secure system, if it's in a network.

a major problem are superfluous running services listening on ports and buggy or malicious applications, though, which windows has quite some of.

considering linux is including more and more services like avahi and many more or less buggy (or worse) applications can be installed by users from arbitrary repositories (may it be proprietary or not), it might not be long before rootkit- and virus-threats increase considerably.
also, potentially unsafe apps like wine or skype can definitely compromise a system's security, or even badly written graphics drivers, as could be seen. 

by the time linux acquires a little higher market share (currently around 1% on desktop pc's), the number of malware and discovered security holes will surely rise. supposedly, the newly implemented parts of selinux won't change that. 

an example of a false security feeling is the mac os.

---

### Post by lavinog on 2009-11-10
> **yellowstoned said:**
> Can you disable all password prompts in linux? I am trying to work my way around getting a tx1000 hp laptop set up and I really tire of typing my password over and over for each step.
Thanks :D

How often are you needing to type your password?
Are you using the terminal or gui apps?
Are you refering to login password prompts, or sudo password prompts?

---

