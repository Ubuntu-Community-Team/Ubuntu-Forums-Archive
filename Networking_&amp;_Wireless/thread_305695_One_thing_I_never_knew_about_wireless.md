---
title: "One thing I never knew about wireless"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by TomFumb on 2006-11-23
I recently discovered something about linux that I never knew before regarding wireless, and I thought I should share it with everyone. I know that there's bound to be at least one other person that needs to know this. 

(I also know that admitting this makes me look dumb, but hey, you don't know who I am so what do I care?)

If you're trying to connect to a wireless network, and you already have a wired connection to that network, the wireless won't work. I spent hours and hours thinking I had a setup problem with my wireless on my laptop, and all the time I couldn't connect because I had an ethernet connection to the router, to allow me to alter the access controls. This is something that a thousand years of googling might never have told me, yet was so simple as to be humiliating. 

I'm sure it is possible to have 2 network connections with enough fiddling, but to the average n00b with a wireless card this isn't much consolation.

Maybe people could reply to this with other stupid things about wireless that people like me would never be able to find out?

---

### Post by FrodoB on 2006-11-23
This is not a problem with any setup I have ever seen, in fact I have been able to get multiple wired and wireless connections working on differing networks at the same time.

I will admit that it can cause confusion, and you should get them all working one at at time, but they are not necessarily incompatible with each other if configured correctly.

In your particular case I am sure that this was a problem, but it is just not a built in characteristic of Linux or UNIX.

Usually I test by using ifdown to bring down the known good network connections in order to test the one that I am adding.

---

