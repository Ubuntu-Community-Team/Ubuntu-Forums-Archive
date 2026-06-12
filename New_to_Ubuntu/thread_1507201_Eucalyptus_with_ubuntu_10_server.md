---
title: "Eucalyptus with ubuntu 10 server"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by macquivrf on 2010-06-11
So I burned the ubuntu 10.04 server image to cd and installed it
when it gave me a what seem to me a very limited selection of package groups to install I checked 'virtualization' (maybe there was a scroll bar missed)
When the system came up I expected Eucalyptus to be there ready for me to configure.
Is there a step during the install I need to take to get it to get Eucalyptus to be 'pre-installed'? 

I tried to go get it but apt-get says
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: couldn't find package <blah> 
where is any package I try and get.

Are there post install steps I need to take to get apt to work?

- JT

---

### Post by skatinjj on 2010-06-11
You can running this command:

```
sudo apt-get update
```

---

### Post by macquivrf on 2010-06-11
Ok, great that was it, apt-get seems to be working for me now.

---

