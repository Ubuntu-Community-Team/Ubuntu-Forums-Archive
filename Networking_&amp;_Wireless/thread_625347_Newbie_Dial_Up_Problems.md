---
title: "Newbie Dial Up Problems"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by billisamoron on 2007-11-27
I'm installing 7.10 on an old system with an ext USR modem.  System dials the modem and apparently connects to my ISP, but Network Monitor shows no connection and Firefox cannot find any servers.  What could be the problem?

var/log/messages shows a connection is being made and 0 bytes sent and a few bytes recieved.

Thanks for any suggestions.

Bill

---

### Post by billisamoron on 2007-11-28
Well, I got it to work with wvdial from a terminal as explained in "DialupModemHowto/SetUp Dialer" under "Alternative Way 1".


Here is a portion of the log, with x's to hopefully cover things that should not be broadcast:

WvDial Modem<*1>: CONNECT 48000/ARQ/V90/LAPM/V42BIS
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: Level 3 Comm xxxx.xxxx XXXXX
WvDial Modem<*1>: Username:/login:/Login:
WvDial<*1>: Looks like a login prompt.
WvDial<*1>: Sending: [email]xxx@xxx.com[/email]
WvDial Modem<*1>: [email]xxx@xxx.com[/email]
WvDial Modem<*1>: Password: 
WvDial<*1>: Looks like a password prompt.
WvDial<*1>: Sending: (password)
WvDial Modem<*1>:     Entering PPP Session.
WvDial Modem<*1>:     IP address is x.xxx.xxx.xxx
WvDial Modem<*1>:     MTU is 1524.
WvDial<*1>: Looks like a welcome message.
WvDial<Notice>: Starting PPP at xxx xxxxxxxx
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: --> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: --> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 5701
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: local  IP address 4.xxx.xxx.xxx
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: remote IP address xx.xxx.xx.xxx
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: primary   DNS address xxx.xx.xxx.xxx
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: secondary DNS address xxx.xx.xxx.xxx
WvDial<*1>: pppd: [10]&#65533;[06][08]&#65533;&#65533;[06][08]

Would anyone care to help me understand what some of this means?
Specifically, in the first line does the 48000 indicate the baud rate?
A little further down what does this mean:  MTU is 1524?
Finally, any comments on the warnings that PAP and CHAP might be flaky?

Thanks,
Bill

---

### Post by billisamoron on 2007-11-28
**Anyone know about Gnome-PPP?**

Installed Gnome-PPP and can now make a connection with it.  However, the notification window hangs at "Authenticating" and will not minimize to the panel.  Connection Log ends after displaying DNS addresses, but the connection allows Firefox to operate in normal fashion.

---

### Post by Bartender on 2007-11-28
bill -
duncan has reported that people have had problems with Gnome-PPP and 7.10
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

try his instructions for ppp-config.  I've found it to be the simplest, most reliable way to connect once you have a compatible modem.

After you've got the feel for pppconfig, try dinking with Gnome-PPP again.  There's some discussion of the PAP/CHAP flaky thing in that thread too.

---

