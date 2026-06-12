---
title: "Noip2 How to know it is on?"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by LowMen on 2008-08-27
I installed noip2 and I am able to pull up the help window showing all the commands.  I cannot see how to tell it is running, in Windows you can see in the tray.  How do you tell it is running in Ubuntu?

Thank you.

---

### Post by tsaid on 2009-01-11
In a terminal, simply type:

```
ps -A | grep noip2
```

If you get no result, then it's not running.

---

### Post by emptythevoid on 2009-01-27
I installed noip2 on 8.04 using Synaptic and it worked just fine (the program ran at boot).  However on 8.10, it did not run at boot.  I ran update-rc.d and it says a link already existed, which i confirmed, but it still refused to run at boot time.  I had to edit the /etc/rc.local to include a pointer to  /etc/init.d/noip2 start to get it to run at boot time  (or use the Sessions manager in Gnome).  Anyone else have this problem?

---

### Post by mexlinux on 2009-03-04
I have the exact same problem in Intrepid

---

### Post by svsig on 2009-03-24
I also had this problem, and I solved it in another way. 

In the script that is supposed to run at startup, /etc/init.d/noip2, the runlevels are specified. Runlevel 2 was different from other similar files in my system, it was specified for default-stop. I changed the lines for default-start and default-stop in /etc/init.d/noip2 from 
```
# Default-start:     3 4 5
# Default-stop:      0 1 2 6
```
to
```
# Default-start:     2 3 4 5
# Default-stop:      0 1 6
```
Then it worked.

---

### Post by mexlinux on 2009-04-11
# Default-start:     3 4 5
# Default-stop:      0 1 2 6

Are both lines comments....that doesn't make any sense

---

### Post by EzraReeves on 2009-04-13
You can check if noip2 is running by doing:
```
sudo noip2 -S
```

noip2 makes an init.d script by default but it has an error. It is'nt set to start at bootup in runlevel 2 (the default runlevel), as a previeous user pointed out.

A very good tool to change which services start and which dont in different runlevels is sysv-rc-conf.

```
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
```

You will notice that in noip2's row under runlevel 2 there is no x. Use the spacebar to toggle.

---

