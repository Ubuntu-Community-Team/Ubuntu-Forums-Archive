---
title: "GParted options disabled / enable GUI root login"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by mark01 on 2010-06-02
I have tried all sorts to get GParted to work. I have tried both sudo and SU and nothing allows me to do what I want. Some options like format and resize are disabled. what can I do?
Oh and I apologize if this has been answered but, how do I enable graphical root login, please don't give me "you don't know how so therefore you shouldn't" or "its a bad idea" just tell me how, please? I'm getting the boxed in feeling with everything behind a password or something stopping me, I just want to use my laptop as I wish to, not how somebody else tells me.. /rant
Thanks, Mark

---

### Post by sisco311 on 2010-06-02
> **mark01 said:**
> I have tried all sorts to get GParted to work. I have tried both sudo and SU and nothing allows me to do what I want. Some options like format and resize are disabled. what can I do?

You have to unmount the partition in order to be able to format or resize it. 

> **mark01 said:**
> 
Oh and I apologize if this has been answered but, how do I enable graphical root login, please don't give me "you don't know how so therefore you shouldn't" or "its a bad idea" just tell me how, please? I'm getting the boxed in feeling with everything behind a password or something stopping me, I just want to use my laptop as I wish to, not how somebody else tells me.. /rant
Thanks, Mark

It's against the forum policy: 
[thread=1486138]Forum policy on log-in-as-root tutorials[/thread] (new)
[thread=716201]Forum policy on log-in-as-root tutorials[/thread] (old)

---

### Post by mark01 on 2010-06-02
> **sisco311 said:**
> You have to unmount the partition in order to be able to format or resize it.
So how would I go about that?


> **sisco311 said:**
> 
It's against the forum policy: 
[thread=1486138]Forum policy on log-in-as-root tutorials[/thread] (new)
[thread=716201]Forum policy on log-in-as-root tutorials[/thread] (old)
Thanks for letting me know :)

---

### Post by sisco311 on 2010-06-02
> **mark01 said:**
> So how would I go about that?


Right click on the partition and select **Unmount**.

---

### Post by John Bean on 2010-06-02
You can't modify the active partition with gparted. Boot from a live CD and run it from there.

As for enabling a root account in Ubuntu, Google is your friend. My advice is "don't".

---

### Post by mark01 on 2010-06-02
> **sisco311 said:**
> Right click on the partition and select **Unmount**.

*facepalm* Thanks :)

---

