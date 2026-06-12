---
title: "How do I get rid of keyring thing?"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by Indy452 on 2010-05-21
I'm using Ubuntu 10.04 and when I start my computer I get a dialog box asking for my default keyring password.  I simply use my user password I created when I installed the system but I find it annoying and it gets in the way of my work.  How do I get rid of it and what the heck does it do??

The only reason I can think that this comes up is when I installed I chose to log me in automatically. Is that why its bothering me?

---

### Post by Boondoklife on 2010-05-21
> **Indy452 said:**
> I'm using Ubuntu 10.04 and when I start my computer I get a dialog box asking for my default keyring password.  I simply use my user password I created when I installed the system but I find it annoying and it gets in the way of my work.  How do I get rid of it and what the heck does it do??

The only reason I can think that this comes up is when I installed I chose to log me in automatically. Is that why its bothering me?

Ok here is the info on your situation. If you have it set to auto login then the system will always ask you for the password as it needs to decrypt your stored passwords in the keyring. You can however change your default keyring password to "BLANK" but this will allow anyone that has access to your system to have access to your passwords.

Really the only solution is to not use autologin, unless this is a local/home machine that your dont mind information being available on.

---

### Post by 2hot6ft2 on 2010-05-21
It's file system protection. Here is the info. you requested.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Indy452 on 2010-05-21
Alright then, how do I undo the auto login option?  

Its my home desktop computer and I am the _only_ person who sees and uses this machine ever...

To me the keyring has always been a pain because all I want to do is start the machine and have everything load without having to type my name and password....silly IMO.

---

### Post by 2hot6ft2 on 2010-05-21
System > Administration > Login Screen
to activate or deactivate auto login.

Running as root is dangerous and that's why you run as a user and have to give the sudo password to make system changes.
:popcorn:

---

### Post by Indy452 on 2010-05-21
> **2hot6ft2 said:**
> System > Administration > Login Screen
to activate or deactivate auto login.

Running as root is dangerous and that's why you run as a user and have to give the sudo password to make system changes.
:popcorn:

Thanks. 

I guess I find it disappointing.....I've been using Ubuntu on and off since 6.06 and I've always used auto login and never had this issue before...I guess I'll have to switch again.

---

