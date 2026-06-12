---
title: "lost desktop after appling compiz effects"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by sanket.kurolikar on 2011-06-27
I have upgraded ubuntu 10.10 to 11.04, after installation I applied some effects form compiz, while doing so i disabled few things, and after completing that I found, I lost my default 11.04 desktop.
I tried to open terminal, Alt+F2 but not working anything...
Now what should I do to get 11.04 desktop back...
Please help..

---

### Post by alphacrucis2 on 2011-06-27
> **sanket.kurolikar said:**
> I have upgraded ubuntu 10.10 to 11.04, after installation I applied some effects form compiz, while doing so i disabled few things, and after completing that I found, I lost my default 11.04 desktop.
I tried to open terminal, Alt+F2 but not working anything...
Now what should I do to get 11.04 desktop back...
Please help..

```
unity --reset
```

Log out and back in. There are some guides floating around about getting some of the other compiz plugins to work with unity (unity is a compiz plugin itself).

---

### Post by sanket.kurolikar on 2011-06-27
but the desktop is very clean..
nothing is on the desktop ...
i cant open the terminal too..
so how do i do that..?
Ubuntu is very strange for me but i want to stick with this ..
so please suggest stepwise what should i do..
please help ..

---

### Post by alphacrucis2 on 2011-06-27
> **sanket.kurolikar said:**
> but the desktop is very clean..
nothing is on the desktop ...
i cant open the terminal too..
so how do i do that..?
Ubuntu is very strange for me but i want to stick with this ..
so please suggest stepwise what should i do..
please help ..

Ctrl Alt F1 

Should display a console session. Login with your normal usercode and password and issue the unity --reset command. Then 

```
sudo reboot
```

---

### Post by sanket.kurolikar on 2011-06-27
Solved ...
Thanks a lot ...

---

