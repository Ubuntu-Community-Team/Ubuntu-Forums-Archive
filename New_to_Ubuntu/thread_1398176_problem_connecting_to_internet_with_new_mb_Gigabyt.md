---
title: "problem connecting to internet with new mb Gigabyte G31M-ES2L"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by wstay on 2010-02-04
After changing to a new motherboard, model Gigabyte S-series G31M-ES2L, I find that I cannot establish a connection to the internet. Using this new motherboard on the same computer and restarting to other operating system, it can establish connection to the internet. Is there any way I can solve this problem?

---

### Post by Tholley on 2010-02-04
It is possible you may have to do a fresh install of your Ubuntu, if you installed a new motherboard, then certain things may not longer be recognized. If you are able to backup all you data, then re-install, it should give you a nice clean start again.

---

### Post by superprash2003 on 2010-02-04
just to make sure ubuntu has recognized your card post output of** ifconfig **from the terminal

---

### Post by wstay on 2010-02-06
I post ifconfig onto the terminal and I get:
wstay@wstay-desktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:14:78:04:47:08  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:78ff:fe04:4708/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:807 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:835521 (835.5 KB)  TX bytes:161146 (161.1 KB)
          Interrupt:20 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25760 (25.7 KB)  TX bytes:25760 (25.7 KB)

wstay@wstay-desktop:~$ 

The eth1 is my pci ethernet card.
I wonder why it cannot detect the RJ-45 Lan Port on the rear of the motherboard?

---

### Post by superprash2003 on 2010-02-09
well , you might need drivers for that , look under system->admin->hardware drivers , if nothing is listed post output of **lshw -C network** from the terminal

---

### Post by caravel on 2010-02-09
That board uses the RTL8111C chip.

Post output of:

lspci | grep -i eth
lsmod | grep r81*

---

### Post by wstay on 2010-03-05
I have another problem with the pci ethernet.
Why after configuring the subnet mast to 255.255.255.0 and pressing ok and going back to see the subnet mast again, it becomes 24?

---

### Post by JKyleOKC on 2010-03-05
> **wstay said:**
> I have another problem with the pci ethernet.
Why after configuring the subnet mast to 255.255.255.0 and pressing ok and going back to see the subnet mast again, it becomes 24?There are two different ways of describing the netmask value. One (the original method) was to use the "dotted quad" format of 255.255.255.0. However as the net grew in popularity, the original method got a bit cumbersome. For example, the netmask my ISP has me use is 255.255.255.248 because the actual mask value is 11111111 11111111 11111111 11111000. The reason for this is so they can crowd more users into the spectrum. Thus a simpler method for describing the mask was developed: counting the number of "1" bits from the left. That gives you a value of "/24" and me a value of "/29" (and the "/" character is the signal that the new method is in use).

When different programs use different methods, though, it can be confusing -- as you've discovered!

---

### Post by wstay on 2010-03-10
I installed ubuntu-9.10 and there is no problem dictating and connecting to the internet on the Gigabyte G31M-ES2L motherboard.
My problem now with ubuntu-9.10 is that it sometimes behaves strangely.
My screen can go blank at times when I am just using it (normal use) and at one time when I try to install wine using synaptic. A few times, the screen on the monitor can go on blinking when it reaches a point just before I can login after I restart the computer. Also at times the usb mouse freezes. Is this an indication of a virus or a hardware or software problem?
I am using ubuntu-9.10 on a Pentium 2.6 Ghz on the Gigabyte G31M-ES2L motherboard with 1 Gb ram.

---

