---
title: "JACK installation for Dummies?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by IBUA on 2009-03-22
Hey,

Basically i'm trying to get Hydrogen to the work the best it can on Ubuntu 8.04, and everywhere says to use JACK.

Unfortunalty i'm having a big problem in finding a understandable tutorial to teach me in how to install and set up (one slightly off topic question is does the soundcard matter?)

I know if you download Ubuntu Studio you get it automatically installed, but i don't particually want to through that faff again, as i havn't had the greatest expereince with it at all. (Also i only want to use Hydrogen, and UStudio has waaayyy too many irrlevant programs for me).

SO BASICALLY:

Could somehow give me a simple "noob-friendly" guide to downloading/installing/set up JACK And then getting it to work with Hydrogen? W/out Having to install Ubuntu Studio.

Cheers in Advance.

---

### Post by kansasnoob on 2009-03-22
How are you trying to install hydrogen?

Have you checked synaptic?

---

### Post by JohnLM_the_Ghost on 2009-03-22
**qjackctl** is a GUI Tool for JACK.
It allows you to setup settings and connections.

Install with:
```
sudo apt-get install qjackctl
```

There is also a good site explaining configurations
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)
and connections
[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

---

### Post by IBUA on 2009-03-22
> **kansasnoob said:**
> How are you trying to install hydrogen?

Have you checked synaptic?

Yes i downloaded that, And it works fine, it's mainly JACK i don't know how to get and so on.

---

### Post by IBUA on 2009-03-22
> **JohnLM_the_Ghost said:**
> **qjackctl** is a GUI Tool for JACK.
It allows you to setup settings and connections.

Install with:
```
sudo apt-get install qjackctl
```

There is also a good site explaining configurations
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)
and connections
[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

Ok, Does the JACK GUI Install jack for me then?
And does the soundcard matter?

---

### Post by JohnLM_the_Ghost on 2009-03-22
> **IBUA said:**
> Ok, Does the JACK GUI Install jack for me then?
And does the soundcard matter?
Yup, it has **jackd** (JACK daemon) as a dependent package, so it will install it.

Hmm... and sound card matters the same amount all other PC components do. Better sound card gives better performance, but asides that... if it is supported by ALSA it should work just fine!

---

### Post by IBUA on 2009-03-22
> **JohnLM_the_Ghost said:**
> Yup, it has **jackd** (JACK daemon) as a dependent package, so it will install it.

Hmm... and sound card matters the same amount all other PC components do. Better sound card gives better performance, but asides that... if it is supported by ALSA it should work just fine!

Fair enough, Cheers for the help :)

It works now! :)

---

