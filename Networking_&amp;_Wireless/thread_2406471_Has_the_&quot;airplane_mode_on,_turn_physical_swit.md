---
title: "Has the &quot;airplane mode on, turn physical switch&quot; issue been solved ?"
date: 2018-11-21
forum: Networking &amp; Wireless
---

### Post by euqed on 2018-11-21
Hi all,
 I'm running Ubuntu 18.04 LTS on a MSI GS65 Stealth 8RE and I'm having the same problem as some people here ([https://ubuntuforums.org/showthread.php?t=2403269&highlight=airplane+mode+hardware](https://ubuntuforums.org/showthread.php?t=2403269&highlight=airplane+mode+hardware) , [https://ubuntuforums.org/showthread.php?t=2391449&highlight=airplane+mode+hardware](https://ubuntuforums.org/showthread.php?t=2391449&highlight=airplane+mode+hardware)).
Namely, when the laptop gets out of sleep mode, airplane mode is on and must be deactivated via a physical switch.
Now, the FN+F10 combination that works on Windows doesn't in Ubuntu.
I have the usual rfkill output : 
```

[COLOR=#000000][FONT=&amp]ubuntu@ubuntu:~$ rfkill list all
[/FONT][/COLOR]0: phy0: Wireless LAN
    Soft blocked: no 
    Hard blocked: yes

```
EDIT: Forgot to mention that when I reboot, everything seems to be fine. So it's not too bad, but recurrent and annoying nonetheless.

---

