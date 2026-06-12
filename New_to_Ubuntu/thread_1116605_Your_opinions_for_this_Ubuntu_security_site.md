---
title: "Your opinions for this Ubuntu security site"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by eddski on 2009-04-05
what do you think of this site, is this person full of *** or not. 

[http://www.itsecurity.com/features/ubuntu-secure-install-resource/#](http://www.itsecurity.com/features/ubuntu-secure-install-resource/#)

I wasn't sure about the su,sudo part, doesn't Ubuntu take care of that?

---

### Post by KIAaze on 2009-04-05
This person is right: Ubuntu is not secured to the maximum on a default install.
And his tips seem quite good to me.

However, I believe the default Ubuntu install is still reasonably secure.

I think disabling ssh root login is extremely important if you install openssh-server.

Here are some more security related links:
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)
[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
[http://www.hermann-uwe.de/blog/towards-a-moderately-paranoid-debian-laptop-setup--part-1-base-system](http://www.hermann-uwe.de/blog/towards-a-moderately-paranoid-debian-laptop-setup--part-1-base-system)
[http://paranoidlinux.org/](http://paranoidlinux.org/)
[http://www.securityfocus.com/infocus/1414](http://www.securityfocus.com/infocus/1414)
[http://www.linuxjournal.com/article/4547](http://www.linuxjournal.com/article/4547)
[http://selinuxproject.org/page/Main_Page](http://selinuxproject.org/page/Main_Page)


cf this thread too:
[http://ubuntuforums.org/showthread.php?t=1049131](http://ubuntuforums.org/showthread.php?t=1049131)

---

### Post by lisati on 2009-04-05
Now why would I want to meddle with su's settings?

---

### Post by CLomax on 2009-04-05
I'm sure I remember reading something bad about applying chmod 0700 to ~/...

---

### Post by KIAaze on 2009-04-05
I think you should read the comments on the site too.
It lead me to this official Ubuntu documentation:
[https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults](https://help.ubuntu.com/community/StricterDefaults?action=show&redirect=UnsafeDefaults)
;)

Mmh, applying "chmod -R 700 ~"(recursively) might be bad, but just "chmod 700 ~", I'm not sure. At least the second solution is easier to undo. ^^

---

### Post by MrWES on 2009-04-05
> **eddski said:**
> what do you think of this site, is this person full of *** or not. 

[http://www.itsecurity.com/features/ubuntu-secure-install-resource/#](http://www.itsecurity.com/features/ubuntu-secure-install-resource/#)

I wasn't sure about the su,sudo part, doesn't Ubuntu take care of that?


Definitely set PermitRootLogin no in your /etc/ssh/sshd_config 


```
# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

```

Also security depends on whether or not your are forwarding any ports from your router to a PC behind the router; especially for ssh logins. If so, you need to consider additional security measures e.g., DenyHosts or maybe a rate limit on logins utilizing iptables (built-in firewall in Ubuntu).

I'd also recommend you run your box by Shields Up! for a scan:

[https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")


Bill

---

