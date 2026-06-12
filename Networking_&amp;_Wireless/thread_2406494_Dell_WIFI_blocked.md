---
title: "Dell WIFI blocked"
date: 2018-11-21
forum: Networking &amp; Wireless
---

### Post by andreasbanell on 2018-11-21
Hello, 

I have a problem on my laptop dell, E7240. 

I am on ubuntu since 2 years and i never had WIFI issues but since somes weeks it is no longer working. (actually since I plug ethernet cable). 
```
dell-rtbn: Wireless LAN
           Soft blocked: yes
           Hard blocked: yes
phy0: Wireless LAN 
        Soft blocked: yes
        Hard blocked: no
```

I tried rfkill unblock all but it doest work. 

I have no idea how to fix it, could you help me please on this ? 

thanks

---

### Post by ajgreeny on 2018-11-21
Hard blocked usually means there is a hardware switch somewhere which is set "Off".

I have never used a Dell laptop, but often there is an F# key which may control this with another Fn key to enable that function.

---

### Post by andreasbanell on 2018-11-21
I already tried Fn + f2 ... still doesnt work.

---

### Post by kc1di on 2018-11-21
go to the terminal and issue this command ```
rfkill unblock all
```
Then the hardblock has to be undone with FN keys on my Dell it's f2
If that does not work then I would suspect you have a bad wifi card.

---

