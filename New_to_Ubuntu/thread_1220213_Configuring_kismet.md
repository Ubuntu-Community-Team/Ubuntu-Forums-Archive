---
title: "Configuring kismet"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by cactuska on 2009-07-22
Hi everyone 
 
i have a special problem, that i cannot solve, son please help me. 
 
i followed the tutorial when i tryed to configure kismet, but it output tis error 
 
cactus@cactus-desktop:~/Desktop$ sudo kismet 
Server options:  none 
Client options:  none 
Starting server... 
Waiting for server to start before starting UI... 
Suid priv-dropping disabled.  This may not be secure. 
No specific sources given to be enabled, all will be enabled. 
Enabling channel hopping. 
Enabling channel splitting. 
FATAL: Unknown capture source type 'rt73' in source 'rt73,wlan0,addme' 
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server} 
 
i use ubuntu 9.04, and asus wl-167g usb wifi adapter 
 
please help 
 
regards 
cactuska

---

### Post by chili555 on 2009-07-22
Please post the relevant section of /etc/kismet/kismet.conf. Also, I don't know if it will run or not with 'addme.' You might just try changing to:```
rt73,wlan0,Realtek
```

---

