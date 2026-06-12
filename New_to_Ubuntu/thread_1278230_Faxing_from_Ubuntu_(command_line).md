---
title: "Faxing from Ubuntu (command line)"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by jsdegard on 2009-09-29
Hello,

I was trying to use efax 0.9 to send faxes from the command line in Ubuntu 8.04.  It failed, telling me that it couldn't open a serial port modem.  The problem is a device (modem) needed to be set to a variable DEV before the efax install.  I tried DEV=cual1 and DEV=tty as instructed but of course it did not work.  I don't have a modem connected to a serial port on the server or anywhere.  What I was hoping to do was use the IP of a printer that is set up to receive / send faxes as my device.  So I tried DEV=192.168.30.225, but this did not work either.  So finally my question is, can I use a remote device as a fax modem, and if so how can I set that up?  If not, can I set up a virtual modem of some sort?  Thanks all,

Jeremy

---

### Post by mamut0o1 on 2009-12-09
Hello; I don't think that will work since all you are doing is poiting at the Printer that has a modem but your linux server doesn't know how to "talk" to this device. I bought a Robotics External Modem for this reason and it worked out of the box.
Let me know if you get it to work.

good luck

---

