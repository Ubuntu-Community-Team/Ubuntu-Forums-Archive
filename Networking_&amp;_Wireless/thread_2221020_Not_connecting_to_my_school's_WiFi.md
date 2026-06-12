---
title: "Not connecting to my school's WiFi"
date: 2014-04-30
forum: Networking &amp; Wireless
---

### Post by Devon_Ruhl on 2014-04-30
I purchased this laptop for school, but the software it runs, doesn't seem to want to connect with my school's WiFi. It keeps asking me to log into the WiFi, which I do the with the information I always use when connecting a device to the WiFi. It keeps popping up "Authentication required by wireless network" So I try and try again, but it doesn't work. What could possibly be the problem?

---

### Post by Warren Hill on 2014-04-30
At school open a terminal and run the following commands

```
sudo lshw -C network; sudo iwlist scan
```

copy the results to a file then when you have access to the internet again post the results here.

---

### Post by Devon_Ruhl on 2014-04-30
> **Warren Hill said:**
> At school open a terminal and run the following commands

```
sudo lshw -C network; sudo iwlist scan
```

copy the results to a file then when you have access to the internet again post the results here.

[sudo] password for dell: 

Is what I get, and then I have searched through the forums a bit on this, because when I put my computer log in password in, it does nothing like I wasn't even typing.

---

### Post by Warren Hill on 2014-04-30
Enter your password.  It should then provide a few lines of text which should help us diagnose what the problem is.

---

### Post by SeijiSensei on 2014-04-30
Many schools and universities use proprietary wifi systems that often do not work well with Linux.  You need to talk with the people in charge of IT at your institution and see if they can help.

---

### Post by Devon_Ruhl on 2014-04-30
> **Warren Hill said:**
> Enter your password.  It should then provide a few lines of text which should help us diagnose what the problem is.

I try, but nothing appears, then after typing it, and clicking enter it says its not the right password. Most forum posts on it say its the same password you access your account with, but it doesn't work for me. 

> **SeijiSensei said:**
> Many schools and universities use proprietary wifi systems that often do not work well with Linux. You need to talk with the people in charge of IT at your institution and see if they can help.

Alright, I will do that, hopefully they can help me, otherwise I'm going to have to take off ubuntu, and thats a lot of time consuming work.

---

### Post by 98cwitr on 2014-05-01
There shouldnt be anything to 'click' on in terminal. It's a command line interface. I suspect the wireless driver that's being used doesn't support the encryption level

---

### Post by Devon_Ruhl on 2014-05-01
[ATTACH=CONFIG]252720[/ATTACH][ATTACH=CONFIG]252721[/ATTACH][ATTACH=CONFIG]252722[/ATTACH][ATTACH=CONFIG]252723[/ATTACH]> **Warren Hill said:**
> At school open a terminal and run the following commands

```
sudo lshw -C network; sudo iwlist scan
```

copy the results to a file then when you have access to the internet again post the results here.

Here is what I got after fixing the problem

---

