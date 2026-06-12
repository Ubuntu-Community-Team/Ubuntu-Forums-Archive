---
title: "Ettercap crashes when scanning for hosts"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by Hilko on 2009-05-17
Hello, when I launch the ettercap GUI from the menu or from the terminal with this command i get an error:

```
:~$ sudo ettercap -G

ettercap NG-0.7.3 copyright 2001-2004 ALoR & NaGA

Dissector "dns" not supported (etter.conf line 70)
Ooops ! This shouldn't happen...
Segmentation Fault...
```

But the GUI starts. Then i do 'Start Unified Sniffing' and after that I try to scan for hosts. The moment I select 'scan for hosts' from the menu. Ettercap just quits.

Can anyone help me with this ? Please ?

-----------
btw: I'm running Ubuntu 9.04 for 64bit

---

### Post by diablo75 on 2009-05-17
> **Hilko said:**
> ```

Dissector "dns" not supported (etter.conf line 70)

```


Due to the nature of this program, you probably won't get any help here.  I'd google the above error message you got to find results elsewhere.

---

### Post by Hilko on 2009-05-18
> **diablo75 said:**
> Due to the nature of this program, you probably won't get any help here.  I'd google the above error message you got to find results elsewhere.
I just want run it for educational purposes; to learn more about computer networks. Isn't there anyone who wants to help me ?

---

### Post by diablo75 on 2009-05-18
I would suggest you try using Backtrack instead of Ubuntu for these types of programs.  Ubuntu isn't exactly designed to function as a network security auditing OS.  Ettercap (and hundreds of other apps) are included with Backtrack by default and it boots pretty quickly from a CD.

[http://www.remote-exploit.org/backtrack.html](http://www.remote-exploit.org/backtrack.html)

---

### Post by Hilko on 2009-05-20
Thank you for your reply and the link to backtrack. I'll try that. But still it would be nice if I could get it to work in ubuntu 64bit too. I'll keep trying.

---

### Post by Hilko on 2009-07-11
Ok. The solution is here:

[https://launchpad.net/~timothy-redaelli/+archive/ppa](https://launchpad.net/~timothy-redaelli/+archive/ppa)

---

