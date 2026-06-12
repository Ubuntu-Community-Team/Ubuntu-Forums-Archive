---
title: "How to kill a process permanately on the OS level"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by so0ky on 2010-02-14
Okay,

I've been playing around with my rack server with Ubuntu Server 64 bit.  I pretty much have the required software installed to run a CS 1.6 server off of it.  Now I just have to configure not only the game itself, but my network as well.

One of the problems I have run into, is when I do kill jobid the same process pokes back up eventually.

I want the instance of the game server to end.  How do I do this with the kill command?  Is there a switch/option that I am missing?

Thank you once again.

---

### Post by bwhite82 on 2010-02-14
I use 'sudo killall processname'. Works for me everytime.

---

### Post by so0ky on 2010-02-14
Thank you for that.

But I may have answered my question.  When I ran this application, I ran it in the background with the & at the end of my command.

How do I bring the process to the foreground?  Thanks.

I did what you suggested and the process still comes back up.

---

### Post by so0ky on 2010-02-14
Here is more information that I thought was interesting.

I do the top command, and I see the process hlds_amd at the very top, taking most resources as it should.  I want to end this occurrence, as this is a game server.  I want to run a game server with other commands, but I don't want two game servers with one I am not using.  Hence, why I am trying to end this occurrence.

top command brings a PID of 3408 .

I swear to god I type in killall 3408 and then it says there is no process with that ID.  WHAT!?!?!?

---

### Post by ibuclaw on 2010-02-14
> **so0ky said:**
> Here is more information that I thought was interesting.

I do the top command, and I see the process hlds_amd at the very top, taking most resources as it should.  I want to end this occurrence, as this is a game server.  I want to run a game server with other commands, but I don't want two game servers with one I am not using.  Hence, why I am trying to end this occurrence.

top command brings a PID of 3408 .

I swear to god I type in killall 3408 and then it says there is no process with that ID.  WHAT!?!?!?

```
kill -9 `pidof jobid`
```
Does that work for you?


How do you start the server? Did you run it yourself, or is it a service?

Regards
Iain

---

### Post by Muzer on 2010-02-14
kill is used for PIDs, killall for executable names.

To pring a process into the foreground that you have backgrounded with &, you can type fg

Finally, if a process won't die, you can stick -KILL after the kill or killall, this will force it to die instead of asking it (relatively) nicely.

---

### Post by so0ky on 2010-02-14
Thank you for your quick responses.

Unfortunately, it doesn't, but this is because I am so unfamiliar with this application, let alone Linux.  This is how I ran the CS server, I ran it with this command based on an article online....

./amd_run -game cstike +autoupdate  and that was it.  I need to figure out how to end the server, because when I kill processes the processes just come back up.  Unfortunately, I am completely new to this stuff.  It is very frustrating.

This is what I want to run when I get the chance....

./hlds_run -game cstrike +ip ipaddresshere +port porthere +autoupdate +maxplayers 10 +map de_dust2 &

I hope this helps.

The kill -KILL PID still has another process eventually restart about 10 seconds later.  I'm thinking about just doing a restart of the server.  Can I restart the server through a SSH session?  Also, what is a good command to restart, NOT shutdown?

---

