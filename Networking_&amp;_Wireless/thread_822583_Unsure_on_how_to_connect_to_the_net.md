---
title: "Unsure on how to connect to the net"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by Jue on 2008-06-08
Hi, I am new on Ubuntu OS. I dont know how to connect to the internet via wireless.

In the terminal i have done "lspci" and it came up with a load of information but i'm not sure what im looking for and what i need to do to connect.

Any help is apprecitated.

---

### Post by Keith Hedger on 2008-06-08
I dont have a wireless connection so I hope someone will take over but a good start is System->Administration->Network

---

### Post by Jue on 2008-06-08
I did that, opened up that and there was only 2 options but when i look on the Ubuntu website it shows there are suppose to be 3. I hope someone helps me soon or I have wasted time installing it. :(:(

---

### Post by rlzyoner on 2008-06-08
Are you sure that your wireless adaptor is enabled...
Try running 
sudo ifconfig wlan0 up (replace wlan0 with the name of your wireless adaptor)

Then run ifconfig and advise of the output

---

### Post by Jue on 2008-06-08
"Are you sure that your wireless adaptor is enabled...
Try running 
sudo ifconfig wlan0 up (replace wlan0 with the name of your wireless adaptor)

Then run ifconfig and advise of the output"

I don't know the name of the adapter. Im pretty useless at this sort of thing.

---

### Post by rlzyoner on 2008-06-08
Ok well in that case, just run ifconfig and post the output

---

### Post by Keith Hedger on 2008-06-08
I dont have a wireless card and I only get two options so It looks like your card aint being seen thats about it for me im afraid:(

---

### Post by Jue on 2008-06-08
My wireless is built in and it only shows 2 options aswell.

And ipconfig won't work. It says "command not found"

---

### Post by Keith Hedger on 2008-06-08
ifconfig NOT ipconfig

---

### Post by Jue on 2008-06-08
eth0      Link encap:Ethernet HWaddr 00:ld:60:f5:b7:30
          UP BROADCAST MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)    TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Netric:1
          RX packets:1072 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1072 errors:0 dropped:0 overruns:0 carrier:0
          collision:0 txqueuelen:0
          RX bytes:54320 (53.0 KB) TX bytes:54320 (53.0 KB)

That is what showed up.

---

### Post by Keith Hedger on 2008-06-08
eth0 is your wired network card l0 is the loopback network so your wireless card is not being seen try searching in the forums for your specific card maybe someone else has had the same problem

---

