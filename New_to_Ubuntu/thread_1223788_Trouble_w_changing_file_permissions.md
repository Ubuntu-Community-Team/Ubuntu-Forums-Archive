---
title: "Trouble w/ changing file permissions"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by andrew222 on 2009-07-26
I downloaded some source code examples of JSF code and installed it according to how the documentation stated.

When trying to run it on Tomcat6, I get a 404 error message.

I suspect it has something to do with the file permissions.

I ran this script 



*$ /usr/share/tomcat6/webapps$ chmod a+x jsfbook*



and got this error message:



*chmod: changing permissions of `jsfbook': Operation not permitted*


Is there anyway I can change the permissions on this file without getting blocked??

---

### Post by TeoBigusGeekus on 2009-07-26
```
sudo chmod a+x jsfbook
```

---

### Post by Michael.Godawski on 2009-07-26
Perhaps

```
sudo chmod a+x jsfbook
```

or is this too simple? :-k

---

### Post by andrew222 on 2009-07-26
Thank you!

---

### Post by stockley on 2009-07-26
The sudo command is used to run as an administrator, su (super user) and do, do as the super user :P
For some reason the default user isn't the root or the administrator, which seems strange to me but they have their reasons for setting up like that I suppose :confused:

Just thought I'd let you know :P
If you ever have problems with permissions just tack on sudo on the front of it. :3

---

