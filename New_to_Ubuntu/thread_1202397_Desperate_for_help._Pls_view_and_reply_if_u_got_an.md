---
title: "Desperate for help. Pls view and reply if u got any answers."
date: 2009-07-02
forum: New to Ubuntu
---

### Post by NfF on 2009-07-02
My problem may sound rather simple, but i just can't enable my wireless! Both wireless devices are on, both linksys and Intel, they are up and running, but i just can't enable them. How do i enable them? is it by running a command in terminal? or do i need to download something? Pls help. I'm stuck, real bad. 

Also pls view the screenshots, it might help u guys to give a suitable solution to my problem.

---

### Post by fooman on 2009-07-02
have you tried going to system > administration > hardware drivers (might be called restricted drivers in feisty)

if they are listed there...try enabling them.

---

### Post by NfF on 2009-07-02
There are no drivers. See my attached screenshot.

---

### Post by Fatal Toenail Infection on 2009-07-02
Does your notebook have a WLAN switch or a FN key combination to enable wireless?

---

### Post by Fatal Toenail Infection on 2009-07-02
Does your notebook have a WLAN switch or a FN key combination to enable wireless?  For example, on my laptop, FN>F2 will toggle between WLAN on or WLAN off.

---

### Post by matey3 on 2009-07-02
never mind the switches...

go to the terminal and type in ifconfig look at the list then do ifconfig -a compare the results and see if NICs added?

---

### Post by matey3 on 2009-07-02
btw, I could never use both the GUi and command network config at the same time, the clash,
if you made any changes in GUI or terminal you have to reboot (that is the only way I know how to str8 things out)!
then I suggest using terminal to config the network,

---

### Post by mkrahmeh on 2009-07-02
try 
```
sudo ifconfig wlan0 up
```
then see if scanning yields anything
```
iwlist wlan0 scanning
```
or
```
cat /proc/net/wireless
```

---

