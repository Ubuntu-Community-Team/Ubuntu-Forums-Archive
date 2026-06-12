---
title: "messed up tty ??"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by zaafar on 2011-04-20
i saw  a  thread on how to change my login screen by pressing ctrl+alt+f1 and typing some commands, but for some reason they didnt work and i had no idea how to get out of that (tty terminal ) thing . i panicked , tried everything then had to shutdown by force , but since then my system is running very slow , especially during boot. 


and i noticed that when i shut down or restart this comes up on the screen 

tty1 process killed by term signal
tty2 process killed by term signal
tty3 process killed by term signal
tty4process killed by term signal
tty5 process killed by term signal
cron process killed by term signal


are these processes running in the background ?


regards
zaafar

---

### Post by Frogs Hair on 2011-04-20
Ctrl + Alt F7 will return you to the desktop from TTY , but I don't know what was done while you attempting to change the login screen.

---

### Post by hakermania on 2011-04-20
As I think I've seen when glanced at the text on screen for one sec or so, on every shutdown the ttys processes are killed. But I'm not 100% sure

---

### Post by Frogs Hair on 2011-04-20
You could try going back into TTY and back to the desktop using key command I wrote in the other post. It looks like it is waiting for you to close the terminal session .

---

### Post by zaafar on 2011-04-21
ok  i will try going back to tty and shutting them down

---

### Post by yanom on 2011-05-08
> **hakermania said:**
> As I think I've seen when glanced at the text on screen for one sec or so, on every shutdown the ttys processes are killed. But I'm not 100% sure

tty is what manages the TeleTYpe terminals 1-6, which the average Ubuntuer never knows exist. They get shutdown when the computer is.

---

### Post by echo6 on 2011-05-08
You can also switch tty by using sudo chvt 7

---

