---
title: "Fresh Install Internet Access"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Wiedzmin on 2009-05-03
Ladies and gentlemen,

Sorry to bother everyone, as I am sure you have heard this all before, but I have a small problem.

I have just installed a fresh copy of Ubuntu for the first time, and am trying  to access the internet.

I am using a router and from what I can tell, I have indicated the correct addresses in my network settings. My router and other computers in the network respond to ping. However, Firefox will simply not work.

Any ideas?

Thank you, in advance.

---

### Post by lorderico on 2009-05-03
Are there other computers hooked up to your router?  If so, do they get Internet?  If they do, it is either a setting on your computer or your connection to the router.  I would reccomend using DHCP instead of setting an IP address yourself.  If your computer is able to get an address, there should be no problem.  To check your IP address, type ifconfig and look for inet addr: under eth0 or eth1

Eric

---

### Post by Wiedzmin on 2009-05-03
Yes, there is another computer in the network and it gets internet. Unfortunately I get nothing using DHCP, it does not even see the network.

New development: outside servers respond to ping, such, as in, if I ping yahoo.com or something like that. This makes me think there is a port problem, but I am not sure.

---

### Post by nandemonai on 2009-05-03
> **Wiedzmin said:**
> Yes, there is another computer in the network and it gets internet. Unfortunately I get nothing using DHCP, it does not even see the network.

New development: outside servers respond to ping, such, as in, if I ping yahoo.com or something like that. This makes me think there is a port problem, but I am not sure.

Make sure 'Work Offline' is not checked in Firefox (File -> Work Offline).

---

### Post by Wiedzmin on 2009-05-04
It's not checked. This looks stranger and stranger...

---

