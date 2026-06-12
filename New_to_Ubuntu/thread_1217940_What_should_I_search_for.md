---
title: "What should I search for?"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by allenbradley on 2009-07-20
I was recently given the task of managing my department's small bunch of computers. We had a system where students used to login at the splash screen with their user name and password, and they would have something like a Network File system, where each student would be allotted something like 1 GB. This system crashed a few years back and the guy who was in charge had left a while ago. I have no clue as to how to go about setting such a system up again. Could someone please point me to the correct tutorials/documentation? Googling Network File systems does not yield the correct result I need.

---

### Post by arochester on 2009-07-20
> This system crashed a few years back 

So what have you got? An existing Ubuntu network for Users, but not students?

Maybe you should give each student their own account (Home) but limit its size to 1Gb (?)

In that case try searching for "linux how to limit size of home" or "ubuntu how to limit size of home"

---

### Post by allenbradley on 2009-07-20
Sorry for the ambiguity. We had a linux server machine and the setup was like this. Each computer would have a login screen, where we used to have a user name and password ( something like ae03bXXX ). Now, upon entering the password, we would be logged into our account, with a graphical desktop and so on. The home folder would be mounted on on the server machine, and we would be working on that. Now, the server machine crashed and we managed without one for a few years. Finally, the funding went through and we purchased a spanking new Xeon server. I was conscripted to set up a system similar to the older one. The older guy who set it up had left quite a few years back, so we are now back to square one. So the situation is as follows : There is no existing ubuntu network. We have a computer with a 2 TB storage which we wish to make our central computer. All the computers in out department, connected by LAN, should be able to login with their usernames and passwords. Upon doing so, they would be logged into their home partition _on_ the server, in which they can store their files and so on. How do I go about :
(a) Setting up the linux server?
(b) Setting up username/password access?

---

### Post by allenbradley on 2009-07-20
I'll probably lose karma points for this, but bump.

---

### Post by allenbradley on 2009-07-20
Sorry again, but bump for the last time.

---

### Post by fraser_m on 2009-07-20
You might want to try XDMCP. While it doesn't look very well documented, it seems easy enough to set up.

---

### Post by Locke_99GS on 2009-07-20
On the nodes, symlink everything except /boot to a network mount, or try netbooting from the server.



Failing that, could try something NX based.

---

