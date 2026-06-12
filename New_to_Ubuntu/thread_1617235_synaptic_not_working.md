---
title: "synaptic not working"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by oaridus on 2010-11-09
Hi guys, I have a problem with my synaptic. when I start it by command line it says
segmentation fault 

and stops there. how can I fix this. The gui does not even open. please help

---

### Post by bioterror on 2010-11-09
> **oaridus said:**
> Hi guys, I have a problem with my synaptic. when I start it by command line it says
segmentation fault 

and stops there. how can I fix this. The gui does not even open. please help

Well, sounds weird.
Open terminal and insert this command:

```
sudo apt-get purge synaptic && sudo apt-get install synaptic
```

And tell if it helps.

---

### Post by miegiel on 2010-11-09
> **oaridus said:**
> Hi guys, I have a problem with my synaptic. when I start it by command line it says
segmentation fault 

and stops there. how can I fix this. The gui does not even open. please help

how exactly did you start it ?

```
synaptic
```
or
```
sudo synaptic
```
or
```
gksudo synaptic
```

---

