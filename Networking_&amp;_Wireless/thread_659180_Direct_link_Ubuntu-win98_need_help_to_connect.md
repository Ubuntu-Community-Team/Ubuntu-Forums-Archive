---
title: "Direct link Ubuntu-win98: need help to connect"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by fedleo on 2008-01-05
Not sure if it's the right forum, but I need to try anyway.

I need to connect two computers trough a direct link using a null modem cable on RS-232.
One is a Ubuntu/Debian box (as a server), another one is a win98 machine (as a client). Need to do this kind of connection because the win98 computer act as a CNC controller for a laser cut machine an is NOT possible to install a lan card without an incredible expensive upgrade. After a heavy google session I found were possible to use Pppd to connect trough serial port (ttys0 I think) and probably next I'll can use Rsync to synchronize a folder on the machines with the files I need. Now I need to know how to do a stable connection, better if automatically. I've tried but with no results using the command:

pppd 192.168.3.1:192.168.3.2

but the prompt did not return a single word and I'm sure the computer is not listening because win98 can't connect. 
At the end, I need:
-some help with the correct configuration (baud rate, flow control and so on)on both machines;
-a simple test to know if the com ports are working, using statserial the direct link seem to work;
-a BIG help for a good bash script that will let me connect and sync every 5 minutes...

Thanks for your attention.

EffE

---

