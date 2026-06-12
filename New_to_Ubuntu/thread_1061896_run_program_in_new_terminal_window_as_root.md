---
title: "run program in new terminal window as root"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by rgb96 on 2009-02-06
Okay, so I want to use terminal, to open a new terminal window, and run a program that can only be run as root. Is that even possible? So far what I've come up with is: 
```
gnome-terminal --execute sudo asterisk -vvvvvvc
```
But then I get stuck, because I don't know how to enter the password from the first terminal, or pass it as an argument.

Before you say, "why not just type in the password when the new screen comes up?" I'm trying to write a program to automate using that program to test equipment, and I'm just trying to come up with what command to give the system.

Thanks in advance.

---

### Post by Hospadar on 2009-02-06
Is this a program that requires user interaction? or is the point of the program to not be touched by humans, and maybe they just read a log file?

If it requires human interaction, or humans are supposed to be watching it, maybe try using "gksu", it'll give you a nicer program.

If you just want something to run in the background and write stuff to some logfile you can check at your lesuire, probably making a cron job would be a better choice.  Cron is a basic linux/unix utility to allow you to schedule programs to run at certain times.  To add cronjobs to be run as root, you can do a "sudo crontab -e" in a terminal.  You'll probably want to google up about cron and how to use it, the main important points are how to format the times, and the fact that you need to use the absolute path names for executables (i.e. /usr/bin/asterisk (or wherever it is) instead of just asterisk).  These jobs will be run as root, and do not need sudo.

Alternatively, it is possible to make it so sudo doesn't ask for a password, but it's (obviously) rather insecure.  If it's just a test machine though, it'd probably be fine.  Google (sudo without a password) or some such, as I recall, there's info on how to make it happen.

---

### Post by rgb96 on 2009-02-06
Yeah. It's a program that has to be running in the background. I think it is basically a software interface between the loopback interface, and the PRI card in this machine. The PRI card generates up 97 VoIP phone calls and sends them to wherever we tell it to. The sudo without a password might be an option, but I think I'll research a bit more first.

---

### Post by rgb96 on 2009-02-06
Oh. I figured it out. 

by using -S as argument for sudo, you can pipe in something from stdin. so the command I was looking for was 

```
gnome-terminal --execute echo password | sudo -S asterisk -vvvvvvc
```

Just in case anyone else wants to know too.

---

