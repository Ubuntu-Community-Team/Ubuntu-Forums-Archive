---
title: "Network gone after user change"
date: 2005-05-20
forum: Networking &amp; Wireless
---

### Post by Disorder2 on 2005-05-20
This one drives me insane, hope someboy can help:

I have warty installed at a friends' computer.
The internet connection works through a DSL router connected via ethernet.
And it works fine - unless you log out and log in back as a different user.
Then the connection is gone.

Ifconfig shows nothing unusual (I cannot post it right now becasue I'm not sitting on that machine for obvious reasons)
/etc/init.d/network stop | start does not help.

The only trace I have is:
When I do a fresh restart and everything works, the output of route -n is
10.0.0.0         0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         10.0.0.138     0.0.0.0         UG    0      0        0 eth0

However, after user change it's
10.0.0.0         0.0.0.0         255.255.255.0   U     0      0        0 eth0

and there it hangs.

Any idea anybody?
Any more you have to know?

---

### Post by nad on 2005-05-20
You have to edit that users network profile to include the default gateway.

---

### Post by Disorder2 on 2005-05-21
[QUOTE=nad]You have to edit that users network profile to include the default gateway.[/QUOTE]

Thanks, I'll try.  :) 
Is this a speciality of warty?
Because on my home machine running kubuntu-hoary I did not have to do anything...

---

### Post by nad on 2005-05-21
My warty installation does not have this problem. Whether it is a network or operating system issue, you may wish to research.

My advice is based on the information you posted.

---

### Post by Disorder2 on 2005-05-26
Well,
I solved the problem with the big hammer - that is, I upgraded that computer to Hoary and now everything's fine.

Thanks for helping!

---

