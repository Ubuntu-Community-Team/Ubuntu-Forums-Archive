---
title: "Remote Desktop"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by aliasghar1451 on 2010-03-19
hi i have 2 pc one with ubuntu 8.04 and the other with windows server 2003 now is it possible to access windows server in ubuntu using remote desktop or whatever it is called here if yes plz can someone guide me

---

### Post by lijcam on 2010-03-19
you could use rdesktop

To install 
```
sudo apt-get install rdestop
```

To run:
```
rdesktop ip.address.of.remote.host:port
```

---

### Post by Paddy Landau on 2010-03-19
The best that I've found for accessing Windows or Mac from any other machine (including from Ubuntu) is [LogMeIn]("http://logmein.com/"). There's a free version that works very well, and a smarter paid-for version.

---

### Post by BitJunkie on 2010-03-19
Take a look at tsclilent, which is a frontend for rdesktop.

---

