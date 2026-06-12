---
title: "Suddenly Ubuntu is running very slowly, lots of unresponsive programs.."
date: 2009-03-13
forum: New to Ubuntu
---

### Post by tegnoto89 on 2009-03-13
Recently Ubuntu has been sort of choking up on me; my programs keep going unresponsive for a few seconds, things are taking much longer to load..  What could this be?

---

### Post by mcla0203 on 2009-03-13
Check out your processes and first verify that there is nothing hefty that got installed and is hogging up your system.  There's a process moniter tool with a nice gui or use the "ps" command.  "man ps" for on ps.

---

### Post by JPtux on 2009-03-13
Weird.... check your swap.
How much ram do you have?

---

### Post by mkvnmtr on 2009-03-13
Another thing to check is how full your disk is. When you have verylittle space things quit working well. start by emptying the trash.

---

### Post by viljun on 2009-03-13
Open up terminal and type: top. You'll see there what's eating your processor power.

Also you might consider to disable your search indexing if you need it - or other services (but don't mess with power manager services as your red shut down button may become _very_ slow to react). Sometimes it may also be firefox - so close it and open again or try opera. Or just reboot and see if the problem persists. But top is your friend - so post the output of it here if you don't understand it. (Just paint text on the terminal with your mouse and _middle_ click on browser to copy the text there)

(Services are found here: System > Admistration > Services)

---

### Post by tegnoto89 on 2009-03-13
Okay here's what the command "top" gives me:

```
top - 22:46:55 up 58 min,  2 users,  load average: 0.47, 0.58, 0.40
Tasks: 123 total,   2 running, 121 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.8%us,  1.4%sy,  0.0%ni, 89.7%id,  0.0%wa,  0.7%hi,  0.4%si,  0.0%st
Mem:   3098480k total,   805884k used,  2292596k free,    39196k buffers
Swap:  6385796k total,        0k used,  6385796k free,   446712k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6395 tom       20   0  292m  86m  28m S    9  2.8   6:57.56 firefox            
 5704 root      20   0  855m  43m 9188 R    1  1.4   2:03.47 Xorg               
 6132 tom       20   0 69516  30m  10m S    0  1.0   0:42.94 compiz.real        
 6154 tom       20   0 29472  11m 8416 S    0  0.4   0:04.22 nm-applet          
10207 tom       20   0 76692  19m  11m S    0  0.7   0:00.62 gnome-terminal     
10232 tom       20   0  2308 1120  856 R    0  0.0   0:00.22 top                
 6541 tom       20   0  166m  47m  20m S    0  1.6   6:30.29 rhythmbox          
    1 root      20   0  2844 1692  544 S    0  0.1   0:02.34 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.06 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.08 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1     
```

I emptied the trash as well.  I can't yet tell if that helped, but I do have 90 of 160 GB of hard drive left.  I'm running 2GB ram.

---

### Post by firefly2442 on 2009-03-13
I assume you tried restarting?

---

### Post by mkvnmtr on 2009-03-13
If you have 90n Gb left you are not getting close to being full. 
Top is nice but I think you will like to use Htop better. It is just a minute or so download. If it is not just Firefox you should see it in Htop. Sometimes I have had some kind of audit taking 100% of my cpu. I never did figure it out but it passed. Maybe an upgrade. But in that same time frame I started to uninstall everything I don't use like palm services, Evolution, Ekiga phone and compiz.

---

### Post by viljun on 2009-03-14
Did you get that kind of top output when your system was slow? (If not, please paste the output while your system is slow.) You should check on the top list what programs are using most cpu power - should be at least 15%.

---

### Post by humphreybc on 2009-03-14
Could it be indexing working in the background?

---

### Post by Funk Algoma on 2009-04-02
Hey Guys what is Xorg? 
I had the same problems in these days and i found this page very interesting, so i tried top on my terminal and i've seen it blowing a lot of memory...
By the way i'm Funk Algoma and i'm new. Thanks for helping.

---

### Post by some_random_noob on 2009-04-09
> **Funk Algoma said:**
> Hey Guys what is Xorg? 
I had the same problems in these days and i found this page very interesting, so i tried top on my terminal and i've seen it blowing a lot of memory...
By the way i'm Funk Algoma and i'm new. Thanks for helping.

Xorg renders and draws graphics on the screen... I'm having trouble with it too. It uses up 100% CPU when I run a 3d game. Can anyone help?

Edit: Fixed it by installing libgl1-mesa-dri - note of course that this problem which I had ONLY affected 3d games. This is not a magical solution to all xorg related problems.

---

