---
title: "[B]eth0 and eth1 do not exist?[/B]"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by GrapeSoda on 2008-05-29
I've been unable to get onto my local network with the wired connection, which is strange because last week I didn't have a single issue.  I tested out the physical layer (switched cables, had a friend use the network drop) and everything says that the problem is with my machine.

I went into the Network Tools to see if I could run a couple of tests, and I received a message telling me that eth0 and eth1 do not exist...shouldn't one of these by default be my ethernet port?  And shouldn't one be my wireless (which is weird, because I have no issue with my wireless connection)?  Additionally, there is a solid orange light by my ethernet card when I'm plugged in, and I'm fairly certain it's supposed to be green and blinking.

Any suggestions would be greatly appreciated (I'm running Ubuntu 8.04 by the way).  Thanks!****

---

### Post by jflowers on 2008-06-03
I am having the exact same problem.  I just posted a similar thread today.  Nonetheless, do you see anything when you type:

$lspci

You should see a list of your pci slots and I at least see one that said ethernet.

I hope you have found a solution

Update: I went to add a new network card, and after installing the new one, both cards began to work. Maybe shutting down and unplugging the computer helped reset the network card?  Good luck again.

---

