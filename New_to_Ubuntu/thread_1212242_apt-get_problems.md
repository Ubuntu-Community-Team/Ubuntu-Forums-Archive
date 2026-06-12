---
title: "apt-get problems"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by schylger on 2009-07-13
I am a newby, so be gentle...:-)
 
I just installed ubuntu on a desktop and everything seems to be up and running, I can browse using names rather than 111.222.333.444, so I am assuming DNS is running somewhere.
 
When I try to use apt-get, I get "couldn't find package xys" on everything I try, so I looked at the forums and found that I should run apt-get update first. When I did this, I got all "couldn't resolve xyz.abc.ubuntu.com". However, using the browser and typing in the respective xyz.abc.ubuntu.com it resolves just fine and I get file systems.
 
I am sure that I have not enabled something that should be enabled, or something like that and I need some help figuring this out. Can anyone guide me through this, so I can start installing tools that I need, like minicom, etc using apt-get?
 
Thanks
T

---

### Post by AndThenWhat on 2009-07-13
Have you tried using Synaptic? Maybe it will give you some kind of clue as to what is going wrong.

---

### Post by philinux on 2009-07-13
> **schylger said:**
> I am a newby, so be gentle...:-)
 
I just installed ubuntu on a desktop and everything seems to be up and running, I can browse using names rather than 111.222.333.444, so I am assuming DNS is running somewhere.
 
When I try to use apt-get, I get "couldn't find package xys" on everything I try, so I looked at the forums and found that I should run apt-get update first. When I did this, I got all "couldn't resolve xyz.abc.ubuntu.com". However, using the browser and typing in the respective xyz.abc.ubuntu.com it resolves just fine and I get file systems.
 
I am sure that I have not enabled something that should be enabled, or something like that and I need some help figuring this out. Can anyone guide me through this, so I can start installing tools that I need, like minicom, etc using apt-get?
 
Thanks
T

Are you behind a proxy?

If so go to system>prefs>Network Proxy and enter your proxy info and apply system wide.

---

### Post by rockerphil on 2009-07-13
> **philinux said:**
> Are you behind a proxy?

i second that. i remember that i once misconfigured anon-porxy and was getting basically the same problem you're having. nothing would install period.

---

