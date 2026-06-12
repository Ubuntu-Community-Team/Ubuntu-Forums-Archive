---
title: "How do i kill a process or program through Terminal?"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Firestem4 on 2009-01-16
As the title says. my main problem is my firefox process does not close (firefox and firefox-bin) and Terminal loads faster than System Monitor, so i was wondering what the command was.

Thanks =)

---

### Post by ibuclaw on 2009-01-16
**HowTO No.1)**
Run:
```
killall **firefox**
```
Where "firefox" is the name of the application executable.


**HowTO No.2)**
```
ps -el | grep "**firefox"**
```
You will get an output like this:
```
0 S  1000 **12166**     1  0  80   0 - 150509 279341 ?       00:00:46 firefox
```
Note the number in the **4th** column, that is the Process ID number.
Now run:
```
kill -9 **12166**
```
To kill it.

Regards
Iain

---

### Post by caro on 2009-01-16
One way:

```
top
```

You will see a list of processes.  Enter "kill" and then the process number.

Or, another way is to use the command
```
killall firefox
```

---

### Post by Seq on 2009-01-16
> **Firestem4 said:**
> As the title says. my main problem is my firefox process does not close (firefox and firefox-bin) and Terminal loads faster than System Monitor, so i was wondering what the command was.

Thanks =)

`kill PID`, where PID is the process ID. You can find this from `ps ax`. Or if you know the binary name (which you do) you could use `pkill NAME`. Or if there was more than one process and you wanted to kill a bunch of them, you could use `killall NAME`.

If it is stubborn, try adding the -9 signal as an argument (kill -9 PID). For more information on these, read the manpages. The kill manpage has a list of applicable signals

---

### Post by Seq on 2009-01-16
I'm forever late to the show.

---

### Post by Firestem4 on 2009-01-16
Thanks all! Does anyone know where the SOLVED button went?

---

### Post by caro on 2009-01-16
> **Firestem4 said:**
> Thanks all! Does anyone know where the SOLVED button went?

It's been removed while they try to get a handle on the problems the forums have had the past few days.

---

### Post by ibuclaw on 2009-01-16
> **Firestem4 said:**
> Thanks all! Does anyone know where the SOLVED button went?
Is it not under **Thread Tools** ?

I honestly don't know then...
Must have been some serious database issues this week (we've been having some frequent downtime), all thanked posts are gone :(

Regards
Iain

---

### Post by donkyhotay on 2009-01-16
Vanished for now due to database error (just like the 'thanks' system). They're planning on putting it back but no idea on when that will happen.

---

### Post by Firestem4 on 2009-01-16
ok cool, thanks for clearing that up.

---

