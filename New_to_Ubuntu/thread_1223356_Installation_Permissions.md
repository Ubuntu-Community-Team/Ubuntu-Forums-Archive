---
title: "Installation Permissions"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Tyrsius on 2009-07-26
I installed Ubuntu on my family's computer today after their most recent viral infection from windows sent me over the edge. I have personally been using Ubuntu on a second box for a few months now and love it. I am a gamer first, so windows will always reside on this box, but Ubuntu has grown on me.

Problem is I have never set it up for use with multiple users. I don't want to give my family the "administer the system" privilege, but I need them to be able to install games and other minor applications. I also want to be able to set up sudo on their accounts, but with my password as the sudo not theirs (that way I can use the terminal on their accounts as sudo, but they can't).

If anyone can help me understand this better, or point me to a guide, I am basically looking to learn how to let users (preferably as a group, so I don't have to set each account up individually) install applications on their own account, without giving them root or sudo access (are they different?)

---

### Post by QIII on 2009-07-26
When you add a new user, you can set their user privileges.

By default "Administer the system" is not selected.  You don't want it to be.

But that will keep them from using Synaptic and the CLI to install programs, I believe.

---

### Post by Tyrsius on 2009-07-26
So basically without making them admins, there is no way to let them install programs?

I was afraid that was the answer.

---

### Post by p0cky84 on 2009-07-26
Well, you can edit your /etc/sudoers file to let them have *some* permissions.

Add a new group.
```
sudo addgroup family
```

Add users to that group.
```
sudo adduser mom family
```

I'm just guessing wild now, but I guess It'd be something like this:
```
%family        ALL=(ALL) NOPASSWD: apt-get, synaptic, aptitude
```

But don't trust that line, its just a pseudo code, read some manuals on sudo and you'll get my point.

And just to point you in the right direction, **[here you go.]("http://www.google.com/search?hl=en&rlz=1G1GGLQ_ENNO338&q=editing%2Bsudoers%2Bfile&btnG=Search&aq=f&oq=&aqi=")**

---

