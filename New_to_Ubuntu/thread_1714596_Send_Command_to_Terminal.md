---
title: "Send Command to Terminal"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by Hovercat on 2011-03-25
I have a Minecraft server running through one Terminal, I want to be able that when cron executes a bash script, it sends the command to the terminal "save-all" (which is a Minecraft server command).  How can I do this?

---

### Post by Hovercat on 2011-03-26
Bump

---

### Post by Cheesehead on 2011-03-26
See [http://ubuntuforums.org/showthread.php?t=514054]("http://ubuntuforums.org/showthread.php?t=514054")

Bumping more frequently than 24 hours is considered rude in this forum.

---

### Post by Hovercat on 2011-03-26
That's out of my league, forget it.

---

### Post by Cheesehead on 2011-03-26
It's not that hard. Just play with it a little, send a test command between ttys, and you'll get the hang of it within 10 minutes.

---

### Post by phil338198 on 2011-10-13
Hi! I'm in exactly the same situation.
I've read and tried everything I could find about doing something like this:
ls -l > /dev/pts/1
and it all works as described.
The thing is, this displays the output of the command in the terminal pts/1. What I need is for the command to be executed by pts/1.

Example:
In pts/1 I have python running in interactive mode. It shows
```
>>>
```I'm in pts/2 and i want pts/1 to execute "exit()". If I type
```
ls > /dev/pts/1
```it displays the output of the ls command in pts/1 and that's it.
If I type
```
exit() > /dev/pts/1
```then pts/2 tells me that there is an error with the command (which is normal since it's a wrong syntax for a bash command)
If I type
```
"exit()" > /dev/pts/1
```then pts/2 displays exit() but does not execute it.
I also tried variations of
```
echo "exit()" and echo -ne "exit()/n"
```
to send a line return, but it does not work. Also, if I go to pts/1 to press RETURN after I sent exit(), it acts as if exit() was never there.

It seems like the method I tried will only send things to the display of another terminal. I would like to send things to the input of a terminal to make it execute it. In the minecraft case, I need the server (which has an interactive command prompt) to execute the command "save-all", which does not works using
save-all > /dev/pts/1


I hope I have been clear enough for someone to be able to help us both!

---

### Post by sysmastr on 2012-07-04
What you guys are looking for is 

```

$ writevt -t /dev/ttyX -T 'helloworld'

```resp.
```

$ writevt -t /dev/ptsX -T 'helloworld'


```Even if you don't use bash, please don't bash *me* (haha love that pun) for replying to this older thread, because this issue took me countless minutes to solve myself, and, as you know, Google washes these kinds of posts up on the shore quite frequently, so these might help future users as well, even after years. :P

---

