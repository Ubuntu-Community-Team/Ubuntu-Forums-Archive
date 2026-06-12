---
title: "Intrepid Ibex"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by magh-87 on 2009-02-05
Today I upgraded from Hardy Heron to Intrepid Ibex and everything ran smoothly until after the reboot. The system rebooted and showed everything as normal however now it appears that my computer is stuck in between screens. The only screen displayed has been the Ibex background and my mouse in the center showing that it's constantly loading, however I can't move the mouse around. What could I do to solve this issue short of installing 8.04 or 8.10 all over again?

Thanks for any help,

Magh

---

### Post by OffAxis on 2009-02-05
what happens if you try to restart x with 

**Ctrl+Alt+Backspace**

?

---

### Post by magh-87 on 2009-02-05
Nothing happens, the keyboard and mouse stop responding

---

### Post by OffAxis on 2009-02-05
Does the keyboard initially work - can you select another line item in the GRUB menu?

Usually it's video drivers or newly enabled hardware modules that tank a system like that. The easiest fix is to try and boot to a command line or 'Recovery Console' (from the GRUB menu) and try a 

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

There's been a lot of updates since Intrepid's release.

you can also try starting the desktop from the command line and see what errors are output to the console.



There's also a log file you can look at 

```
tail syslog
```

to get an idea of what went wrong

---

### Post by magh-87 on 2009-02-05
I did both the update and upgrade but there was nothing to update/upgrade. As for the syslog, I couldn't find that. Is there something more that I should be trying?

I let it go for the day while I was at work in the hopes that something more might happen, but nothing. This is becoming rather discouraging for 8.10 :( I fear I may have to re-burn the iso and re-install Hardy

---

### Post by abyssius on 2009-02-06
> **magh-87 said:**
> I did both the update and upgrade but there was nothing to update/upgrade. As for the syslog, I couldn't find that. Is there something more that I should be trying?

I let it go for the day while I was at work in the hopes that something more might happen, but nothing. This is becoming rather discouraging for 8.10 :( I fear I may have to re-burn the iso and re-install Hardy

If you choose to re-install Hardy, you'll join a host of others including myself who had to do the same thing due to system lock-ups. Those that report this, usually updated from hardy to ibex via the update process. I re-installed 8.04 on one partition and 8.10 on another partition. The 8.10 version booted alright after a fresh install, but kept randomly freezing with not way out except a hard reset. i believe this is hardware related. I had an nvidia card which I suspected was causing the problem, even though it worked perfectly in 8.04.1 I'm presently running both systems with an old ATI card replacement, with no more lock-ups in 8.10.

---

### Post by hamdi on 2009-02-06
I think you need to fresh install Ubuntu 8.10

---

### Post by magh-87 on 2009-02-06
Okay thanks. I have the iso saved on my laptop, forgot I had it there so I'll try that tomorrow and hopefully that'll work out for me. Otherwise I'll stay with 8.04 which worked fine :p

Thanks for the help and if I have issues past the clean install I'll let you know. 

Magh

---

