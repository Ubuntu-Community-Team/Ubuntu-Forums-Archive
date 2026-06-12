---
title: "Some assistance please - Shell commands - programming"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by I_am_trainee on 2011-03-08
Hi,

I am using the text editor getedit in ubuntu 10.10 to type up sample shell commands for execution in the terminal through the use of the bash command, i.e. bash [replace with filename].

Can anyone help out re the points below?

[*]I am trying to list the command name and user for the busiest process (i.e. the one using the greatest percentage of CPU time). Please suggest code using the ps command if possible.

[*]I need separate code which will kills any process with a utialisation of more than 70%. I also need to display a message on screen saying which process was killed.
Thanks

---

### Post by turtle153 on 2011-03-08
Use the command **top** to get the most CPU hungry processes. But I don't think it's a good idea just to kill them off. Imagine if you were saving some work and it just happens to go over 70%.

---

### Post by I_am_trainee on 2011-03-08
Thanks but could you could back with sample code and I will test them out. I am using ubuntu via a usb boot up for test reasons only so please no need to worry. 

Suitable code to deal with both points would be great. Thanks

> **turtle153 said:**
> Use the command **top** to get the most CPU hungry processes. But I don't think it's a good idea just to kill them off. Imagine if you were saving some work and it just happens to go over 70%.

---

### Post by blind2314 on 2011-03-08
You should really think about the previous response..
 
Since top gives a snapshot of the current processes, sorted by usage (refreshing at a set interval), it wouldn't be very effective in giving you the "current" busiest process. Again, this heavily depends on what you want to define as current, but using top for scripting isn't the best solution.

---

### Post by I_am_trainee on 2011-03-08
Please just some sample code which meets my needs. Thats all I need.

Thanks

> **I_am_trainee said:**
> Thanks but could you could back with sample  code and I will test them out. I am using ubuntu via a usb boot up for  test reasons only so please no need to worry. 
 
 Suitable code to deal with both points would be great. Thanks
 

> **turtle153 said:**
> Use the command **top** to get the most CPU  hungry processes. But I don't think it's a good idea just to kill them  off. Imagine if you were saving some work and it just happens to go over  70%.
> **blind2314 said:**
> You should really think about the previous response..
 
Since top gives a snapshot of the current processes, sorted by usage (refreshing at a set interval), it wouldn't be very effective in giving you the "current" busiest process. Again, this heavily depends on what you want to define as current, but using top for scripting isn't the best solution.

---

### Post by howefield on 2011-03-08
Perhaps you could have a stab at your homework on your own.

This isn't the place to have it done for you.

---

