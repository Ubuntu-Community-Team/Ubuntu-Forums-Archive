---
title: "Xubuntu 11.04 - Huge Boot Time Increase"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by guv999 on 2011-07-26
Hi
Xubuntu 11.04 was booting consistently under 30 seconds for me until recently when it starting taking 75 seconds .   
To the best of my knowledge I have changed nothing in terms of start up programs etc.

I have a link to the latest Boot Chart output below.  Any help greatly appreciated.
[http://imageshack.us/photo/my-images/827/davedesktopnatty2011072.png/]("http://imageshack.us/photo/my-images/827/davedesktopnatty2011072.png/")

---

### Post by 3602 on 2011-07-26
I'm not very proficient at reading Boot Charts. 
Did you install any new packages?
Where there any updates "recently"?
Thanks.

---

### Post by Toz on 2011-07-26
Post back the results of:
```
dmesg
```

---

### Post by skatinjj on 2011-07-26
Also if it has anything in it post what is in /var/log/boot

---

### Post by guv999 on 2011-07-31
Thanks for the responses.  I figured this out by chance in the end.
In the start up settings I had selected to start Gnome Services at start up.
De-selecting this option has got me back to to 30 second boots.

---

