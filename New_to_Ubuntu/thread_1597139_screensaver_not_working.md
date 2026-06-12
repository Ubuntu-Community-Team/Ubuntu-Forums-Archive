---
title: "screensaver not working"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by owners4life5 on 2010-10-15
hello,

can anyone help me with this?
it seems like something really simple, but i can.t figure it out,


my screensaver will activate for nothing..i don.t exactly know how to explain it..it just won.t start. period.

what is wrong?

any help is appreciated
-thanks

---

### Post by ubudog on 2010-10-15
Open a terminal and post the result of:

```
ps ax | grep gnome-screen
```

---

### Post by owners4life5 on 2010-10-15
```
brian@brian-laptop:~$ ps ax | grep gnome-screen
 1593 ?        Ss     0:03 gnome-screensaver
10254 pts/2    S+     0:00 grep --color=auto gnome-screen
brian@brian-laptop:~$ 
```

---

### Post by ubudog on 2010-10-15
Try this:

```
killall gnome-screensaver && gnome-screensaver &
```

Might work.

---

### Post by shubes on 2010-10-15
I was having the same problem. I didn't have "Activate screensaver when computer is idle" checked. When I checked it, screensaver began working.

I would like my screen (an external monitor on a notebook dock, using nVidia driver), to quit sending a signal so that the monitor goes into sleep mode. I haven't been able to make this happen yet.

---

### Post by ubudog on 2010-10-15
Did you look in System>Prefs>Power Management yet?  That fixed it for me (but that was like 2 years ago).

---

### Post by shubes on 2010-10-16
Yes, that's the first place I looked. I have "Put display to sleep when inactive for:" set to 10 minutes. "Set display brightness to:" is 50%. (Not sure what this does - apparently nothing in my setup). "Dim display when idle" is checked.

Hardy used to drop the signal to the external monitor after a period of time. I don't recall any special settings to get it to do that, but it was 2 years ago so that I set that up so I doubt that I'd remember.

Lucid does not ever drop the signal to the external monitor. I'm trying to make this happen, with no success. :(

---

### Post by owners4life5 on 2010-11-14
i eventually figured out how to do this myself...marking as solved.

---

### Post by Elwood72 on 2010-11-14
> **ubudog said:**
> Open a terminal and post the result of:

```
ps ax | grep gnome-screen
```

I'm having the same issue.I did a dirty upgrade to 10.10,and now I don't have a screensaver.

Here's my results:
> elwood@elwood-desktop:~$ ps ax | grep gnome-screen
 3727 pts/0    S+     0:00 grep --color=auto gnome-screen
elwood@elwood-desktop:~$ 

> **owners4life5 said:**
> i eventually figured out how to do this myself...marking as solved.

How?

---

### Post by owners4life5 on 2010-11-14
> **Elwood72 said:**
> How?

honestly, i don.t even remember...being that i marked this as solved, though, you might just want to start a new thread because the majority of people probably won.t view this anymore.

---

### Post by ikiini on 2010-12-18
it would be nice to out the resolved solution here.

-B

---

### Post by owners4life5 on 2010-12-18
> **ikiini said:**
> it would be nice to out the resolved solution here.

-B

sorry that i can.t

---

### Post by zmike1 on 2011-02-15
It might also be nice if someone could delete threads like these that purport to solve a problem but really give no useful information.

... and get off my lawn

---

