---
title: "Bluetooth?"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by JohnRory1971 on 2008-12-31
I'm not 100% sure that I have bluetooth on my Dell 1525 laptop.

How would I check? and how do I get it up and running?

---

### Post by igknighted on 2008-12-31
Mine appears to be connected via USB even though it is internal, so for me I ran the command 'lsusb -v | grep Bluetooth'.  If you get nothing there, try PCI via 'lspci | grep Bluetooth'.  If neither of these work, and the bluetooth icon is not in your system tray, I think it is a safe bet that you do not have a bluetooth adapter.

---

### Post by JohnRory1971 on 2008-12-31
Thanks.

Output as below:

john@laptop:~$ lsusb -v | grep Bluetooth
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
john@laptop:~$ lspci | grep Bluetooth

I guess I don't have an adapter. Thanks for your help

---

### Post by igknighted on 2008-12-31
> **JohnRory1971 said:**
> Thanks.

Output as below:

john@laptop:~$ lsusb -v | grep Bluetooth
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
john@laptop:~$ lspci | grep Bluetooth

I guess I don't have an adapter. Thanks for your help

Try it with sudo

---

### Post by JohnRory1971 on 2009-01-01
Hi I tried with sudo and got nothing so definitely no adapter

---

