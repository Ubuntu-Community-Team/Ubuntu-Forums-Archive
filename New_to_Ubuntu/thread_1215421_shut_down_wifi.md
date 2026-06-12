---
title: "shut down wifi"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by marcopalla on 2009-07-17
Hi, on my laptop I'd like to have not active wifi for default (I don't use often and passwords request annoy me a lot, plus battery consupction),
so I'm trying to write a script to run at the start up do do this,
both wifi and cable works great,
BUT I've a problem in shutting down wifi.

#sudo ifconfig 
>eth0 ...... (my cable connection)
>lo ... (the loopback...)
>Wmaster0... (I think the wifi)

#sudo ifdown Wmaster0
> Wmaster0 is not configured (???)

any idea? wifi works.... but is too hard too die ;-)

thanx for any suggestion,
m.

---

### Post by zeroseven0183 on 2009-07-17
You can just turn the wireless device off by switching the button on your laptop.
 
I think that would be easier.

---

### Post by marcopalla on 2009-07-17
sometimes esyest solutions are the best solutions....
....sometimes definetly not ;-)

no switch button

---

### Post by s3a on 2009-07-17
Not sure but if sudo ifconfig says that your wireless card is wlan0 maybe doing:

sudo ifconfig wlan0 down

would work.

---

### Post by marcopalla on 2009-07-17
I don't think ia name problem, 
now I don't remember if is Wlan0 or Wmaster0 but I try the correct name displayed by ifconfig,

nor a command problem (I thinK)
"ifconfig XY down" and "ifdown XY" are the same command?

thanx 'bross

---

