---
title: "Not receiving security updates for many days in ubuntu jaunty"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by t_k_majumdar on 2009-05-29
I am not getting any security updates for 23 days now.  Synaptic package manager reports "your system is up-to-date". Is it normal? 

I am suspecting that security updates has stopped after I installed some games through synaptic package manager.

How to be sure that I am not missing any security updates through alternative methods?

---

### Post by SunnyRabbiera on 2009-05-29
Dont worry, if your system is patched then it will stay patched.
Ubuntu is quite secure compared to windows XP.

---

### Post by 73ckn797 on 2009-05-29
Check under System/Software Sources/Updates to see whether security updates are checked to "install security updates without confirmation".

---

### Post by drs305 on 2009-05-29
> **t_k_majumdar said:**
> I am not getting any security updates for 23 days now.  Synaptic package manager reports "your system is up-to-date". Is it normal? 

I am suspecting that security updates has stopped after I installed some games through synaptic package manager.

How to be sure that I am not missing any security updates through alternative methods?

Have you checked the Updates tab of either Software Sources or Synaptic to make sure you have the security updates enabled? You can also manually check your enabled security repositories in sources.list by running this command:
```
cat /etc/apt/sources.list | grep "security" | grep -v "#"
```

You might also try manually run "Check" after opening Update Manager (System, Administration, Update Manager) even after it does it's automatic run. Also note at the top as to when it says it did it's last package info update.

Have you tried another server (Synaptic/Software Sources: Settings, Repositories, Other).

---

### Post by t_k_majumdar on 2009-05-31
Thanks to all three persons who replied to my post. 

Well, the problem was solved now. Probably the suggestion of 73ckn797 to check "install security updates without confirmation" worked. However, I was really benefited and learned much from the advice of drs305. My system is now updated with package information less than one hour old.

It is reassuring that Ubuntu is more stable than Window as SunnyRabbiera wrote. I installed avast anti-virus. Is is really necessary to run an anti-virus program in ubuntu? I found that avast does not run well as it cannot examine most of the system files due to lack of permission.

---

### Post by nandemonai on 2009-05-31
> **t_k_majumdar said:**
> Thanks to all three persons who replied to my post. 

Well, the problem was solved now. Probably the suggestion of 73ckn797 to check "install security updates without confirmation" worked. However, I was really benefited and learned much from the advice of drs305. My system is now updated with package information less than one hour old.

It is reassuring that Ubuntu is more stable than Window as SunnyRabbiera wrote. I installed avast anti-virus. Is is really necessary to run an anti-virus program in ubuntu? I found that avast does not run well as it cannot examine most of the system files due to lack of permission.

Only real reason to run anti virus in Linux is to protect Windows clients on a mail server or some such.

---

### Post by t_k_majumdar on 2009-05-31
Hi nandemonai - Thanks for your comment.

I use avast anti-virus to scan files transported from other sources to my computer through removable medias like USB sticks.

---

