---
title: "What are the disadvantages of a real-time kernel?"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by Blutkoete on 2010-04-23
Hello!

I've been using Ubuntu 9.10 for some time now and I changed to Ubuntu Studios because I wanted to test it (out of curiosity).

It wasn't a plain install, I just loaded the packages from a previous standard installation (apt-get lot-of-packagres-with-ubuntu-studios), as found in these forums.

As I'm not experiencing any problems or things that work slower than they did before (even when I use MATLAB), I just wanted to ask:

What are the disadvantages when using a real-time kernel?

I'm studying control engineering, so I know what a RT Kernel is, and yes, I won't really need it for the sound or video editing I do (and I won't program feedforward controls at home, but still ... if I don't have a disadvantage ...

Please just tell me :).

Thank you very much!

---

### Post by madnessjack on 2010-04-23
[https://rt.wiki.kernel.org/index.php/Frequently_Asked_Questions](https://rt.wiki.kernel.org/index.php/Frequently_Asked_Questions)

> What is real-time?  Real-time applications have operational deadlines between some  triggering event and the application's response to that event. To meet  these operational deadlines, programmers use real-time operating systems  (RTOS) on which the maximum response time can be calculated or measured  reliably for the given application and environment. 
A typical RTOS uses priorities. The highest priority task wanting  the CPU always gets the CPU within a fixed amount of time after the  event waking the task has taken place. On such an RTOS the latency of a  task only depends on the tasks running at equal or higher priorities,  all other tasks can be ignored. On a normal OS (such as normal Linux)  the latencies depend on everything running on the system, which of  course makes it much harder to be convinced that the deadlines will be  met every time on a reasonably complicated system. This is because  preemption can be switched off for an unknown amount of time. The high  priority task wanting to run can thus be delayed for an unknown amount  of time by low priority tasks running with preemption switched off.


I think it means applications don't have to share Kernerl priorities, which in turn means that applications that don't relate to audio/video don't get priority.


I think :P

---

### Post by Objekt on 2010-04-23
Funny you should ask.  I recently switched to using the realtime kernel (2.6.31-9-rt) with a regular Ubuntu 9.10 install.

One possible disadvantage: Because it is "only" 2.6.31, it does not have TRIM support for SSDs, as do the newer 2.6.33-x series kernels.

That doesn't affect me, as I don't have an SSD or plans to purchase one.

Except for the TRIM thing, I have found no disadvantages at all.  Rather, using the realtime kernel removed some annoying video lag in one 3D game.  That made me very happy! :)

---

### Post by Blutkoete on 2010-04-23
Thank you, madnessjack, thank you, objekt.

The simple answer might be: You don't lose anything when using a RT kernel, but you might win a lot if you really need it.

I couldn't find something in the FAQ recommending against it.

EDIT: I don't care about SSDs, too.

---

