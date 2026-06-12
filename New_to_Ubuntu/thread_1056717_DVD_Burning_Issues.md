---
title: "DVD Burning Issues"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by koopa225 on 2009-02-01
hey im still kinda new to ubuntu and I was wondering why when i insert a black dvd it wont let me burn it. Ive tried but the burn option is greyed out. I looked around and found that I needed to download and install a few programs and when I try to install it tells me that I need to download it from the software channel, and when i go to install updates it tells me that only one software management tool is allowed to run at a time. I dont know what 2 do if someone could help me I would greatly appreciate it.

---

### Post by HotShotDJ on 2009-02-01
> **koopa225 said:**
> I looked around and found that I needed to download and install a few programs and when I try to install it tells me that I need to download it from the software channel, and when i go to install updates it tells me that only one software management tool is allowed to run at a time. I dont know what 2 do if someone could help me I would greatly appreciate it.Close every application that you have open.  You probably inadvertently tried to run two software installation programs at the same time (such as apt-get while add/remove was open, or Update Manager while Synaptic Package Manager was open... something like that).  In fact... log out and then log back in just to make sure. :)  It won't hurt anything.

Once you've done that, open Applications --> Add/Remove... and search for and install k3b (check it off then click "Apply Changes").  I've found it to be among the best CD/DVD burning applications available -- including those Windows applications that people spend money for.  If you continue to have problems, post back.

---

### Post by koopa225 on 2009-02-01
This is what i get when i try to add the applicaiton


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by indytim on 2009-02-01
The message is telling you what to do to make things happy again.

In the terminal mode:
```

$ sudo dpkg --configure -a'

```

IndyTim

---

### Post by indytim on 2009-02-01
forget the " ' " at the end of the code snippet shown above.

---

