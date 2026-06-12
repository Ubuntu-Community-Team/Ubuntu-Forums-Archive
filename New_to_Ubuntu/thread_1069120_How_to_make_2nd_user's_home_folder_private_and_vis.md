---
title: "How to make 2nd user's /home folder private and vise versa?"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by MerlinsLair on 2009-02-13
Hi,

I searched the forums but couldn't seem to find what I was looking for so I'm posting this in this forum to not only help me but others in my predicament. First off, I'm using Ubuntu with the Gnome desktop.

I created a 2nd /home account as a user only from my original one. I want them both to be private as in not able to read into one from another. How would I go about this? I'm needing to do this so if my grandkids want to 'play' on the computer I won't have to worry about what they do so much as I can always delete the account if need be. Thanks.

---

### Post by bodhi.zazen on 2009-02-13
```
sudo chmod -R 770 ~user1
sudo chmod -R 770 ~user2
```

---

### Post by MerlinsLair on 2009-02-13
Thanks bodhi.zazen. Is there any documentation I can go over concerning this so I can get more familiar with it?

---

### Post by lazyart on 2009-02-13
I thought by default home folders were private....

---

### Post by bodhi.zazen on 2009-02-13
> **MerlinsLair said:**
> Thanks bodhi.zazen. Is there any documentation I can go over concerning this so I can get more familiar with it?

What kind of information are you looking for ?

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

You can also look at apparmor.

> **lazyart said:**
> I thought by default home folders were private....

No they are not private by default although you can now install with encryption, either the entire system or $HOME.

---

### Post by MerlinsLair on 2009-02-13
> **lazyart said:**
> I thought by default home folders were private....

I did too but evidently not thus my needing to protect what I have in my /home directory from the hooligan grandkids. :)

Thanks again bodhi.zazen. I just wanted to get familiar with this in case I need to make any further changes.

---

### Post by Shpongle on 2009-12-23
thanks, just what i was looking for

---

