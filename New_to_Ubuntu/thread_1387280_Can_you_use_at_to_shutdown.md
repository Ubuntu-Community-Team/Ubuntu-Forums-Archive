---
title: "Can you use at to shutdown?"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by dvfreelancer on 2010-01-21
I'm using 9.04 and trying to figure out how to use the at command to shutdown at a specific time.  

I tried:

at 2pm
at>halt
ctrl+d

at 2pm
at>shudown
ctrl+d

at 2pm
at>sudo shutdown
ctrl+d

I changed the times, of course, but none of those worked.  It saved all the jobs, but nothing happens.  What am I missing?

---

### Post by Revolutionary101 on 2010-01-21
What you need to do is type:

```
sudo shutdown -P 18:45
```

That is just an example. This would shutdown your computer at 6:45 pm. It doesn't have to say -P, you could change that to the restart command or any other shutdown commands. The time after the command must be in the 24 hour time format. Instead of the time you could also type "now" which results in an immediate shutdown. You could also type:

```
sudo shutdown -P +m 4
```

That command would shutdown the computer four minutes after that command was executed. The +m indicates that the time will be set in minutes after the command is executed and the 4 just represents the numbers of minutes.

Hope it answers your question.

I know it isn't the at command but it does the same thing.

---

### Post by slooksterpsv on 2010-01-21
I did it:

at 4:26PM
at> shutdown --help > /home/shawn/test.tmp1
CTRL+D

so you would need to type

at 2pm
at>shutdown -h 0
ctrl+d

---

### Post by Bigtime_Scrub on 2010-01-21
I'm not 100% sure but I think in terminal

```
 sudo shutdown hh:mm 
``` sets the computer to shut down at a specific time using a 24 hour clock. I think that is the syntax but I'm not really certain.

Or you can try by opening up a terminal and typing ```
sudo contrab -e
```

---

