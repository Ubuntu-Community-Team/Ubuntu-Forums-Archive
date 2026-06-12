---
title: "Sudo error"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Omegaxis on 2009-02-11
I'm running Ubuntu 8.10
Whenever I try to run anything involving adiminstrative privileges In my intial user account, I get either a sudo error, or an access denied message.

---

### Post by Archmage on 2009-02-11
You need to be in the sudo-group and than need to enter your password to perform any task that involves root-rights.

To test this, you can go to the terminal, enter the below command and paste the output.

```
sudo ls
```

---

### Post by Omegaxis on 2009-02-11
Terminal isn't working from the applications menu, so I have to hit ctrl+alt+f1, so I can't copy and past. 

Anyways, it says 
```
<username> is not a sudoers file, this incident will be reported.
```
I just tried
```
adduser <username> admin
```
And that didn't work.
I also checked, and my username is listed in the admin group. 
Yet I still get the same error.

---

### Post by Omegaxis on 2009-02-11
Fixed, I add myself in manually with visudo

---

