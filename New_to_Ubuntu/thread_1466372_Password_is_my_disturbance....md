---
title: "Password is my disturbance..."
date: 2010-04-30
forum: New to Ubuntu
---

### Post by munna.cheyur on 2010-04-30
I am a home pc user no one will touch my pc. in this case i dont want to make security much... but in ubuntu for administration tasks asking password continuously is there any way to do all works access everywhere without password...

---

### Post by P4man on 2010-04-30
You computer is connected to the internet, isnt it? So how do you know you are the only one using it!

---

### Post by mechro on 2010-04-30
Edit: Link removed


> If you disable the sudo password for your account, you will seriously compromise the security of your computer. Anyone sitting at your unattended, logged in account will have complete root access, and remote exploits become much easier for malicious crackers.	

> 
Please do not suggest this to others unless you personally are available 24/7 to support the user if they have issues as a result of running a shell as root.

---

### Post by tarps87 on 2010-04-30
There is however it is against the Forum CoC and there is a good reason for it. I would suggest reading this [documentation]("https://help.ubuntu.com/community/RootSudo"). You can disable password requests for things like installing software from the repos, but doing this for every command if some what dangerous

---

### Post by Paqman on 2010-04-30
> **P4man said:**
> You computer is connected to the internet, isnt it? So how do you know you are the only one using it!

+1

The only single-user machine is one that's not connected to anything. If it's on the internet then it's connected to billions of other machines and humans. You need good security.

---

### Post by ibuclaw on 2010-04-30
If you feel that you are always being prompted for a password, you are most likely not using/administering your system appropriately.

Unless your system is in a stage of flux (ie: where you are installing / uninstalling packages just to test and find right one for you) - then you should never really be constantly prompted to unlock root privileges.

If you need to use a string of administrative tasks over a brief period, try:
```
sudo -i
```
Instead.

Also, rather than unlocking password prompt for every applications in every conceivable location on your system, you can instead opt for a more fine grain control and configure sudo to allow only certain applications permission to run without prompt. See [http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)


Regards

---

### Post by 3177 on 2010-04-30
not cool
you should never have given him thatcode mechro

---

### Post by mechro on 2010-04-30
> **3177 said:**
> not cool
you should never have given him thatcode mechro

Eh? It was just a link to Ubuntu documentation. Same link was given by tarps87.

---

### Post by mechro on 2010-04-30
Hmm... the link about RootSudo says...

> If you disable the sudo password for your account, you will seriously compromise the security of your computer. Anyone sitting at your unattended, logged in account will have complete root access, and remote exploits become much easier for malicious crackers.	

> 
Please do not suggest this to others unless you personally are available 24/7 to support the user if they have issues as a result of running a shell as root.

I apologise for posting the link.

---

### Post by egalvan on 2010-04-30
> **munna.cheyur said:**
>  is there any way to do all works access everywhere without password...

Two ways come to mind...

1) Microsoft Windows XP.

2) Un-secure Linux.

---

