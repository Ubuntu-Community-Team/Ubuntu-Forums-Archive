---
title: "xterm to tty?"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by gurt on 2009-06-30
I have a 4 port Serial card connected to some switch console ports.
I installed setserial
did a setserial -bg /dev/ttyS*

03:00.0 Serial controller: Oxford Semiconductor Ltd OX16PCI954 (Quad 16950 UART) function 0 (Uart) (prog-if 06)
    Subsystem: Siig Inc Device 2050
    Flags: medium devsel, IRQ 17
    I/O ports at bc00 [size=32]
    Memory at fe8ff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at b880 [size=32]
    Memory at fe8fe000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: serial

03:00.1 Bridge: Oxford Semiconductor Ltd OX16PCI954 (Quad 16950 UART) function 1 (Disabled)
    Subsystem: Siig Inc Device 0000
    Flags: medium devsel, IRQ 10
    I/O ports at b800 [size=32]
    Memory at fe8fd000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at b480 [size=32]
    Memory at fe8fc000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>


How do I xterm to these puppies?
Why is access denied?

bam@mingus:/dev$ sudo xterm /dev/ttyS0
[sudo] password for bam: 
No absolute path found for shell: /dev/ttyS0

Ta!

---

### Post by iponeverything on 2009-06-30
install minicom.

```
sudo apt-get install minicom

```

edit:

```
sudo nano /etc/minicom/minirc.dfl
```

---

### Post by gurt on 2009-06-30
Thanks -- that's working!

'nother question... since I have 4 ttys, how do I edit the minirc.dfl to reflect all of them?
[FONT=monospace]or maybe the question should be, is there a way to create 4 or so tty connections to different devices simultaneously?

Ta!
[/FONT]

---

### Post by gurt on 2009-06-30
Got it. I just need to create multiple config files -- one for each device and do..
minicom -o minicom.router1

Playing with launchers now.

---

