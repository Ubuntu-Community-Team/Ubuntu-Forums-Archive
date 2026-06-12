---
title: "restart apache for php.ini 10.04"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by melbs on 2010-11-01
Hi all,

I've made changes to session.gc_maxlifetime and max_execution_time in php.ini. It is not showing in the php info (I'm editing the php.ini file it specified in that php info).

I am using ubuntu 10.04 and I've read a few things online saying you have to restart apache for the changes to take effect, but I wanted to make sure since this has never been the case in 8.04.

If I have to restart it is the command:
/etc/init.d/apache2 restart


[FONT=Verdana]Would it be different for each situation? Thanks![/FONT]

---

### Post by indytim on 2010-11-01
".ini" = initialization.  As in runs once at server startup.  Changes to the php.ini will only be reflected after the server has been restarted.

IndyTim / DataMan

---

### Post by melbs on 2010-11-01
In another installation (redhat) it took effect right away. Weird.

Okay, so does using apache: /etc/init.d/apache2 restart do it or does it need to be restarted another way? (sorry, newbie).

Also, how long does it take to restart?

---

### Post by sandyd on 2010-11-01
> **melbs said:**
> In another installation (redhat) it took effect right away. Weird.

Okay, so does using apache: /etc/init.d/apache2 restart do it or does it need to be restarted another way? (sorry, newbie).

Also, how long does it take to restart?

a) if your using a different implementation (ex php-cgi instead of the apacne module) it will take place instantly in some cases.

b) yes, that will restart it.

c) depends on how fast your computer is, mine takes 2 seconds.

---

### Post by melbs on 2010-11-01
Thank you very much, you guys are great!

---

