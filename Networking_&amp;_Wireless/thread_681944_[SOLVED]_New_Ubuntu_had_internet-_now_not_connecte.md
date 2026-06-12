---
title: "[SOLVED] New Ubuntu had internet- now not connected"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by vixmusic01 on 2008-01-29
Hello,
I am a fairly adept Win/Mac user new to Ubuntu.

I have Gutsy gibbon and I am totally willing to reinstall everything as I just got this machine working and have no data.

As an experienced user I wanted to install all apps and have a functioning platform before use.

The wired internet was working well and I used Synaptic to install some listed music packages.

After the process was over I continued using the internet and then suddenly it went out.

I reset my modem and router, but still no signal.

exploring the help, I ping'd ubuntu com all five tries but could not get any action on the IP address numbers. Firefox and Synaptic do not connect. 

Maybe unrelated, but I tried to save the terminal if config text to OO and it would not save giving me the error mssg that no document exists. This is also with save as ...

I tried to repair with the Ubuntu disk and I got an error when it got to the internet part.

Please instruct. Thanks so much.
Vixmusic01

---

### Post by an.echte.trilingue on 2008-01-29
Let us see the output of ifconfig -a, please.

How are you connected?  I suppose that you have a standard router that issues you a ip with dhcp, and connects with cat v, etc?

Edit, I meant:```
sudo ifconfig -a
```

Edit, if you are having trouble saving with OO, you can

```
sudo ifconfig -a > myinfo.txt
```
This will route the output to a file called myinfo.txt

---

### Post by vixmusic01 on 2008-02-17
I am running cable internet into a Microsoft router. The ethernet cable is plugged in and the system worked previously.


victoria@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:07:E9:86:B7:34  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10663 (10.4 KB)  TX bytes:6945 (6.7 KB)

I am also having trouble saving from Open Office. I don't know if this is related.

Victoria

---

### Post by vixmusic01 on 2008-02-18
After playing around with it for a couple of weeks -- I wiped the drive and reinstalled. 

I am posting from the computer now.

Praise to the god of external hard drives -- I no longer loose data.

Thanks for the help.

I will be careful in future about installing programs with Synaptic. There do seem to be a lot of version differences and something I installed broke my internet.

I am so happy it is working now!


vixmusic01 :)
.

---

