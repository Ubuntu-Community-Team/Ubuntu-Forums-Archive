---
title: "What PID/program is this?"
date: 2019-05-30
forum: Networking &amp; Wireless
---

### Post by linux-user-0987 on 2019-05-30
I am running the netstat command to check if there are any unwanted  connections and there is a program which keeps coming up for a few  seconds that I don't know about.

Here is a description :        udp        0      0 0.0.0.0:44848           0.0.0.0:*  20730/host               

This shows up many times but only for a short time and the other PIDs  that it has shown up with are 512, 32404, 32353, 31509, 31123. The port  of the local address is different also every time. 
Sometimes it shows up when I connect to the internet after disconnecting and sometimes it does not.

Can you provide some information on how to detect unwanted access using netstat or some other program?

I ran a virus scan and I found nothing.

---

### Post by TheFu on 2019-06-01
If you showed the command used and all options, we wouldn't have to guess.
I'd guess it is the **host** program.  The manpage:
```
NAME
       host - DNS lookup utility
...
DESCRIPTION
       host is a simple utility for performing DNS lookups. It is normally
       used to convert names to IP addresses and vice versa. When no arguments
       or options are given, host prints a short summary of its command line
       arguments and options.
```

There are many ways to determine the PID.  **ps** is probably the most normal.

---

