---
title: "ssh  vs  openssh. Any difference?"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by egalvan on 2009-04-07
Edited to avoid the confusion about my confusion... :)
this is not a question about the closed, proprietary package,
and the open-source package

Is there a difference between ssh and openssh [I]when they are talked about 
in regards to Ubuntu?[/I]

How-to's will  say
"install ssh"
 or
"install openssh"

are they referring to the same package?
Is the different name just a convenience?

Synaptic has a meta-package called "ssh"
which, to me, appears to be an installer for openssh.

As far as I can tell, there is no difference.

If there is a difference, could you give a short explanation?
Is one better than the other?
Is one recommended over the other?

Thanks
ErnestG

---

### Post by jo4hnc on 2009-04-07
Try this.

[http://www.google.com/search?q=ssh+vs+openssh&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=ssh+vs+openssh&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Gen2ly on 2009-04-07
Hmm, I'm not sure that ssh is being developed anymore.  Openssh was developed because of problems with ssh and because of closed standards.  Openssh now uses a protocol 2 which provides even better security-measures.

---

### Post by Stupendoussteve on 2009-04-07
There is a difference... [SSH]("http://www.ssh.com/") is a closed-source, commercial product. OpenSSH was originally based on the last open-source release of the commercial SSH, and is developed by the developers of OpenBSD. The commercial SSH is still under development, and also supports SSH 2. The company was founded by the inventor of the ssh protocol, Tatu Ylönen. The ssh protocol itself is [open]("http://tools.ietf.org/html/rfc4252").

If you are using the "ssh" command on any Linux distribution, unless you have specifically purchased the commercial SSH product, you are using OpenSSH.

EDIT for your EDIT: In regards to the Ubuntu package, there is no difference, it is only for convenience:
> [ssh]("http://packages.ubuntu.com/jaunty/ssh") - This metapackage is a convenient way to install both the OpenSSH client and the OpenSSH server. It provides nothing in and of itself, so you may remove it if nothing depends on it. 

---

### Post by ataraxia937 on 2009-04-07
"OpenSSH" is the name of a project (part of the OpenBSD group of software). "ssh" is one of the programs that they ship, and the name of the protocol it supports. Ubuntu and Debian divide the upstream package (just called "openssh") into two packages, "openssh-client" and "openssh-server".

---

### Post by egalvan on 2009-04-08
> **ataraxia937 said:**
> "OpenSSH" is the name of a project (part of the OpenBSD group of software). "ssh" is one of the programs that they ship, and the name of the protocol it supports. **Ubuntu and Debian divide the upstream package (just called "openssh") into two packages, "openssh-client" and "openssh-server"**.

Thank you...

This give more info to help me research...

ErnestG

---

