---
title: "Equal to: CTRL+ALT+CANC ???"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by webwiller on 2009-08-01
Or...
how to end a crashing applicacion without having to restart ubuntu? Mozilla happens to crash frequently...and most of the times I have to restart the hole OS cause I dont know how to restart a single application.

Tx in advance for your kind help ;-)

WW.

---

### Post by llamabr on 2009-08-01
What happens when it crashes?  Try running it in a terminal, and then copy back the errors here.

In the mean time, you can find the process id (pid) by looking in top, or by running:

```
ps aux
```

to find the pid.  It'll look like this:

```
brock     4724  2.9 13.7 407580 140668 ?       Sl   Jul31  24:24 /opt/firefox/firefox-bin

```

and then run:

```
kill -9 4724
```

Which will kill the running firefox

---

### Post by irv on 2009-08-01
Just go to System>Administration>System Monitor and run. Go to the Processes tab find the process that you want to end, highlight and click the [End Process] button.
Here is a screen shot:
[ATTACH]123199[/ATTACH]

---

### Post by Sidewinder1 on 2009-08-01
Or the GUI way: Go to System---->Administration---->System Monitor--->Processes 
Find Mozilla/Firefox, right click on it and either Kill or Stop the process.
HTH, 
Side

---

### Post by Sidewinder1 on 2009-08-01
Irv beat me to it. Maybe someday I'll learn to type; not today. :-)

---

### Post by irv on 2009-08-01
> **Sidewinder1 said:**
> Irv beat me to it. Maybe someday I'll learn to type; not today. :-)

That's alright, I went back and added a screen shot to help clarify.

---

### Post by ridetheteapot on 2009-08-01
in addition to the other choices -- if you use gnome there is a nice little "force quit" applet for the panel. pretty useful for quickly killing hanging gtk apps. also there is killall <name>. it is a little sloppier though and will kill all instances of that process.

---

### Post by ecmatter on 2009-08-01
Related question:  what's the proper way to shut down and the proper way to reboot from the command line?  I have a 'command line only' Debian install, and the **reboot** and **shutdown** commands don't work.  I've been using **exit** to return to the login prompt, and then ^ALT-DEL to reboot, but half of the time the computer hangs during reboot.

---

### Post by irv on 2009-08-01
> **ecmatter said:**
> Related question:  what's the proper way to shut down and the proper way to reboot from the command line?  I have a 'command line only' Debian install, and the **reboot** and **shutdown** commands don't work.  I've been using **exit** to return to the login prompt, and then ^ALT-DEL to reboot, but half of the time the computer hangs during reboot.

I believe the shutdown command would look like this:
```
shutdown now
```
This would shut down the system and do it right now. I have used this on my server.

---

### Post by ecmatter on 2009-08-01
Thanks, irv.  It was the time argument that I was forgetting.

**shutdown** gives me a *command not found* error, but **sudo /sbin/shutdown now** followed by **poweroff now** at the *#localhost* prompt seems to work.

---

### Post by philinux on 2009-08-01
Alt+Sysrq+k = kill x session and takes you safely back to the login screen for when it's really hung.
And REISUB
[http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

---

### Post by irv on 2009-08-01
> **ecmatter said:**
> Thanks, irv.  It was the time argument that I was forgetting.

**shutdown** gives me a *command not found* error, but **sudo /sbin/shutdown now** followed by **poweroff now** at the *#localhost* prompt seems to work.

Glad I could help. It's the simple things that we forget. I remembered this because I made the same mistake when I was trying to shutdown a server at work a few years ago.

---

### Post by zerhacke on 2009-08-01
You could use 

sudo shutdow -h now

to turn the computer off.  the -h switch tells it to halt.

---

### Post by ridetheteapot on 2009-08-01
sudo shutdown now shoulddo the trick. similarly there is "reboot".

---

### Post by SuaSwe on 2009-08-01
I always use Alt+F2 *killall firefox* when it crashes; usually the whole system freezes up so going through several menu branches would take hours. :D

---

### Post by webwiller on 2009-08-03
Ty All!!!!!!

---

### Post by lunarmelody on 2009-08-03
You can also use 'sudo shutdown -r now' to reboot.

---

