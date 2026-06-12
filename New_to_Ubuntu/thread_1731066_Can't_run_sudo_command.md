---
title: "Can't run sudo command"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by RoyceDalton on 2011-04-16
I ran the update manager and loaded new header files (I think.)  Anyway, now I can't run the Package Manager or any command that requires super user rights. I get an error message as follows:

royce@NetPC:~$ sudo nautilus
sudo: /etc/sudoers is mode 0640, should be 0440
sudo: no valid sudoers sources found, quitting

Can someone help?

Thanks!

---

### Post by wojox on 2011-04-16
You would need to reboot into recovery mode and run:

```
chmod 0440 /etc/sudoers
```

---

### Post by RoyceDalton on 2011-04-17
I'll try that as soon as I learn how to boot into recovery mode. I don't have a boot menu on this machine like on the dual-boot machine that also has Windows OS. As you can tell, I'm very new at Linux. I have an older Dell laptop, which I had decided to donate to charity, so I had completely wiped the hard drive. I decided instead to use it as a network computer, so loaded Ubuntu Netbook Remix. I've never had boot menu, or if I do it defaults so quickly I can't see it. Long story short - I need to get into recovery mode so I can do the chmod as suggested. Thanks for your help, and your patience! :)

---

### Post by wojox on 2011-04-17
Reboot and hold down the left shift key.

---

### Post by RoyceDalton on 2011-04-17
Wojox - thank you very much! I'm back in business.:D

---

### Post by jucny2 on 2011-05-11
Sorry,  Probably thread hijack, brand new to this, with a lot of reading coming on fairly good. Found this
thread to fix my problem also. Question what was cause of problem.

---

