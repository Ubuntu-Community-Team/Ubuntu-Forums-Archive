---
title: "Can't login"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by gigenieks on 2011-08-09
Hi.


My problem is that I can't login anymore in Xubuntu 11.04 after I rebooted it.

I did reboot because I had only 50MB free RAM (of 768MB).
Also, earlier today (when I turned PC) I had some wierd windows problems (yesterday I turned off PC everything was fine). Had only 1 workspace (desktop), didn't have minimaze, maximaze or close buttons, programs didn't show up in top panel when I opened them - that kinda stuff.

Fixed that with **Alt+F2 "xfwm4 --replace"**


So, how should I fix this "login" problem. When I enter my password > Enter - **nothing happens** (meaning I have to enter again password) (=neverending cycle)

Also I noticed that in bottom screen is no "Xubuntu session" or whatever there was. Just in right bottom edge button where I can choose 3 options:
[LIST]
[*]Suspend
[*]Restart
[*]Turn off (or Shutdown; dont remember)
[/LIST]

[[COLOR="Navy"]**SEE YouTube video!!**[/COLOR]]("http://www.youtube.com/watch?v=4XX0lCWNfHY")

---

### Post by mmsmc on 2011-08-09
when you boot up are you able to get into the grub menu? and just to get a reference, how experienced are you with linux?

---

### Post by Jose Catre-Vandis on 2011-08-09
Check hard drive isn't full, or nearly full

---

### Post by gigenieks on 2011-08-09
GRUB doesn't show (because I have only Xubuntu on that PC) No need to show GRUB2.

I was using Ubuntu few weeks about 1 or 2 years ago. 
Now I am using Kubuntu (on father's PC) and Xubuntu (on mine old PC). Started 1.5week or so ago.

I have some knowledge (or put it in another way: most of time I know where to search if something goes wrong)
I am eager to learn.
But I am not that experienced (or have knowledge) to help others much. Was this kind of answer useful?

> 
Check hard drive isn't full, or nearly full

Ahh.. Before I restarted I had to know free space, so I typed in terminal
```

df -h

```
It showed that I have used 105GB (of 110GB) and also showed something wierd disk is 100% full or something like that... (don't remember)

Anyway, also when I tried to just create new folder in home directory I got error "there is no free space on device".
But I am quite sure there is like 5GB or so free..

---

### Post by Jose Catre-Vandis on 2011-08-10
Make some space in your / or /home (copy some stuff off or delete it if not needed) and I betcha you'll be able to log in again.

---

### Post by westie457 on 2011-08-10
Something else to try.

Boot into a LiveCD and run Gparted or Disk Utility. Highlight your full drive/partition and then click on Check Filesystem.

Had a similar situation a few weeks ago. Nautilus said 'disk is full'. Gparted showed it as about 40% full. The Filesystem check sorted things for me.

---

### Post by gigenieks on 2011-08-14
> **Jose Catre-Vandis said:**
> Make some space in your / or /home (copy some stuff off or delete it if not needed) and I betcha you'll be able to log in again.
Yes, this fixed everything. Can login as usual. Somehow there was no free space in /home.

---

