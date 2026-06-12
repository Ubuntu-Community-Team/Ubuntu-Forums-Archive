---
title: "what's the problem?!"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by jazzersaxman on 2010-03-27
hi everyone,

ok...I installed ubuntu, setup Samba...I was able to detect the ubuntu system on my vista home premium system, but when I try to access my ubuntu system, it asks for username/password.  I enter it and it denies me access.  I have tried clicking on folder sharing in ubuntu, but windows still denies me access...what's the problem?  I ready stuff about registry config changes and other stuff relating to Vista Ultimate for fixes, but I have Home Prem...am I basically outta luck?

---

### Post by sandyd on 2010-03-27
> **jazzersaxman said:**
> hi everyone,

ok...I installed ubuntu, setup Samba...I was able to detect the ubuntu system on my vista home premium system, but when I try to access my ubuntu system, it asks for username/password.  I enter it and it denies me access.  I have tried clicking on folder sharing in ubuntu, but windows still denies me access...what's the problem?  I ready stuff about registry config changes and other stuff relating to Vista Ultimate for fixes, but I have Home Prem...am I basically outta luck?
```

sudo apt-get install system-config-samba samba
```
```

gksudo system-config-samba
```
Prefrences -> Server setting
Make sure
1. workgroup is set
2. Change authentication mode to "share"
3. change guest account to your username.
4. Click "ok"

click the "+" sign to add a share or click on a share and click on the "pencil" icon to edit a share.

in the access tab, select "allow access to everyone"

---

### Post by jazzersaxman on 2010-03-28
> **carlee said:**
> 
```

gksudo system-config-samba
```
Prefrences -> Server setting
Make sure
1. workgroup is set
2. Change authentication mode to "share"
3. change guest account to your username.
4. Click "ok"

click the "+" sign to add a share or click on a share and click on the "pencil" icon to edit a share.

in the access tab, select "allow access to everyone"


When I enter the "gksudo system-config-samba" code I get "NameError: global name 'Error' is not defined" what in the world did I do wrong?

---

