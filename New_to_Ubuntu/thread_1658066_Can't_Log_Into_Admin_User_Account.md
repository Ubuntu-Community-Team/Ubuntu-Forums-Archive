---
title: "Can't Log Into Admin User Account?"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by bitnitlit12 on 2011-01-02
Hello,

I use XUbuntu 10.04. 
I preface this with apologies, as I am a relative n00b to Linux. 

My problems are as follows:

Last night I shut off my computer like normal. I have two user accounts, one Admin and one just General User. I tried logging into my Admin account, where most of my files are, and a quick black screen pops up with approximately 5-10 lines of text. It disappears just as quickly as it pops up, and thus I cannot read what it says to give any information. 

I was able to create another Admin account by opening the General User account, etc. 

However, ALL of the files in the original Admin account are inaccessible. There are some things I would like to salvage here, but have no idea how to access them through my new Admin account. 

I am sorry if this is a general explanation of the problem. At this point a lot of the Linux terminology goes over my head, but if somebody could ask me the right questions to get to the bottom of this problem, I would appreciate it. 

Thank you kindly...

---

### Post by Verbeck on 2011-01-02
could you try to access it through the root nautilus
from a terminal, run:
```
gksu nautilus /home
```or change the ownership of the old home directory
```
sudo chown -R $USER:$USER /home/directoryname
```

---

### Post by bitnitlit12 on 2011-01-02
> **Verbeck said:**
> could you try to access it through the root nautilus
from a terminal, run:
```
sudo nautilus /home
```or change the ownership of the old home directory
```
sudo chown -R $USER:$USER /home/directoryname
```

Neither of them produce results. In fact, when I try to access it through the root nautilus, the folder is just simply locked.

---

### Post by philipballew on 2011-01-02
is it best to even really have an admin account. cant all be done with sudo and gksudo?

---

### Post by bitnitlit12 on 2011-01-02
> **philipballew said:**
> is it best to even really have an admin account. cant all be done with sudo and gksudo?


Well, that might be very good advice in retrospect. But, it doesn't really solve my current dilemma. I just need access to the files that are inaccessible at this point :)

---

### Post by philipballew on 2011-01-02
can you boot in to a xubuntu live cd and access them there?

---

### Post by bitnitlit12 on 2011-01-02
> **philipballew said:**
> can you boot in to a xubuntu live cd and access them there?


Doesn't work. Any other suggestions?

---

