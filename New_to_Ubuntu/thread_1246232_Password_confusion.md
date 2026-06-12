---
title: "Password confusion"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by beacon on 2009-08-21
I had this problem once before and don't know how it resolved itself, but it has arisen again after a new install. When I try to enter as root and put in my password, it is said to be invalid. However, when I go to synaptic and am asked for my password, it works. What is the explanation, and what I can do to regain control?

---

### Post by credobyte on 2009-08-21
By default, root account is disabled ( as an example, you can't use su ). Synaptic asks for your password, not root password. Basically, if you need to do something with root privileges, use sudo - it relies on sudoers file and will have the same functionality if you were logged in as root ( NOT recommended ).

---

### Post by Iowan on 2009-08-21
[Broken sudo]("http://www.psychocats.net/ubuntu/fixsudo")?

---

### Post by donkyhotay on 2009-08-21
As mentioned the root account is disabled, please explain what you're doing. If you are doing
```

su
somecommand

```
and it's not accepting your password that is intentional and you shouldn't do that. If you are doing
```

sudo somecommand

```
and it's not accepting your password then there is something wrong.

---

### Post by theozzlives on 2009-08-21
> **donkyhotay said:**
> As mentioned the root account is disabled, please explain what you're doing. If you are doing
```

su
somecommand

```
and it's not accepting your password that is intentional and you shouldn't do that. If you are doing
```

sudo somecommand

```
and it's not accepting your password then there is something wrong.

You have to have Administrator rights to use sudo.

---

### Post by lisati on 2009-08-21
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by beacon on 2009-08-22
I thank all of you for the replies which were very helpful. I was particularly pleased to have the link suggested by lisati. The problem is now that I can't really explain what happened. I had downloaded (from synaptic) a file (sbackup), but the files all showed a lock, which I assumed meant that I had to become administrator. I did in fact try the wrong thing, as you pointed out, by trying su. Then I tried sudo but didn't know what command to use to remove the locks. In any case I went to bed after fiddling about and this morning the problem is gone. So I'll take the suggestions to heart and write again if I should have the same problem and be unable to resolve it.   With many thanks.

---

