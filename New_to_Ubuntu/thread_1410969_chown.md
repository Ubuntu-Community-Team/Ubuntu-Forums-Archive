---
title: "chown"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by Artanis.ro on 2010-02-19
I want to change permissions for a folder I own in which I have mounted a smb share.
The thing is that I have done this before and now doesn;t seem to work anymore.
So, when I type as root "chown myuser:myuser /home/myuser/Desktop/mounts" it gives me the followin error:

```
chown: changing ownership of `/home/myuser/Desktop/mounts': Permission denied
```

Also I have noticed in folder permissions that the owner of that folder is 3882. Who is 3882? :o

10x

---

### Post by blur xc on 2010-02-19
> **Artanis.ro said:**
> I want to change permissions for a folder I own in which I have mounted a smb share.
The thing is that I have done this before and now doesn;t seem to work anymore.
So, when I type as root "chown myuser:myuser /home/myuser/Desktop/mounts" it gives me the followin error:

```
chown: changing ownership of `/home/myuser/Desktop/mounts': Permission denied
```Also I have noticed in folder permissions that the owner of that folder is 3882. Who is 3882? :o

10x

I don't know anything about smb shares, but if you are trying to change ownership of a file that you currently do not own, you need to use sudo in front of it.

BM

---

### Post by Artanis.ro on 2010-02-19
> **blur xc said:**
> I don't know anything about smb shares, but if you are trying to change ownership of a file that you currently do not own, you need to use sudo in front of it.

BM

no need for sudo if I am using the root user. The thing is like this. I have created that folder as root. After this I have mounted the share in that folder. The folder is mine. The mounted files are a different thing. 
Anyway, I can find a way to make another folder using my user than mount the share as root. My main question is though who is this 3882 that has permissions over my files?

---

### Post by MinimalBin on 2010-02-19
> **Artanis.ro said:**
> My main question is though who is this 3882 that has permissions over my files?

No one. Change the permissions / ownership and forget about it.

---

