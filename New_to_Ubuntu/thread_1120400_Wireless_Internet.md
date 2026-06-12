---
title: "Wireless Internet"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by rmf8066 on 2009-04-08
I just transfered my Dell inspiron 8200 laptop that my roommate (kevin36) changed to ubuntu. I know i have an old wireless card, but when i used windows i could connect to different servers at a good connection when on campus. Now since i transfered to ubuntu, all of my Internet connections are weak, including my own router. This is making it near impossible to do anything on the Internet without having to reload the page constantly. I was just wondering if there was anything i could download or something to strengthen my connections.

My card is a Lucent Technologies WaveLAN silver card

Any ideas?

Farah

---

### Post by tripolitan on 2009-04-09
This sounds like a driver issue but just out of curiosity, was the wireless card automatically detected? or did you download and install the driver? if so, how did you do it? and what driver did you use and what version of Ubuntu are you using?

Since your card is kind of working, here is a long shot but it worked for me on one system:

in terminal, type
sudo ifdown wlan0 (Assuming your wireless card is wlan0, you can check with ifconfig)
then type
sudo ifup wlan0
this restarts the wireless card, the last digit in wlan0 is a zero, not the letter "O"

if this works then it is a driver issue and you might have to download the latest WinXP driver for your card and use ndiswrapper to install it. (search these forums for wireless ndiswrapper)

good luck

---

### Post by superprash2003 on 2009-04-09
post output of ifconfig from the terminal

---

### Post by rmf8066 on 2009-04-09
I got this computer as a remade one from some guy my dad knew. i've had to redo the entire computer 2 times in the last 2 years because it starts running slow then not at all. Anytime i've rebooted it, the wireless card automatically is already detected 

i'm using ubuntu 9.4 the jaunty jackalope
my roommate is tryin to convert me to this because he says it works better then windows 

when i went to my terminal and typed in ifconfig to check and see if my wireless card is wlan0. it gave me this:
eth0    Link encap:Ethernet HWaddr 00:08:74:e4:3d:77
        UP BROADCAST MULTICAST MTU:1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
        Interrupt:11 Base address:0xac00

eth1    Link encap:Ethernet HWaddr 00:60:1d:1e:98:40
        inet addr:192.168.1.136 Bcast:192.168.1.255 Mask:255.255.255.0
        inet 6 addr: fe80::260:1dff:fe1e:9840/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        RX packets:7 errors:0 dropped:0 overruns:0 frame:0
        TX packets:28 errors:1 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:1430 (1.4 KB) TX bytes:6225 (6.2 KB)
        Interrupt:3 Base address:0xe100

lo      Link encap:Local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

and when i typed in output of ifconfig, it reads:
The program 'output' is currently not installed. you can install it by typing: sudo apt-get yagiuda
bash: output: command not found

so i typed sudo apt-get yagiuda:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following New packages will be installed:
  yagiuda
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded
Need to get 95.9kB of archives
After this operation, 356kB of additional disk space will be used.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe yagiuda 1.19-5
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/univeersse/y/yagiuda/yagiuda_1.19-5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/univeersse/y/yagiuda/yagiuda_1.19-5_i386.deb) Could not resolve 'us.aarchive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-geet updaate or try with --fix-missing?

I'm typing this reply off the tower we have in our apartment, but running the terminal on my laptop to figure out whats wrong

if that makes sense to anyone, please help me with what im supposed to do, because i am lost!

Farah

---

### Post by rmf8066 on 2009-04-09
this is what happened when i typed:

terminal: sudo ifdown wlan0
ifdown: interface wlan0 not configured

so i typed: 

terminal: sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0

dont get this either

Farah

---

