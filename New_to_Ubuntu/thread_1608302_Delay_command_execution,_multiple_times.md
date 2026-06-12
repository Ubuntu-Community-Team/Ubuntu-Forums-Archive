---
title: "Delay command execution, multiple times"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by djmac on 2010-10-28
I have been unsuccessfully trying to find a method to delay the execution of a command, multiple times to no avail.

Essentially, what I am trying to do is run a command every (say) 10 minutes, for (say) 10 iterations. I.e the command would run 10 times over 100 minutes. 

Anacron isn't really any use in this situation (nor cron), and 'sleep' is only useful for one delay, as I understand it. 

Any suggestions would be greatly appreciated.

---

### Post by marshmallow1304 on 2010-10-28
Like a loop?

In pseudocode:

```
i = 0
while (i < 10)
    run command
    sleep 10
    i++
```

---

### Post by uRock on 2010-10-28
Nevermind- Marshmallow1304 beat me to it.

---

### Post by papibe on 2010-10-28
Using 'sleep' in a loop may be fulfill your needs (example.sh):
```
#!/bin/bash
for i in 1 2 3 4 5 6 7 8 9 10
do
  /path/your_command
  sleep 10m
done

```
You can even run this in the background, adding a '&' at the end of the shell.

```
$ example.sh &
```

Good Luck!

---

### Post by darkhelmetchris on 2010-10-28
A quicky solution would be to string the commands together like this:

sleep 600; mycommand; sleep 600; mycommand ..
and so on as many times as you like.  This is a little bit manual, and there are better ways (like a for loop containing sleep).  But this is simple and fast.

If it were me, I might couple this with 2 other optional ideas:
1.  If your "command" is complicated, create a bash script of your own
2.  Call the script using it like the above example

Some of this actually CAN be done in cron natively using a parameter divisor.  For example, to run a particular command every 10 minutes during the hour of 3pm(15) try this:
# crontab format is - minute hour day month dayofweek command
*/10 15 * * * mycommand
This means:
every 10 minutes -- during hour of 3pm(15) -- any day -- any month -- any day of week -- the command you want
and will run at 15:00, 15:10, 15:20, 15:30, 15:40, 15:50 .. and stop.  Modify to your liking.  Perhaps using */6 for every 6 minutes, making 10 times in one hour.

Hope that suits your needs,
Chris

---

### Post by djmac on 2010-10-28
Thanks for your help! (and the speed of the help!). That works perfectly. Cheers

---

