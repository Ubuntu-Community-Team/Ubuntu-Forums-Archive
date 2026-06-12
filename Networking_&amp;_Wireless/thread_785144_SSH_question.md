---
title: "SSH question"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by Lyana on 2008-05-07
Hi,

I am new here, so please excuse me if this is not the right place to ask this question.
At work i have a limted internet access and only port 80 is open(as far as i can see).
I was wondering if it is possible to set up an SSH tunnel on port 80.
I have a server at home which is ready and working, but the only problem is that my requests on port 80 cannot be forewarded by the router to one particular PC.

Atleast that is what i think is the problem.

Is there any way around this?

Greetz

---

### Post by tamoneya on 2008-05-07
you should look into port forwarding on your router since most routers are able to do this.  Also to change from port 22 to port 80 you just need to change sshd_config and the restart the ssh server```
gksu gedit /etc/ssh/sshd_config
sudo /etc/init.d/ssh restart
```

---

