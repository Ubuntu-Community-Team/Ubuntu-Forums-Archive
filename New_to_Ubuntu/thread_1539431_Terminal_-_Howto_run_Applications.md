---
title: "Terminal - Howto run Applications"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by Krabby.Linux on 2010-07-26
Hey,

does anyone know how to start more than 1 Application with the Terminal?Usually the Terminal is Occupied while the Program runs. I dont want to start lots of Terminals one by one ...

And how do I create a file where a few Programs start automatically (for example after Loging In Thunderbird Firefox Empathy etc etc. at once when I choose to click on it :))
thanks

---

### Post by bodhi.zazen on 2010-07-26
> **Krabby.Linux said:**
> Hey,

does anyone know how to start more than 1 Application with the Terminal?Usually the Terminal is Occupied while the Program runs. I dont want to start lots of Terminals one by one ...

Use the &

```
command &
```> And how do I create a file where a few Programs start automatically (for example after Loging In Thunderbird Firefox Empathy etc etc. at once when I choose to click on it :))
thanksThis is called a bash script

```
#!/bin/bash

# A few comments on what the script does
# More comments

command1 &
command2 &

...


```See also : [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by nmaster on 2010-07-26
add an & after the command. for example, 
```

vlc &
evince &
firefox &

```

the '&' backgrounds the process.

---

### Post by surfer on 2010-07-26
```
$ command -flags args **&**
```

the ampersand (&) at the end of the line sends the job to the background.
```
$ jobs
```
will list the jobs currently running in that shell.

---

### Post by Krabby.Linux on 2010-07-26
Thanks for the quick responses!

what if my Terminal is occupied and there is already a program running. Can I "add" the command with the & Operator? Or is it just working while my Terminal is not occupied?

---

### Post by Krabby.Linux on 2010-07-26
Ok Surfer just answered my questions before I was posting my questions! THANKS

---

### Post by sisco311 on 2010-07-26
EDIT: wow, i'm slow!

You could create a launcher on the Desktop or a panel. Type something like:
```
sh -c "thunderbird & firefox & empathy"
```in the command field.

---

### Post by sisco311 on 2010-07-26
> **Krabby.Linux said:**
> Thanks for the quick responses!

what if my Terminal is occupied and there is already a program running. Can I "add" the command with the & Operator? Or is it just working while my Terminal is not occupied?


You can stop a job with the suspend character ^Z (Ctrl-z) and use bg (fg) to continue the job in the background (foreground).

See:
```
man bash | less +/^"JOB CONTROL"
```

EDIT:
Or use screen: [uhelp]community/Screen[/uhelp] or dwtm. 

On the virtual consoles, I prefer fbterm.

[http://kmandla.wordpress.com/2010/05/28/fbterm-birth-of-the-cool-for-the-console/](http://kmandla.wordpress.com/2010/05/28/fbterm-birth-of-the-cool-for-the-console/)
[http://kmandla.wordpress.com/2009/03/01/dvtm-rocks-my-fscks/](http://kmandla.wordpress.com/2009/03/01/dvtm-rocks-my-fscks/)

---

### Post by WRDN on 2010-07-26
To add to the information currently provided, you can use the command, "fg" to make the program the foreground process.

Use the "jobs" command, then you can use "fg" to bring to the foreground any of the background processes.

For example:

```

sleep 1000 &
sleep 2000 &
sleep 3000 &

```

Running jobs tells me:

```

[1]   Running     sleep 1000 &
[2]-  Running     sleep 2000 &
[3]+  Running     sleep 3000 &

```

To start the process "sleep 2000" (number 2), I can then type:

```
fg 2
```

---

