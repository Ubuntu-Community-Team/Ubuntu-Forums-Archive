---
title: "Trouble installing oracle 11g enterprise edition on ubuntu 8.10 intrepid"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by aksingh99 on 2009-01-30
Hi, I've just installed ubuntu 8.10 on my machine (no xp).

I want to know how I can install oracle 11g enterprise edition on my machine.

I've already downloaded the file but when I try to run the installer, I get a lot of errors. I found one tutorial online but this is really beyond me:

[http://www.pythian.com/blogs/1355/installing-oracle-11gr1-on-ubuntu-810-intrepid-ibex](http://www.pythian.com/blogs/1355/installing-oracle-11gr1-on-ubuntu-810-intrepid-ibex)

I was thinking of downloading wine and then running windows version of oracle 11g from there.

---

### Post by yeats on 2009-01-30
Wow - I didn't realize Oracle ran on Linux :-).

If you actually need Oracle (for work or something), I don't think Wine is going to cut it, unfortunately.  Wine is great - don't get me wrong - but it doesn't provide the full Windows environment to support huge programs like Oracle.  (I wouldn't think . . .)

Anyway, if you DON'T need Oracle, try PostgreSQL, which is available through the Synaptic Package Manager and is a full-featured, very trustworthy open source RDBMS.  I'll look at the tutorial you've got and see whether I can help you, though . . .

UPDATE: Just looked, and I agree that it is quite involved (though it does seem like a clearly denoted step-by-step).  I would use PostgreSQL or even MySQL, depending on your needs. :-)

---

### Post by jrusso2 on 2009-01-30
> **aksingh99 said:**
> Hi, I've just installed ubuntu 8.10 on my machine (no xp).

I want to know how I can install oracle 11g enterprise edition on my machine.

I've already downloaded the file but when I try to run the installer, I get a lot of errors. I found one tutorial online but this is really beyond me:

[http://www.pythian.com/blogs/1355/installing-oracle-11gr1-on-ubuntu-810-intrepid-ibex](http://www.pythian.com/blogs/1355/installing-oracle-11gr1-on-ubuntu-810-intrepid-ibex)

I was thinking of downloading wine and then running windows version of oracle 11g from there.

Actually that guide looks pretty straight forward and step by step unless your really new to Linux.

---

### Post by aksingh99 on 2009-01-30
> **jrusso2 said:**
> Actually that guide looks pretty straight forward and step by step unless your really new to Linux.

Well, I just started today but have little exposure to ubuntu (as well as a few other linux distros).

One thing I didn't understand in that tutorial is how to proceed when ubuntu is already installed on the machine and what is pythian ??

---

### Post by jrusso2 on 2009-01-30
Pythian is a company name it seems.  This guy installed it on an ibex virtual machine so I would start by making sure all the updates are run first and go from there.

---

### Post by yeats on 2009-01-30
> **aksingh99 said:**
> One thing I didn't understand in that tutorial is how to proceed when ubuntu is already installed on the machine and what is pythian ??

I would probably start with the "Let's create some users" section, myself.

---

### Post by jrusso2 on 2009-01-30
Either way would work but if he can't get it installed no use in having a users group for oracle.

---

### Post by aksingh99 on 2009-01-30
> **chrissharp123 said:**
> I would probably start with the "Let's create some users" section, myself.

Ok I will give it a try.

Will update and see if it gets installed. I suppose a few errors can also be neglected

---

