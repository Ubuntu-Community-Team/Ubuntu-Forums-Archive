---
title: "synaptic does not ask for password"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by fwin on 2010-04-20
Hi everyone,

I am running ubuntu 9.10 and here is my question

-why does synaptic only ask me for my password once? The first time i open it, it asks for my password and then after i close it and open it again it does not. It looks like it remembers my password for a while. The same thing happens when i use the command "sudo". Is this ok?, does this happen to everybody?, wouldn't it be safer if it would ask for the password all the time?


Thanks

---

### Post by cgroza on 2010-04-20
This is normal. Once you enter the password synaptic will remember it for some time ( 5 min or 15 , i forgot) , but after this period of time expires it will ask you once more when you start it.

Good luck.

cgroza

---

### Post by immerohnegott on 2010-04-20
Yeah, that's normal. I'm not sure how to change it, but sudo/gksu store the password for like 5 minutes IIRC.

They probably assume that since you were able to put the password in, you are authorized to continue using root-level apps, and it's just convenient if you say, forget to install a package when working in synaptic, not to have to re-input the password when going back in.

---

### Post by aysiu on 2010-04-20
By default, the timeout is 15 minutes.

You can change it to be 5 minutes or even 0 minutes if you'd like:
[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

---

### Post by fwin on 2010-04-20
thanks everyone, i will mark this thread as solved.

---

