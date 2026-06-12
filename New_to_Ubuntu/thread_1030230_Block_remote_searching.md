---
title: "Block remote searching"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by mancroft on 2009-01-04
Using 8.10.

Is it possible to block remote searching of a computer by people who want to see what files you have?

---

### Post by northern lights on 2009-01-04
No need to block anything.

What you describe is not possible (Unless you, knowingly or unknowingly, have software installed that allows this).

---

### Post by scorp123 on 2009-01-04
> **mancroft said:**
> Is it possible to block remote searching of a computer by people who want to see what files you have? "out of the box" (e.g. after a fresh Ubuntu installation) there is **_nothing_** installed on your system that would allow others to connect to your Ubuntu system in any way.

What some people do is that they install e.g. openssh-server so they can remotely access their own machines. But to login you'd still need to know a valid username and a valid password.

The only reason I can see why you might be asking this is if you use certain types of P2P software maybe? If that is the case can you tell us more which software you are using?

---

### Post by mancroft on 2009-01-04
Hi, scorp123. The reason I'm asking is that I don't want people snooping on my computer which is why I switched to Ubuntu from Winders. I am not using any form of software to do with P2P.

---

### Post by northern lights on 2009-01-04
> **mancroft said:**
> I am not using any form of software to do with P2P.
Your system is absolutely safe then.

---

### Post by scorp123 on 2009-01-04
> **mancroft said:**
> The reason I'm asking is that I don't want people snooping on my computer Then the replies already given to you apply: "out of the box" it is not even possible to connect to your installation, let alone do any remote "snooping" on your files. Per default there are no services running that would offer such possibilities. Please be aware that this however changes as soon as you install things like FTP-, WWW-, SSH- or SAMBA-servers on your system. Just don't install anything like that unless you are sure you know what you do.

Here is a little command that might interest you:
```
 > sudo lsof -n -i -P
COMMAND     PID  USER   FD   TYPE  DEVICE SIZE NODE NAME
**[COLOR="Red"]sshd[/COLOR]**       5182  root    3u  [COLOR="Red"]**IPv6**[/COLOR]   16771       TCP [COLOR="Red"]***:22**[/COLOR] (LISTEN)
**[COLOR="Red"]sshd[/COLOR]**       5182  root    4u  **[COLOR="Red"]IPv4[/COLOR]**   16773       TCP **[COLOR="Red"]*:22[/COLOR]** (LISTEN)
cupsd      5392  root    2u  IPv4 2292090       TCP 127.0.0.1:631 (LISTEN)
dhclient  13094  root    5w  IPv4 2366413       UDP *:68 

``` ... what it does: "lsof" lists all open files, and the parameters specified above focus on opened TCP/IP network ports (from a UNIX perspective these are "files" too in a way). If the list the command produces is empty and does not list anything that would listen to outside world connections which are denoted by " **[COLOR="Red"]*:[/COLOR]** ", then everything is fine.

In my case above I have a running SSH server (sshd) - I highlighted it in red. The port information above show that this server is listening on TCP port 22 - written above as " ***:22** " ... So this might be potentially risky and not what you want (in my case it is what I want).

So if you are not sure you can check with "lsof -n -i -P" if there is anything on your system that would allow others to connect to you. But there shouldn't be anything.

The other things listed above is harmless ... you might have that too: "cupsd" is the printer driver, and it only listens to your own machine (it is per default unreachable for others), and "dhclient" is the DHCP service which will auto-configure your network card if there is a DHCP server in the network. It's a harmless standard service too.

> **mancroft said:**
>  which is why I switched to Ubuntu from Winders. The OS doesn't really matter here. Windows too could be secured if only people paid attention to what they do with their Windows installation. ;)  The only real big difference is that "out of the box" Windows is already running several network services that could be remotely exploited whereas Ubuntu does not have such services per default. But if you install things such as SSH or SAMBA without care your security on Ubuntu will get just as bad as it might be on Windows. You're biggest safety measure is therefore to know what you do and why.

> **mancroft said:**
>   I am not using any form of software to do with P2P. OK.

---

### Post by mancroft on 2009-01-04
Thanks guys. That has put my mind to rest.

---

