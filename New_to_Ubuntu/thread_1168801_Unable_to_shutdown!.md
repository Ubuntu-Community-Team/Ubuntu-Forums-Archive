---
title: "Unable to shutdown!"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by Oded on 2009-05-24
Hi,
I'm using 9.04 64bit on my HP EliteBook 6930p
As of today I cannot Shutdown(or reboot)...
I press it, it closes all windows and goes into the usplash(?) screen and then hangs halfway. After playing around with ctrl-alt-del I've seen this printings:```
usplash: can't get console font: invalid argument
* Stopping VirtualBox kernel module
 Done.
* Stopping the Winbind daemon
* Stopping the system clock
* Stopping atieventsd
```
I tried de-activating the ATI driver and then reboot but it still hangs...
Important to note it was fine for 2-3 weeks or so

Thanks in advance!

---

### Post by shifty_powers on 2009-05-24
might sound odd, but i used to get a similar problem connected to my wireless. When it shuts down, wait till it stops and then press the power button again. That used to kick start the process again for me...

---

### Post by Oded on 2009-05-24
Sadly this does not help,
it does seem to 'kick start' the shutdown process again but halts at about the same point
halp :|

---

### Post by shifty_powers on 2009-05-25
> **Oded said:**
> Sadly this does not help,
it does seem to 'kick start' the shutdown process again but halts at about the same point
halp :|

what i meant was, shut down using the normal method, wait till it gets stuck THEN press the power button again.

might not make a blind bit of difference but you never know.

also does

```
sudo shutdown -n
```

work? (away from my linux box atm, have to excuse me ;))

---

### Post by Oded on 2009-05-25
> **shifty_powers said:**
> what i meant was, shut down using the normal method, wait till it gets stuck THEN press the power button again.
might not make a blind bit of difference but you never know.
also does
```
sudo shutdown -n
```
work? (away from my linux box atm, have to excuse me ;))
I did just that, initiating a normal shutdown and then pressing the power off button again.
At the moment I'm shutting it down by cutting the power which makes me scared to turn it on in the first place.
Is there no way to 'debug'(?) the shutdown process to figure out what's up?

---

### Post by andrew.46 on 2009-05-25
Hi shifty_powers,

> **shifty_powers said:**
> 
also does
```
sudo shutdown -n
```
work? (away from my linux box atm, have to excuse me ;))

Might be better:

```
sudo shutdown -h now
```

I have never used the -n option myself but the man pages have a small warning about its use:

```

-n     [DEPRECATED]  Don't  call  init(8)  to do the shutdown but do it
ourself.  The use of this option is discouraged, and its results
are not always what you'd expect.

```

All the best,

Andrew

---

### Post by shifty_powers on 2009-05-25
well i did say i was away from my linux machine :P

---

### Post by Oded on 2009-05-25
I'll try using the -n flag on shutdown when I'm in reach of my laptop, I'm assuming (if it works) that it would be safer than cutting off power to the laptop at the halt point...
Will let you know ;)

---

### Post by Oded on 2009-05-25
I've tried using the -n flag...no cigar
Please help me avoid my 3rd reinstall in a week!

---

