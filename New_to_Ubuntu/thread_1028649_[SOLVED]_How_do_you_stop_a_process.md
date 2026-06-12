---
title: "[SOLVED] How do you stop a process?"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by scotttie on 2009-01-02
Hi everyone,
I seemed to have inadvertently started a presentation wizard which is no longer responding, could you tell me how I close a program which doesn't respond please?
thanks 
Scottie:confused:

---

### Post by bump_ on 2009-01-02
Open up a terminal and type the following

```
ps -e
```

which will list all the processes. Along the left side you will see the Process ID (PID) associated with each process. Find the process you want to kill by name and see its associated PID. Then type

```
sudo kill -9 PutPidHere
```

and that should kill it.

Alternatively, once you find the name of the process, you could type

```
sudo killall -9 PutProcessNameHere
```

Hope it helps

---

### Post by mc4100 on 2009-01-02
> **scotttie said:**
> Hi everyone,
I seemed to have inadvertently started a presentation wizard which is no longer responding, could you tell me how I close a program which doesn't respond please?
thanks 
Scottie:confused:

There is an applet you can add to the panel called, "force quit" -- if you click it, and then click the window which is unresponsive, it will terminate it.

An alternative way is to press Alt+F2, and type:
```
killall [and then the process name]
```

---

### Post by Shazaam on 2009-01-02
Another way is to open System>Administration>System Monitor>Processes, find the offending app and click the "End Process" button (bottom right).

---

### Post by caro on 2009-01-02
Open the terminal and enter:

```
top
```

You will see all the processes running.  Find the one you want to stop and enter:

```
k
```

K stands for kill.  Enter the number of the process and hit enter.

Be careful not to kill the wrong process.

---

### Post by donkyhotay on 2009-01-02
There is a 'force quit' applet you can add onto the panel that works pretty good. But the most certain way (if that fails or if you don't have it on your panel) is to bring up a terminal prompt and use
```
ps -e
```
to find the PID of the rogue process then use kill to fully terminate. For example if the process I want to kill has PID of 5514 then I would do
```
kill 5514
```
Sometimes of course depending on the process you may need to use sudo to have permission to terminate the process and *very* rarely even this won't terminate at which point you would need to use th -9 option to force it permanently down (I've only had to do this once). 
```
sudo kill -9 5514
```
but as I mentioned this is very rare and should only be used when all else fails.

---

### Post by scotttie on 2009-01-02
I have entered the ps -e and the affending program appears in the list approximatly 100 time! all with different numbers but the same program, any ideas please.
thanks

---

### Post by Copernicus1234 on 2009-01-02
> **scotttie said:**
> I have entered the ps -e and the affending program appears in the list approximatly 100 time! all with different numbers but the same program, any ideas please.
thanks

killall <programname> should do it. Did you try it?

---

### Post by bump_ on 2009-01-02
What is this process?

You can kill them all using the killall command, but make sure it is the right process you are killing first.

```
killall ProcessName
```

if that fails

```
sudo killall ProcessName
```

and if that fails

```
sudo killall -9 ProcessName
```

---

### Post by scotttie on 2009-01-02
Hi all,
done now but it was a stubborn little blighter, had to do killall -9 three times before it would go, kept freezing on me, but OK now.
I may be back with another thread in a mo as the cause of this one may crop up again but it will need a new thread.
thanks all
Scottie:D:D

---

