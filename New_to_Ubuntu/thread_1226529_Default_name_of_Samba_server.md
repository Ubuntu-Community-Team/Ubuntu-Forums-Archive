---
title: "Default name of Samba server?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by skaldicpoet9 on 2009-07-29
I am going crazy trying to figure out the name of my SMB server. I just installed Samba to share files over my network but I cannot find what the name of my Samaba server is. I have googled for about the last hour and turned up nothing. the only thing I could find said that the server name is in the /etc/samba/smb.conf file but it is not. I swear this should be much simpler then it is....why is this so frustratingly difficult to find the server name? Can anyon help me out here?

---

### Post by fooman on 2009-07-29
not exactly sure what your looking for,  but wouldn't that be the domain/workgroup name?  in the smb.conf file,  look under global for this line:

```
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
```

i believe WORKGROUP is the default name of the samba server.  you can edit that line to match whatever name you have given your domain.  for instance, if my domain were named FOOMAN,  i would edit the line like this:

```
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = FOOMAN
```

hope that helps.

---

### Post by skaldicpoet9 on 2009-07-29
Ha, that is what I was thinking was the server name but it said "Workgroup" so I wasn't sure. Thanks for the info. Now to try and get my PS2 to stream from my laptop :(

(it hasn't been working so far)

---

