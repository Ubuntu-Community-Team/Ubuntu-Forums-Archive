---
title: "possible bug in ppp"
date: 2013-11-19
forum: Networking &amp; Wireless
---

### Post by bugbear6502 on 2013-11-19
I have encountered a slightly odd phenomona in pppd, which I use
to connect to my workplace office from my home laptop.

[http://linux.die.net/man/8/pppd](http://linux.die.net/man/8/pppd)

In Ubuntu 11.04, I had a script which launched a named pppd session.
I ran this script inside a spawned lxterminal.

Hitting ctrl-c in the terminal window neatly stopped
everything, including correct unwinding of the ppp connection,
and reversion to "normal" internet. Lovely.

When I got a new home computer, I installed Ubuntu 13.10,
and set everything up, installed my preferred sound editing software,
set my desktop, etc.

My connection script worked OK, but ctrl-c no longer killed
pppd inside the terminal?!

Some trial and error testing simplified the failure.

If I create a root shell
```
sudo bash
```
and run the following as a trivial shell script:
```
pppd call somewhere
```
ctrl-c does NOT stop the ppp.

If (in the same root shell) I simply run
```
pppd call somewhere
``` directly from the command line, ctrl-c DOES stop the ppp.

Checking with a friend at work, who has Ubuntu 12.10 installed, he sees
the same bad behaviour as I do.

So it looks like ppp changed it's ctrl-c behaviour somewhere between 11.04 and 12.10.

Is this a bug, or deliberate code change?

 BugBear

---

