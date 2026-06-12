---
title: "RDP from Ubuntu to a Windows Server running Terminal Services"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by Canderson13 on 2007-11-29
I'm about to install Ubuntu for the first time, but I have one quick question first. 

I use my Windows XP box and Remote Desktop Client to connect to a server at my work that runs Terminal Services.  I hope to do the same from Ubuntu.  I know that Ubuntu comes with a client capable of handling the Remote Desktop Protocol, but I'm wondering if this client automatically establishes an encrypted connection (assuming the server supports such connections) or if it requires user intervention.  Am I going to accidently send confidential data in the clear because I missed a check box somewhere?  The Ubuntu client does support encryption, right?  

Thank you very much.

---

### Post by wjp.reg on 2007-11-29
AFAIK ubuntu terminal client supports encryption; I use it to connect to my agencies server

---

### Post by Canderson13 on 2007-12-02
Thanks, wjp.reg, for the advice.  I've gone ahead and installed Ubuntu and I love it.
  :)

I have one more related question:  I successfully connected to my office's server using rdesktop, but it was very laggy at first.  The screen took forever to redraw.  I've been trying to optimize the connection, and I wonder if anyone has any advice.  This is what I'm doing now:

```
/usr/bin/rdesktop xxx.xxx.xxx.xxx -z -P
```

-z compresses the data stream and -P forces bitmap caching.  Is there anything else I should do if I want it to go faster?  None of what I'm currently doing decreases the security of the connection, does it?  Please forgive the noobish questions.

---

### Post by wjp.reg on 2007-12-03
what kind of connection have you got?

I actually use the terminal client in the internet section of the applications menu and it has  a gui for setting the options.  You might want to try it or persevere with rdesktop.

---

### Post by Canderson13 on 2007-12-06
I've got a decent broadband connection.  The graphical frontened just wasn't working for me.  It didn't have nearly as many options as the command line.  Anyway, I've fiddled around a little more and have it all going at a good speed.  As long as the connection's still encrypted, which I assume it is, I'm in good shape.

Anyway, thanks for all your pointers.  I'm really happy with Ubuntu.

---

