---
title: "Log in problem after upgrade to 10.04LTS"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by fcoroa on 2010-05-02
Hey guys! I hope you can help me with my problem. I was using Ubuntu 9.10 Karmic Koala successfully for quite a while. But suddenly the sound stopped working... So after various attempts of fixing it i decided to upgrade to 10.04. Although sound was back up, a new problem came up, i tried to edit the appearance settings and it gave me an error. I rebooted the computer and when i tried to log in it would just come back to the log in screen... Also, even though i upgraded from within ubuntu, i found a version of 9.10 still working on GRUB. Please help me!


Thanks guys...

---

### Post by madjr on 2010-05-02
you upgraded from update manager or live-cd?

9.10 is still working ? am confused

the easiest fix is just reinstall 10.04 from live-cd

backup

---

### Post by ajk95 on 2010-05-02
> **madjr said:**
> you upgraded from update manager or live-cd?

9.10 is still working ? am confused

the easiest fix is just reinstall 10.04 from live-cd

backup
Did you read the message? The OP said that he/she installed **from within Ubuntu**.

---

### Post by fcoroa on 2010-05-02
> **ajk95 said:**
> Did you read the message? The OP said that he/she installed **from within Ubuntu**.


yeah i used the update manager... Does anybody have any idea?

---

### Post by capistrano on 2010-05-04
This isn't a solution, fcoroa, but you're not alone. I've upgraded a 9.10 system in a VM to 10.04 and now I can't get past the login screen. I enter the correct user and password and it just returns to the login screen.

I've tried changing the session selection to xterm and Failsafe Gnome but the same thing happens.

Help please!

---

### Post by capistrano on 2010-05-04
I've just had a thought.

I have DB2 installed, for which I had to change the password hashing algorithm, to md5, because the default Ubuntu algorithm (sha512) creates hashes that are too long for DB2 (I was following instructions [here]("http://blog.herbert.groot.jebbink.nl/2009/06/wmb-61-ubuntu-904.html")).

So now I think the original setting in /etc/pam.d/common-password was restored by the 10.04 upgrade and this is causing the login to fail on account of the it's hashed with md5 and not sha512.

So, my question now is, how on earth can I modify /etc/pam.d/common-password if I can't even log in?

---

