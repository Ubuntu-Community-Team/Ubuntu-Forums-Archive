---
title: "Ubuntu 6.06-server: Serial communication with a PLC"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by hollowed on 2006-07-21
I make my first steps now in the Linux-world. I have set up an ftp-server and it works (yeah). But now I come to my second task:
I have to transmit and receive data to and from a PLC. This PLC has a RS232-Communication-Port, so that's easy (I know from other applications that it works and how it works).

My problem is the setup or configuration of the serial port of my server. I tried a lot (minicom, setserial, /dev/MAKEDEV, ...) but I can't read or print with my ttyS0.

My ttyS* are working, aren't they?
$ ls -l /dev/ttyS0
crw-rw---- 1 root dialout 4, 64 2006-07-21 20:15 /dev/ttyS0
$ ls -l /dev/ttyS1
crw-rw---- 1 root dialout 4, 64 2006-07-21 20:15 /dev/ttyS1
$ ls -l /dev/ttyS2
crw-rw---- 1 root dialout 4, 64 2006-07-21 20:15 /dev/ttyS2
$ ls -l /dev/ttyS3
crw-rw---- 1 root dialout 4, 64 2006-07-21 20:15 /dev/ttyS3

What could be my next trials?
I have no ideas any more.

---

### Post by hollowed on 2006-07-22
> I have no ideas any more.

I had one more idea:
To change the pins of my cable...

Now it is like this:

Server:      PLC:
Tx   <-->    Tx
Rx   <-->    Rx
Gnd  <-->    Gnd        

I don't know why, but now it works! :D

---

