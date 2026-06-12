---
title: "Serial Port ttyS0 and Cisco 831 router"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by metallica1973 on 2008-07-10
I am am using Ubuntu/Hardy and have it installed on several machines in my office. The problem that I am having is trying to use minicom and connecting to a Cisco 831 router via my serial port (ttyS0). I know that on all of my machines that I have the serial port enabled in the BIOS and I can see them is DMESG,

[PHP][    4.797770] console [tty0] enabled
[    7.008943] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    7.010429] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A  [/PHP]

I have configured minicom with 

[PHP]•9600 baud

•8 data bits

•No parity

•1 stop bit

•No flow control  [/PHP]
 
I can only connect to my aux port on one machine. Why cant I connect using the other machines? How does one tell Ubuntu to start using the serial port on boot?

---

