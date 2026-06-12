---
title: "using the korn shell"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by BradleyAtkins on 2009-02-08
Hi All

I have just built an Ubuntu laptop so that I can work at home if I need to. I am working on Unix systems at work using the korn shell and would like to set up my Ubuntu laptop to default to korn as well for compatibility.

So for I have hopefully installed korn with: -

sudo apt-get install ksh

I have changed the entry in /etc/passwd to /bin/ksh although this seems to just be a link to: -

lrwxrwxrwx 1 root root 21 2009-02-08 11:51 /bin/ksh -> etc/alternatives/ksh

Is this all I would need to do to get korn by default when I log in?

Thanks

Brad

---

### Post by blueridgedog on 2009-02-08
Those are the only two steps I know...did it work as expected?

---

### Post by BradleyAtkins on 2009-02-08
Yes thanks

I am so used to logging into servers via a terminal session it didn't occour to me for a while that I need to log out of the laptop and back in again rather than just closing the terminal and restarting it... Doh!!!! 

](*,)

Cheers

---

