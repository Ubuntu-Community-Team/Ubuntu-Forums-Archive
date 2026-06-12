---
title: "Messages during boot"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by awp2513_ on 2010-12-30
Hi,

During boot and shutdown (or reboot), I see a lot of messages on the screen, many with "[OK]" at the end (especially during boot). I was wondering what actually generates the messages in Ubuntu. Everything I've read points to programs/services that are not installed on my system (/etc/syslog.conf doesn't exist, I cannot find klogd or syslogd).

I'm guessing it's not just one thing, so maybe my question is too broad, but any information or resources would be appreciated. I'm using Ubuntu 10.04 Netbook Remix.

Thanks!

---

### Post by blind2314 on 2010-12-30
Those are messages that are written by the kernel as it goes through and executes the start/stop scripts in /etc/rc.X. If the startup script has any specific messages, those can be written as well, but the generic "Blah blah shutting down...OK" is the kernel saying that exited successfully.
 
On another note, does "ps -ef | grep syslog" not return any syslog processes?

---

### Post by QLee on 2010-12-30
[QUOTE=awp2513_]... I was wondering what actually generates the messages in Ubuntu. ...(/etc/syslog.conf doesn't exist, I cannot find klogd or syslogd).

I'm guessing it's not just one thing, so maybe my question is too broad, but any information or resources would be appreciated. I'm using Ubuntu 10.04 Netbook Remix....[/QUOTE]

A while back it was changed to rsyslog.

You can read the logs with a GUI, System-->Administration-->Log File Viewer, if you don't know how to find them in /var/log/ with the command line.

However, to be frank with you, this is not really a beginner topic and a beginner should not muck with the rsyslog configuration. If you choose to continue, I suggest you read the manual page.

---

### Post by Paul E on 2011-12-22
Came up with a workaround for this issue for a kiosk I was deploying. Edited /etc/rc.local and added "clear" (without quotes) right above exit 0.

---

### Post by /bin/sh on 2011-12-22
By the way, these messages are written to /var/log/boot.log.

---

### Post by grahammechanical on 2011-12-22
These kinds of messages are there when the system loads and when it shuts down but are hidden by splash and log in screens. When the Shut down screen is itself shut down the final few messages appear.

The kernel defaults to a quiet boot mode but that instruction can be removed. This is useful if we have problems loading the kernel. We can find the point in the loading process where it fell over.

I think that this shows the Unix roots of Linux. These kernel messages are echoed or printed to the screen as an aid to debugging should something go wrong with the start or shut down process.

I used to work in a high street store and years ago it had a Unix system. I had responsibility for closing the store. Before I could go home I had to wait until the computer had worked its way through printing to the screen these types of messages. If it stalled at any point I had to telephone an engineer and he would talk us through re-setting the system.

Regards.

---

### Post by CharlesA on 2011-12-22
> **/bin/sh said:**
> By the way, these messages are written to /var/log/boot.log.
Beat me to it. :)

> **Paul E said:**
> Came up with a workaround for this issue for a kiosk I was deploying. Edited /etc/rc.local and added "clear" (without quotes) right above exit 0.

Did that on Debian, but it was a clunky solution.

@OP: I think most of it's been covered, by default the "background stuff" is hidden behind a slash screen.

---

