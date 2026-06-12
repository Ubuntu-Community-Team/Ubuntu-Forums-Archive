---
title: "Chnaging host name"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by ububaba on 2009-05-17
Couldn't find the right thread. My question is not exactly related to the 
points being discussed here. This is the best place I could think of.

Were I to change name of the (hosting) machine, would the files become 
inaccessible? How does one do that?

---

### Post by cariboo on 2009-05-18
To change your host name, open a n Applications-->Accessories-->Terminal and type:

```
hostname <new name>
```

where <new name> is the hostname you want to change to. You will have to reboot in order for the new hostname to take effect.

---

### Post by ububaba on 2009-05-18
> **cariboo907 said:**
> To change your host name, open a n Applications-->Accessories-->Terminal and type:

```
hostname <new name>
```

where <new name> is the hostname you want to change to. You will have to reboot in order for the new hostname to take effect.

Thanks. Solved.

---

### Post by jelsa on 2009-05-20
It's just for temporally. The permanent one is typing this line :
      sudo gedit /etc/hostname  
Edit your hostname then save & exit.

---

