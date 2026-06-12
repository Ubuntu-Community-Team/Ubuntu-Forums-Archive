---
title: "Total Linux Ubuntu/noob sudo qustion"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by ejim_shan on 2011-08-21
Hi everyone, my first post to this forum:

I hope this is the right place for this post. My apologies if it's not. I have checked other posts on this topic. although I could h ave overlooked something.

Here's what I'm trying to do: I'm trying to edit the limits.config line for real time audio. But in order to do this I need ROOT privileges. I need something called Sudo. I did a bit of reading. I've got the code I need for the bottom of the limits config page. But I need Sudo to enter that code. Can any of you folks help me out on how to proceed with this? The path (for lack of a better term) is Sudo (username) gedit/etc/security/limits.config. Once I have RT audio I can then utilize Jack d. I'm I making any sense? [FONT=Tahoma][SIZE=2]

[/SIZE][/FONT]Thanks, Jim[FONT=Tahoma][SIZE=2]
 [/SIZE][/FONT]

---

### Post by papibe on 2011-08-21
The simplest way is to use the terminal. Open a 'Terminal' application and run this:
```
$ sudo gedit /etc/security/limits.config
```
Your password will be asked as security practice.

Another alternative is this:
```
$ gksudo gedit /etc/security/limits.config
```
Which asks the password in a graphical environment.

Hope it helps,
Regards.

---

