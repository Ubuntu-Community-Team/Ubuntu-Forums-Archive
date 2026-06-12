---
title: "sudo apt-get install openssh --ERROR"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by richyrage on 2011-08-31
Hello,
Quick question.

I was advised to use openssh and taffy to access and do things to my server.
I cant seem to get this installed:

sudo apt-get install openssh

give me the error:

*E:Couldn't find openssh*   

I read some posts and found something to the effect that the pkgname is not in a file 
somewhere on the server, so how would I go about updating this..

Also, is there a section/tutorials somewhere that explains setting up users/groups./and all that good stuff?

thanks,

RR

---

### Post by saltmarshlamb on 2011-08-31
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

The client should be installed by default. 

```
apt-cache policy openssh-client
```

should tell you.

---

### Post by seawolf167 on 2011-08-31
Do this instead

```
sudo apt-get install openssh-server
```

---

### Post by gnometorule on 2011-08-31
If you're not sure about how the package is actually called, run this first in the future:

sudo apt-cache search openssh

You get a page full of related packages, and usually you will know which one you need.

---

### Post by seawolf167 on 2011-08-31
> **gnometorule said:**
> If you're not sure about how the package is actually called, run this first in the future:

sudo apt-cache search openssh

You get a page full of related packages, and usually you will know which one you need.

Or what I do

```
sudo apt-get install openssh[TAB][TAB]
```

I'm lazy lol

---

### Post by aura7 on 2011-08-31
Thanks [gnometorule]("http://ubuntuforums.org/member.php?u=997827") i really appreciate your help, I did not knew about this search thing.

and @richyrage - try using synaptic it will show the suggestion along with some description too.

---

### Post by richyrage on 2011-09-02
Thanks everyone for the great tips...
alot of the starter info and basic questions r hard to find documented....

but alas i guess that is part of the process.

thanks again,
you help is much appreciated

RR

---

### Post by seawolf167 on 2011-09-03
Take a look at [this link]("https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo"), or just google/search this forums for "how to ssh", this is a pretty common subject that will have tons of results and documentation.

```
man ssh
```

---

