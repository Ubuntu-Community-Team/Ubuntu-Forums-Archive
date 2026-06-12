---
title: "Samba NAS won´t mount anymore"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by fanoodlehey on 2008-01-05
I have a D-Link DNS-323 which I use for network attached storage. It runs samba for network access. I have it set up to mount automatically at /home/myuser/DNS-323. Here is the line from my fstab (modified to omit personal info).

```
//dns-323/Volume_1 /home/myuser/DNS-323 smbfs username=myuser,password=mypassword,uid=myuser 0 0
```

I don´t use credentials because my network consists only of my PC and this NAS

This has been up and working for almost a year now. But recently the share won´t mount at all. I can see a Remote Share icon as an unmounted samba share on my desktop but the thing will not mount. If I do sudo mount -a I get 

```
10174: Connection to dns-323 failed
SMB connection failed

```

I remember there being some update to smbfs recently, could this be the reason? No configuration has changed on the server side or for that matter on the client side. 

Whatup?

---

### Post by jetsam on 2008-01-05
It is possible the update is causing this.  

Name resolution can be a troublesome and sticky area when things go wrong.  

Probably the surest fix for your problem is to reserve a static ip on your router for the NAS device  and then change your mount command to```
//*NASipaddress*/Volume_1 /home/myuser/DNS-323 smbfs username=myuser,password=mypassword,uid=myuser 0 0
```

You can also add the static IP and name to your hosts file to get name resolution to work properly again.

---

### Post by fanoodlehey on 2008-01-05
Thanks for the response. It does seem to have been a name resolution issue although it is odd since it looks like a DNS-323 bug. The box provides a different name than it used to provide. I don know how this could have happened. In any case my issue is solved now.

---

