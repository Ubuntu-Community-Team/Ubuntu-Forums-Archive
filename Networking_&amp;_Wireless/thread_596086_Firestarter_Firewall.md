---
title: "Firestarter Firewall"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by VincentValentine on 2007-10-29
I am using Firestarter Firewall and I have one small issue...

When Firestarter comes up at boot time, it ALWAYS asks for the root password. It doesn't really decrease the functionality as everything works quite fine after entering the password, but I was wondering, is there a way you can set it up to load with root privileges without having to type in the password again as it is extremely annoying to have to type in my password twice every time I boot up...

Thank you much!

---

### Post by kebes on 2007-10-29
Why is Firestarter starting at boot time in the first place?

Firestarter is a GUI to access/edit the Linux firewall (iptables)... but you don't actually need it to be running for the firewall to be active. You only need to run Firestarter when you want to edit your firewall. In general I wouldn't leave it running, since that means anyone who sits down at your computer can easily edit the firewall without entering the admin password!


So, one answer would be to not have Firestarter start up at boot, and only open it when you need it. (If you like Firestarter's ability to show you net connections and network traffic, there are other programs that can also do that, such as "conky", and they don't have to run as root.)


If you really need it to run as on startup, it may be possible to do. How are you auto-starting it right now?

---

### Post by kebes on 2007-10-29
These links seem to describe the process of getting Firestarter to start from a normal user login (so no password needed):
[http://mandrivausers.org/index.php?showtopic=35278](http://mandrivausers.org/index.php?showtopic=35278)
[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

Hope that helps.

---

### Post by shane2peru on 2007-10-29
> **kebes said:**
> Why is Firestarter starting at boot time in the first place?

Firestarter is a GUI to access/edit the Linux firewall (iptables)... but you don't actually need it to be running for the firewall to be active. You only need to run Firestarter when you want to edit your firewall. In general I wouldn't leave it running, since that means anyone who sits down at your computer can easily edit the firewall without entering the admin password!


So, one answer would be to not have Firestarter start up at boot, and only open it when you need it. (If you like Firestarter's ability to show you net connections and network traffic, there are other programs that can also do that, such as "conky", and they don't have to run as root.)


If you really need it to run as on startup, it may be possible to do. How are you auto-starting it right now?

I have the same question and appreciate the info.  I'm sure there are some people that may be concerned about others setting down at there PC and changing settings, however for me that is not an issue.  I like it running to I can monitor the attempts to get in or out and so that I can setup rules too.  That are my thoughts.  Thanks for the links I will look them over.  

Shane

---

### Post by julian67 on 2007-10-29
[ How-To: Firestarter on startup (better & safer way)]("http://ubuntuforums.org/showthread.php?t=542756")> This how-to will let you start Firestarter automatically without having to enter a password for it, but also not editing /etc/sudoers and, thus, giving access to anyone to change it.


---

