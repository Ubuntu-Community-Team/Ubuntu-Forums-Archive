---
title: "is java safe?"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by REMIX8604 on 2011-04-13
i keep hearing people telling me to disable java and thats how viruses get in. is this true? is java a possible threat?

---

### Post by rosencrantz on 2011-04-13
I suppose you mean disabling javascript in a browser. The Java programming language is something different.
Viruses are usually targeted at Windows machines and have no more permissions than the user executing the program (i.e. a web browser). So, they can't do much harm on a Linux machine, if you aren't logged in as root.
Firefox has a Noscript add-on that allows you to disable Javascript selectively for sites you don't trust, but it isn't really necessary.

Cheers,
rosencrantz

---

### Post by josephmills on 2011-04-13
> **REMIX8604 said:**
> i keep hearing people telling me to disable java and thats how viruses get in. is this true? is java a possible threat?

java is one way that viruses "can" get in, but I think that viruses come from user error, It is not common for ubuntu box don't get viruses very easy as most viruses are written for windoz.  if you are super paranoid look at noscript and other monitoring program. If you need java for something then you need java it is not a bad  language, but a powerful one at that anything that is powerful can be dangerous. but I think you are fine.

---

### Post by idoitprone on 2011-04-13
> **REMIX8604 said:**
> i keep hearing people telling me to disable java and thats how viruses get in. is this true? is java a possible threat?

Only if you run java as root, it becomes unsafe. Try to learn about linux permissions. It is a proven security concept that is linux main defense for security. It so useful that Windows had no choice but to copy it with UAC.

[http://www.gnulinux.in/forum/why-linux-doesnt-contain-virus](http://www.gnulinux.in/forum/why-linux-doesnt-contain-virus)

[http://linuxmafia.com/~rick/skoll/anti-virus.p](http://linuxmafia.com/~rick/skoll/anti-virus.p)

[http://ubuntuforums.org/showthread.php?t=1725329](http://ubuntuforums.org/showthread.php?t=1725329)

---

### Post by REMIX8604 on 2011-04-13
i was trying to download some youtube vids but those web based downloaders need java. thanks guys

---

### Post by Spice Weasel on 2011-04-13
Even if the java virus is does not have root access, it can still delete or corrupt your personal files. Make sure you do backups of your documents and any other personal stuff saved on your machine.

---

### Post by idoitprone on 2011-04-13
> **REMIX8604 said:**
> i was trying to download some youtube vids but those web based downloaders need java. thanks guys

enable the partner repos, and download the sun java. You might have problems, since iced tea plugin do not have the all the libraries required as oracle/sun(dont know what it is named now dawn it oracle curse you) java

---

### Post by REMIX8604 on 2011-04-13
> **idoitprone said:**
> Only if you run java as root, it becomes unsafe. Try to learn about linux permissions. It is a proven security concept that is linux main defense for security. It so useful that Windows had no choice but to copy it with UAC.

[http://www.gnulinux.in/forum/why-linux-doesnt-contain-virus](http://www.gnulinux.in/forum/why-linux-doesnt-contain-virus)

[http://linuxmafia.com/~rick/skoll/anti-virus.p]("http://linuxmafia.com/%7Erick/skoll/anti-virus.p")

[http://ubuntuforums.org/showthread.php?t=1725329](http://ubuntuforums.org/showthread.php?t=1725329)

after reading this first link, it feels like the virus protection guys are the ones making viruses just to sell more virus protection. make a virus. scare the crap out of windows users. charge them an arm and a leg to "fix".

---

