---
title: "networking"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by chelseachelsea on 2010-02-20
I have just installed Ubuntu 9.10 on an older Dell laptop (latitude) that previously had Ubuntu 7.10 installed.

Neither version of Ubuntu on this computer were able to connect to a LAN network or directly to a modem (DSL or dialup).

When the LAN cable is plugged in, there is no light at the connection (the little green light) on the laptop.

Does that suggest the network card is not working?  Is it possible there's something going on with Ubuntu (ie. not detecting the card)?

Wireless card works fine with 7.10 and 9.10.

C

---

### Post by Easy Limits on 2010-02-20
Did you right click on the network icon up in the right hand corner of your screen by the date/time and click Enable Networking?

---

### Post by chelseachelsea on 2010-02-20
yes - and details were completed for a dsl connection

---

### Post by lyall on 2010-02-20
have you checked to see if the networking is turned off in the BIOS?

good luck and have fun learning

---

### Post by Ozymandias_117 on 2010-02-20
Can you post the output of the commands "lshw" and "ifconfig"? 

(Open a terminal, run "ifconfig > ifconfig.txt", it will output the results into a text file that you can then highlight and paste into the forums. It will be saved in the directory that you're working in, the command pwd will tell you what that is)

---

### Post by chelseachelsea on 2010-02-21
this make any sense to you?

&#65279;lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

