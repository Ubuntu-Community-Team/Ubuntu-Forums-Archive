---
title: "Controling the computers on my network"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by A1Cyber on 2008-11-12
Hello.
At school computers, we have installed edubuntu, and there are 5 or 6 computers on one network. Because I'm obliged from the profesor to control other students, what they do, and if they do something thats forbidden to close that.  I run the terminal and write
```

cd ..
ls

```
to see list of other users, and thats okey. That, which I need is if someone has runned Firefox, how to close Firefox? to restart/log out his/her computer? etc etc..

And another one question, is there way to find 'root' password to have more rights. Professors and the others from staff don't know the password.

Thanks in advance.
A1Cyber.

---

### Post by HermanAB on 2008-11-12
You cannot 'find' the root password, but you can reboot the machine into single user mode and then reset the password to something new.

---

### Post by Coreigh on 2008-11-12
To gain root level access you use the command sudo in front of what ever command you are running that needs privilege. Do a little reading about sudo on the Ubuntu Wiki or Google.

To execute remote commands I think you will need to use an ssh terminal to connect to the other computer to kill or re-spawn processes.

I am unfamiliar with edubuntu so they may actually have a utility just for this need.


Here is a link to the forums talking about sudo and its use:
[root login vs. sudo]("http://ubuntuforums.org/showthread.php?t=765414")

---

### Post by Iowan on 2008-11-12
As mentioned (or at least hinted), the standard Ubuntu has no root password because the root account is disabled (not sure about Edubuntu either).  Though it can be enabled, the referenced Forum policy "discourages" telling how to do so.  [Here]("https://help.ubuntu.com/community/RootSudo") is another explanation of RootSudo on Ubuntu.

---

### Post by sharon.gmc on 2008-11-12
I see.  Thank you for the info.. .Learning new things here. . .

---

### Post by A1Cyber on 2008-11-13
Thanks all. If someone have another variant please infor me. Thanks again.

---

