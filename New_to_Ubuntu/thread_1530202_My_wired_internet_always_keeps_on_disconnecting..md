---
title: "My wired internet always keeps on disconnecting."
date: 2010-07-13
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-07-13
HI!
I am using ubuntu 10.04 and have got a problem.
My wired internet keeps on diconnectin' very often. This does not used to happen before, it has recently started.

one more thing....internet seems to reconnect automatically after sometime and the it gets disconnected...this happen again and again...
I tried my wired internet over windows but everything goes fine over there.

Please tell me if anyone have understand my problem.

Thanks!

Amit

---

### Post by expatCM on 2010-07-13
You say that you have a wired connection.  Is this ADSL / Cable or what is your setup?  What is the make / model of your modem / router?

Have you discussed this with your ISP?

---

### Post by amityadav9314 on 2010-07-14
well, I have a broadband connection from a telephone company MTNL.
My internet connection works fine under windows so i didn't think to contact my ISP.
and if you want i can do that.
Any other information that you asked i don't know about that.

Please help me if you can!!

\thnaks!

---

### Post by yaaarrrgg on 2010-07-14
Are you dual booting the same machine with Linux and Windows?  IF so that would rule out a hardware issue.

Otherwise., if it's two different machines, I would suspect the wire, jack(s), or nic card is faulty.

---

### Post by amityadav9314 on 2010-07-15
I HAVE INSTALLED UBUNTU UNDER WINDOWS 7 AS AN APPLICATION(wubi)...

---

### Post by yaaarrrgg on 2010-07-15
Hmm, so Windows and Ubuntu are running on the same machine.  Windows Ethernet works, Ubuntu Ethernet is flakey.

It's still hard to rule out a hardware issue. I might test  plugging the machine into another network and testing Ubuntu again.  If possible, you can swap the nic card and wire too and test.  Hardware tolerances could be different, such that the Windows driver is more fault-resistant and ignores the specific problem.  After a while, though, if it's a hardware failure, it may affect both.

Also, how is the router configured?  I'm assuming a dynamic IP (DHCP)?   I might also try powering down all routers for 30 seconds, and possibly resetting them.  Otherwise, there could be an issue with the network configuration.  I wonder if you could delete the "Auto eth0" connection and set it back up.  And disable and restart networking.  (should be accessible under the nm-applet -> Edit Connections).

To troubleshoot the lowest driver level, you'll need to open a Terminal, and copy/paste the output of the following commands in the forum:

lspci

lshw

lsmod


IMO there's basically three levels this may be breaking at (in the order of most likely):  hardware, network configuration, and driver.

---

### Post by amityadav9314 on 2010-07-15
okay lemme do it.

---

### Post by yaaarrrgg on 2010-07-15
I should add, IMO if it's a static IP, the order of likelihood is:

network configuration problem,
hardware problem,
driver problem

---

### Post by gr4nf on 2010-07-15
My guess would be your application has intermittent hardware interfacing issues (possibly caused by inadequate system resources?). Still, you should post your /etc/network/interfaces file from the ubuntu installation.

---

