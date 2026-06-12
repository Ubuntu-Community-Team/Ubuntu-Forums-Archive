---
title: "Updating VirtualBox to 3.0.2 on Jaunty 64"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by The Bright Side on 2009-07-30
Hey guys!

I just saw that there's a big new version of VirtualBox. I am running 2.2.4 on my system and want to update, but before I do, I'd like to ask for your advice:

Is it okay to just get the .deb from the VirtualBox web page and use it to install 3.0.2 over my old version? Did you do that? I am reluctant to just try it, because I don't want to screw up my installed version along with its Virtual Machines.

Thanks!
M.

---

### Post by mgranet on 2009-07-31
That's what I did. Works fine.

EDIT: You will have to re-install all your guest additions.

---

### Post by spcwingo on 2009-07-31
You could also add the virtualbox repos and update using Synaptic.  BTW, the apt line for virtualbox is:

```
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free
```

---

### Post by akrchstn on 2009-07-31
I didn't even know there was a new one coming out, I'll have to try arch on it since it doesn't work on the current version I have.

---

