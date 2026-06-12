---
title: "How do you kill command line processes the right way?"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by Xeoncross on 2010-06-06
Every time I run a never ending task from the commandline, such as top or ping, I always exit by pressing "ctrl+z". However, it seems that only moves the process to the background so that I can continue using the command line. 

What is the proper way to kill long lasting processes?

On a side note, now that I installed killall it doesn't seem to close the ping or top processes I started. Each time I start top I still see them.


```
killall ping
```

---

### Post by tacutu on 2010-06-06
you can quit most programs by pressing Q. If you want to "kill" it, ctrl+C should work.

---

### Post by rcayea on 2010-06-06
I believe, sudo kill "whatevernumbertheprocessis" will work. Don't use the quotes when you type in your number.

---

### Post by Xeoncross on 2010-06-06
Yes, I didn't even see that top SAYS TO PRESS "Q" TO QUIT. At any rate, I found I had many left over pings running (hope they don't ban me!) at least 5 top's and some left over nano processes!

While killall NAMEHERE didn't work this did:

```
killall -9 NAMEHERE
```

What's with the "-9" anyway?

---

### Post by Barrucadu on 2010-06-06
Ctrl-C, that sends SIGINT to the process.

---

### Post by Barrucadu on 2010-06-06
> **Xeoncross said:**
> What's with the "-9" anyway?

-9 is the numeric value for SIGKILL, which ends the process immediately, without giving it time to clean up.

---

### Post by bumanie on 2010-06-06
You can also use the PID number - find that by putting > top in terminal, once you know the PID of the process you want to kill > kill -9 <PID>

---

### Post by jwbrase on 2010-06-06
> **Xeoncross said:**
> Yes, I didn't even see that top SAYS TO PRESS "Q" TO QUIT. At any rate, I found I had many left over pings running (hope they don't ban me!) at least 5 top's and some left over nano processes!

Ctrl-Z does pause the process, so you weren't pingflooding anybody.

---

### Post by Barrucadu on 2010-06-06
> **Xeoncross said:**
> and some left over nano processes!

Ah, didn't notice this. nano actually tells you how to close it at the bottom of the terminal window - Ctrl+X

---

### Post by tgalati4 on 2010-06-06
sudo killall firefox

You need sudo to kill most processes.

I like htop for killing processes:

sudo apt-get install htop
htop

With htop, you can watch the process die a slow death (if you are into that sort of thing).  You can send terminate signals first then send kill signals to the process.  You can injure the process then give the final death blow.

---

### Post by Barrucadu on 2010-06-06
> **tgalati4 said:**
> sudo killall firefox

You need sudo to kill most processes.

Only processes not owned by your user.

---

### Post by Windows Nerd on 2010-06-06
> **tgalati4 said:**
> 
With htop, you can watch the process die a slow death (if you are into that sort of thing).  You can send terminate signals first then send kill signals to the process.  You can injure the process then give the final death blow.
Sorry to be off-topic, but that has to be the most entertaining use of htop I have ever seen. Hilarious.

---

