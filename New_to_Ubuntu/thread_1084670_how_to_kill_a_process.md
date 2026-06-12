---
title: "how to kill a process"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-03-02
recently i've come up with some programs stalling while trying to exit the program and i was wondering how i can kill a program from a terminal?

---

### Post by lykwydchykyn on 2009-03-02
Well, there's pkill and killall which can operate on a process name (or various other things, see the man pages for a full refernce), or the venerable "kill" which can operate on process ID numbers.

---

### Post by taurus on 2009-03-02
You can either kill it by name

```
sudo killall *prog_name*
```
or you can kill it by it PID (you can get the PID from this command.

```
ps -A
sudo kill -9 12345
```
Assuming 12345 is the PID of that program.

---

### Post by cipher_lx on 2009-03-02
Hi,

First you need to know the process Id or PID of a process that you want to kill or terminate and then use the 'kill' command.

For more information see [http://www.cyberciti.biz/faq/kill-process-in-linux-or-terminate-a-process-in-unix-or-linux-systems/](http://www.cyberciti.biz/faq/kill-process-in-linux-or-terminate-a-process-in-unix-or-linux-systems/)

---

### Post by WatchingThePain on 2009-03-02
There's a nice little app HTOP in synaptic. Htop list all the processes with process id's. Once you get the pid try kill 'pid'. Kill -9 'pid' is a sure kill (like sending Rambo in) but try not to do that a lot unless you are familiar with fsck.

---

### Post by jmmL on 2009-03-02
killall is quite useful. As an example:
```
killall firefox
```

Also there's **xkill**. Just type it in the terminal, and it will prompt you to click on a program window that you want to kill. Useful if you don't know the process name or PID.

---

### Post by WatchingThePain on 2009-03-02
Hmmm that's a new one xkill..I tried it and It is goooood. Better than piri-piri beef Jerky!.

---

### Post by metallicamike on 2009-03-02
add the force quit button to panel and use that

---

### Post by Messyhair42 on 2009-03-02
so for using a program ## is there a command that lists programs running (giving the names you can use to kill them)?

---

### Post by stchman on 2009-03-02
> **Messyhair42 said:**
> recently i've come up with some programs stalling while trying to exit the program and i was wondering how i can kill a program from a terminal?

If it a graphical program right mouse click and hit close.  This will command the force quit.

If it is a terminal use the kill -9 <process id> function.

---

### Post by jmszr on 2009-03-02
Messhair42.
           Sorry, when I reread the original post I realized it was from the terminal,oops.

---

### Post by lykwydchykyn on 2009-03-02
> **Messyhair42 said:**
> so for using a program ## is there a command that lists programs running (giving the names you can use to kill them)?

ps -e

---

### Post by handy on 2009-03-03
I just use htop, it lists the processes & you can kill the process from within htop.

---

### Post by RealG187 on 2009-03-03
> **jmmL said:**
> killall is quite useful. As an example:
```
killall firefox
```

Also there's **xkill**. Just type it in the terminal, and it will prompt you to click on a program window that you want to kill. Useful if you don't know the process name or PID.

Ya u can even add it to the gnome panel, but that doesn't help when you can't click on the Window like in this case:

[img]http://win.tue.nl/bcf/linux/usage/closeff.jpg[/img]
[http://www.win.tue.nl/bcf/linux/usage/firefox.php](http://www.win.tue.nl/bcf/linux/usage/firefox.php)

---

### Post by drubin on 2009-03-03
You could also use the xkill command This will turn your mouse into a cross and the next window you click on will be killed.

This is a similar easier way of doing it.  but might not work for really really crashed applications, so it is handy to know the kill -9 and killall commands

---

### Post by Messyhair42 on 2009-03-03
thanks, all questions answered. thread solved.

---

