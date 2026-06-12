---
title: "update manager problems"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by redspotss on 2011-05-29
when i check for software updates i get a failed connection window ? and and something about launchpad ? how do i fix this

---

### Post by jtarin on 2011-05-29
Copy, paste and post the contents of the dialog box. It's usually a matter of editing a file or finding another server.

---

### Post by redspotss on 2011-05-29
W:Failed to fetch [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


this is the message that i get

---

### Post by webofunni on 2011-05-29
remove them from /etc/apt/sources.list or correct the path

---

### Post by redspotss on 2011-05-29
ok so where do find them at to remove them?

---

### Post by wildmanne39 on 2011-05-29
> **redspotss said:**
> W:Failed to fetch [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


this is the message that i get
Hi, go into synaptic click settings click repositories,click other software uncheck it or remove.

---

### Post by webofunni on 2011-05-29
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by jtarin on 2011-05-29
What application ppa are these related to?

---

### Post by redspotss on 2011-05-29
cool thank you wildmann .

---

### Post by NormanFLinux on 2011-05-29
If the PPAs are backports, they won't exist on Natty. Correct them to the last version they ran on... i.e, Lucid or Maverick. Then they should load correctly into Synaptic.

---

### Post by wildmanne39 on 2011-05-29
> **redspotss said:**
> cool thank you wildmann .
Hi, your very welcome.:)

---

