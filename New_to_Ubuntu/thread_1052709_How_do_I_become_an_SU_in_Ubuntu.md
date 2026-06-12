---
title: "How do I become an SU in Ubuntu?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by BrendanMark on 2009-01-28
I've been having a few permission issues (and for convenience, I must add) with Ubuntu and binary extractions, as well as being unable to run .RPMs, so I was wondering how one becomes a genuine superuser in Ubuntu, rather than using the "sudo" command.

Thanks in advance.

---

### Post by jimmy the saint on 2009-01-28
You use sudo before the command you want to issue.
```
sudo <command>
```
Ubuntu is based on Debian which uses .deb files, not RPM.  The issues you seem to be having with the RPM file is not a permissions issue, but a compatibilty one.

If you wish to learn more about sudo vs SU and why it is against the forum rules to give instructions on gaining true SU status, read the link in my sig.

---

### Post by TCSnyder on 2009-01-28
first log in at the terminal and type

```
sudo su -
```

once logged in type

```
passwd
```

enter a new root password and from there on out you can log in via 

```
su -
```


WARNING ---- Do not log in graphically as root. Do NOt Use Autologin as root

---

### Post by BrendanMark on 2009-01-28
Thank you! I thought it'd be easy once you knew. :D

---

### Post by jimmy the saint on 2009-01-28
TCSnyder: Please refer to the forum policy on login as root tutorials and edit the instructions out of your post.  They are not supported and expressly verboden.

---

### Post by BrendanMark on 2009-01-28
If that's the policy I will not be frequenting this forum very often! I wish to thank the person for providing the answer I actually wanted.

---

### Post by igknighted on 2009-01-28
> **BrendanMark said:**
> If that's the policy I will not be frequenting this forum very often! I wish to thank the person for providing the answer I actually wanted.

The data you sought is freely available on other sites, but it circumvents the security model used in Ubuntu.  These forums are more than simply a conversation between you and those who help you, but rather anything posted is part of a huge how-to guide.  The last thing we want is someone who doesn't understand what he/she is doing to unlock and use the root account as a crutch, it just isn't safe computing.

I believe unlocking the root account is OK to post, but enabling a graphical root login is not OK (for the reasons posted above).  I'm sorry if this bothers you, and there aren't many things taboo, but there are certain standards we must adhere to for the safety of all.

---

### Post by TCSnyder on 2009-01-29
i know graphically logging in as root is a bad idea, but why is "su -"
i used fedora for a long time and i didnt make a sudoers file, so "su -" was all i used.

any of the same changes can be made with sudo vs su -

---

### Post by TCSnyder on 2009-01-29
the policy says 
 "Policy
Tutorials explaining how to enable the root account for a graphical login or autologin will not be supported on the forums and will be moved to the Jail"

which i did not give instructions for root graphical login or root autologin, so i am going to change my post back unless someone gives me a reason

---

### Post by jerome1232 on 2009-01-29
Surprised no one has linked this yet
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The reason being is there are very few reasons one would need to use the root acount, if you need it you are advanced enough to do it yourself or  at least google the method.

Don't take this link wrong it's meant as a joke :)
[http://tinyurl.com/b7m3n2](http://tinyurl.com/b7m3n2)

btw "sudo -i" will get you a root shell that's no different then using "su -" other than you don't need to unlock the root acount to do it.

---

### Post by sisco311 on 2009-01-29
a little trick:
```
alias su='sudo su'
``` :)

---

### Post by niteshifter on 2009-01-29
> **jerome1232 said:**
> 
Don't take this link wrong it's meant as a joke :)
[http://tinyurl.com/b7m3n2](http://tinyurl.com/b7m3n2)


... and just as I was about to slurp some coffee ....

You owe me (ok, the folks I work for) a keyboard :lolflag:

---

### Post by ibutho on 2009-01-29
> **BrendanMark said:**
> If that's the policy I will not be frequenting this forum very often! I wish to thank the person for providing the answer I actually wanted.

I personally don't agree with the policy, but I don't think this should be reason for you to stop frequenting the forum. Just ask these type of questions elsewhere and you will get an answer without anyone lecturing you about sudo vs root.

---

