---
title: "bluetooth applet 0.25"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by t0mk1fal on 2010-04-11
bluetooth applet 0.25, **post #1**

Using ubuntu 8.04 linux 2.6.24
Have 7 BT dongles, three Bluetooth 2.1, four Bluetooth 2.0.
Testing on Pentium 2 (233 Mhz), Pentium 4 (2.4 Ghz) and Samsung cellphone.
BT dongle brand names: iogear(3), asus(1), power data (3).
I need a ***trouble shooting / diagnostic*** **_[FONT=Arial]strategy[/FONT]_**.
BT software is Bluetooth Applet 0.25
I have not been able to produce consistent results.
Have tried for a reset effect  by clearing directories in /var/lib/bluetooth/.
Swapping dongles between machines hasn't worked.
I need a step by step debugging method.
Your help will be appreciated. **Thanks.**  t0mk1fal


bluetooth applet 0.25, **post #2**

In the months since I have been hacking at my bluetooth problems,
I noticed a recurring message during start up and shut down.
It filled the screen.

hci_scodata_packet: hci0 SCO packet for unknown connection handle 92

or rather,

hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
.
.
... you get the idea.


A few weeks ago, I googled the message and found that it related to bluetooth.

Gentoo Bug 249523 - broken usb bluetooth adapter needs to be ...
24 Dec 2008 ... Dec 2 12:08:27 Raptor hci_scodata_packet: hci0 SCO packet for unknown connection handle 92 Dec 2 12:08:27 Raptor hci_scodata_packet: hci0 ...
bugs.gentoo.org/show_bug.cgi?id=249523 - Cached - Similar

The above report uses the phrase "spams syslog due to a buggy SCO support".

dmesg showed that syslog was indeed being spammed,
nothing but
"hci_scodata_packet: hci0 SCO packet for unknown connection handle 92."

I also tried the bluetooth software again.
I was able to browse /Public and send files, P2 to P4 and vice versa.
I had few windows open on the P2 which possibly made the difference, less cycles out of 233Mh getting in the way while the bluetooth timeout clock was running.

As explained in prior post,
I had 2 dongles on P2 (one asus and one powerdata) and 4 dongles on P4 (three iogear and one powerdata).
I removed one dongle from each, basically a **** bid to stir the pot,
and to my surpise, the P4 stopped spamming.
The remaining 3 dongles in the P4 are all iogear BT 2.1.
A step forward, but still mostly tea leaves that I can't read.

As of this writing, I consider the P4 bluetooth stable enough to use as is.
The P2 needs to have the spamming to syslog addressed.
I have tried
sudo /usr/sbin/logrotate /etc/logrotate.conf -f
on P4 and ls tells me syslog has been reset ...
-rw-r----- 1 syslog adm         0 2010-05-23 12:42 /var/log/kern.log
-rw-r----- 1 syslog adm 405291501 2010-05-23 12:15 /var/log/kern.log.0
If logrotate works the same on the P2 I'll have a work around I can live with.
**In theory.**
t0mk1fal

---

