---
title: "Remote SYSLOG server not working !"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by rdsmf on 2007-05-14
I have followed the steps to setup a syslog server by stopping the syslogd service and then editing the /etc/init.d/sysklogd file like so ...

# Options for start/restart the daemons
#   For remote UDP logging use SYSLOGD="-r"
#
#SYSLOGD="-u syslog"
SYSLOGD="-r"

After starting the syslogd service I do not see the syslog port (UDP 514) when I do a netstat -an. Can someone tell me what I am doing wrong ?

---

### Post by rdsmf on 2007-05-14
OK I found a fix for my remote syslog problem (not sure if this is a temp or perm fix yet). Thanks to the user "STRIDER" <thanks again for the tip strider !> he posted his fix for the same problem I was encountering with setting up a remote syslog server. My problem was after I edited the /etc/init.d/sysklogd file to enable remote syslog to be dumped from a cisco router, I would not see the proper udp port (514) opened up doing a netstat. I could tcpdump and see the router send the syslog info but nothing would get logged. Anyway long story short after I found Strider's fix I was able to see the syslog udp port open. I will post the link to Strider's fix for anyone who is interested. Here ya go .....

[http://ubuntuforums.org/showthread.php?t=366267&highlight=sysklogd](http://ubuntuforums.org/showthread.php?t=366267&highlight=sysklogd)

If you can not link to it I am including it also in this reply ........



[B][I]Hi all,

I recently installed Ubuntu 6.10 Server. I wanted to enable syslog remote capabilities so the system can log syslog messages. I edited /etc/syslog.conf file and changed the following:

Code:

SYSLOGD="-u syslog"
to
SYSLOGD="-r -u syslog"

I restarted the syslog daemon but was not able to capture any remote syslog info. tcpdump reports that udp/514 was no reachable. After troubleshooting the issue I found that the "SYSLOGD" options were not being passed to the start-stop-daemon (located in /etc/init.d/sysklogd script).

It turned out that the /etc/init.d/sysklogd file has the following line:
Code:

test ! -r /etc/default/syslogd || . /etc/default/syslogd

runs /etc/default/syslogd which re-writes the SYSLOGD options to "" (none).

I resolved this by changed the variable in /etc/init.d/syslogd from SYSLOGD to OPTIONS and replace the variable reference within the file.

Not sure if this is by design or not. I did not find any docs stating to modify /etc/default/syslogd instead of /etc/init.d/syslogd. At any rate, this resolved my problem I was having.

I hope this is helpful to anyone having a similar issue. If anyone know why this is the way it is, please let me know.

-Mike[/I][/B]

---

### Post by sblanzio on 2007-10-05
Hey I can't get it to work even doing what is explained here!

how can i do!?

I see NO 514 listening port!

thanks!

---

### Post by sblanzio on 2007-10-05
i solved commenting the first line that begins with
"test ! ....."

can't understand why this is the only way to get my syslog listening....

---

