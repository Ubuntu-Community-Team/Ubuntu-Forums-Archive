---
title: "how to stop a misbehaving program from Terminal"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by nns2006 on 2009-08-13
Hi,
how can i stop a misbehaving program from terminal. i know force quit is there to do this otherwise.
thanks

---

### Post by mikewhatever on 2009-08-13
killall program_name

---

### Post by wizard10000 on 2009-08-13
Two ways to do it.

You can run top and get the process id (PID) and issue a

```
sudo kill *PID*
```

or if you know the name of the program you can do it this way -

```
sudo killall *process_name*
```

Hope this helps -

---

### Post by rizman on 2009-08-13
Try the ```
killall
``` command

Here's a link [http://www.linfo.org/killall.html](http://www.linfo.org/killall.html)

```
killall the_program_to_kill
```

Edit: I think the ubuntuforums are the only forums on the net where you get answers from 3 different people within 1 Minute :-) It's just great

---

### Post by arochester on 2009-08-13
Have you tried xkill?

In a terminal input: xkill

The cursor changes to an X.

Place the X on the thing you want to kill. Click. It's gone.

---

### Post by nns2006 on 2009-08-13
> **wizard10000 said:**
> Two ways to do it.

You can run top and get the process id (PID) and issue a

```
sudo kill *PID*
```

or if you know the name of the program you can do it this way -

```
sudo killall *process_name*
```

Hope this helps -


I did this but i am not able to stop this program.terminal gives me this output 
nityanand@nityanand-laptop:~$ sudo killall AllTray
[sudo] password for nityanand: 
AllTray: no process killed


i am attaching the screen shot of the program.

---

### Post by nns2006 on 2009-08-13
> **arochester said:**
> Have you tried xkill?

In a terminal input: xkill

The cursor changes to an X.

Place the X on the thing you want to kill. Click. It's gone.


its not stoping. 
i have attached the screen shot of the program.

---

### Post by wizard10000 on 2009-08-13
> **nns2006 said:**
> I did this but i am not able to stop this program.terminal gives me this output 
nityanand@nityanand-laptop:~$ sudo killall AllTray
[sudo] password for nityanand: 
AllTray: no process killed

i am attaching the screen shot of the program.

Maybe the name of the process isn't AllTray - check top and make sure.

Also, you can add a spiffy kill icon to your panel if you want - you click the icon and then click the misbehaving window.  That works pretty well too.

You can also kill the process from within System Monitor.

---

### Post by nns2006 on 2009-08-13
> **wizard10000 said:**
> Maybe the name of the process isn't AllTray - check top and make sure.

Also, you can add a spiffy kill icon to your panel if you want - you click the icon and then click the misbehaving window.  That works pretty well too.

You can also kill the process from within System Monitor.


thank you. i get rid of it. i kill it from System Monitor.

---

### Post by Yaspoon on 2009-08-13
Also to kill the process from terminal you can use
```
ps ax
```
that will list all the currently listed processes then using grep you can look through the processes for the running one.
```
ps ax | grep AllTasks
```
that will only show the tasks called AllTasks it will also on the very left hand side have a number you can then use
```
kill 4999
```
that will kill the process with the process number 4999
if the process still fails to end yo ucan use the -9 signal which is dangerous!!!
```
kill -9 4999
```
That will force the process to end

Hope this helps

---

### Post by Barrucadu on 2009-08-13
To find a process which contains a certain string anywhere in the command line, use `pgrep -f`:

```
kill -9 `pgrep -f <pattern>`
```

---

### Post by pascie on 2011-08-29
> **arochester said:**
> Have you tried xkill?

In a terminal input: xkill

The cursor changes to an X.

Place the X on the thing you want to kill. Click. It's gone.

Thanks for the tip!
Worked for me..
I know there was a GUI application for it in ubuntu, but couldn't find it anymore..

---

### Post by PayPaul on 2011-09-19
> **Yaspoon said:**
> Also to kill the process from terminal you can use
```
ps ax
```
that will list all the currently listed processes then using grep you can look through the processes for the running one.
```
ps ax | grep AllTasks
```
that will only show the tasks called AllTasks it will also on the very left hand side have a number you can then use
```
kill 4999
```
that will kill the process with the process number 4999
if the process still fails to end yo ucan use the -9 signal which is dangerous!!!
```
kill -9 4999
```
That will force the process to end

Hope this helps
Thank you very much. I'm saving this thread. I was looking for a way to kill the Winecfg process that's been locked all day long. That is just plain beautiful! In additional now I know how to find the processes running. Hmmm. Ubuntu is looking better by the day!!

---

### Post by sisco311 on 2011-09-19
Necromancing.

Thread closed.

---

