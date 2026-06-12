---
title: "Error with running app from other user"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by honeybear on 2011-07-12
Hello, 

I have a question regarding "su". I encouter this error message... : 
 
```
pantarox@ubuntumagic:~$ su -l potato xterm
Password: 
/usr/bin/xterm: /usr/bin/xterm: cannot execute binary file
```
 
Thanks if you woudl know


>  env  DISPLAY=':0.0' su -l potato  xterm
Password: 
/usr/bin/xterm: /usr/bin/xterm: cannot execute binary file

not working either: 
>  su -l potato -c "XAUTHORITY=$HOME/.Xauthority DISPLAY=:0.0 xterm"

---

### Post by Quitty on 2011-07-12
man su 
Note the placement of -l.

---

### Post by honeybear on 2011-07-12
> **Quitty said:**
> man su 
Note the placement of -l.

```
env  TERM='xterm' DISPLAY=':0.0' XAUTHORITY=/home/mainuser/.Xauthority    su - --login potato -c xterm
Password: 
No protocol specified
xterm Xt error: Can't open display: :0.0
```

not working :(  although man.

---

