---
title: "Not recognising my router"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Omegastick on 2010-01-17
Hello, I'm Omegastick

I've recently installed Ubuntu using Wubi and it looks really cool. I have one problem, though, I can't connect to the internet. I spent a while trying to figure out why and have come to the conclusion that Ubuntu doesn't recognise my router. I have plugged in the recieving end of a Belkin 54g router (I'm using a different transmitting end now) and windows does fine with it. Ubuntu, however, simply refuses to acknoledge it's existence. Any ideas as to why this is happening and how I can fix it?

---

### Post by halitech on 2010-01-17
Normally the OS (windows or linux) doesn't recognize a router as an attached piece of hardware. How are you hooked up to the router? Do you have the model number? Is it a wireless connection or a wired connection?

What do you mean by a different transmitting end?

---

### Post by Omegastick on 2010-01-17
IIRC (which I probably don't) there are two parts to a router, a part that sends a signal and a part that recieves it. Any recieving part should recieve any signal. There is probably a name for each one, I just can't seem to remember.

I am using a USB to connect the router to my computer, it is a wireless connection and 802UIG-1 is the model number.

Thank you for any help.

---

### Post by halitech on 2010-01-17
I'm going to varify what you are saying just to make sure because the first part of your statement
> I am using a USB to connect the router to my computer
makes it sound like you are running a usb cable from the computer to the router, but this
> it is a wireless connection
tells me you are using wireless. So, to clarify, you are using a wireless USB adapter to connect to the router. Am I correct?

---

### Post by Omegastick on 2010-01-17
Yes, I am using a wireless USB adapter to ocnnect to the router.

---

### Post by halitech on 2010-01-17
ok, that makes more sense now. Can you open a terminal and post the output of
```
lsusb
```
and
```
sudo ifconfig
```

---

### Post by Omegastick on 2010-01-17
Okay, from the lsub command I got lots of stuff and I don't have much paper to write on so I copied down everything that I thought was relevant:
> Bus 002 Device 003: ID 1668:1050 Actiontec Electronics, Inc. [hex] 802.11g Wireless Mini AdapterThat's my "Wireless Mini Adapter"

For the sudo ifconfig command I got too much to write down, and I couldn't figure out what you wanted, so could you tell me what bits you need and I can copy them down.

---

### Post by halitech on 2010-01-17
Not much info about that card online but it looks like it uses the Prism2 driver. There is info here
[http://ubuntuforums.org/showthread.php?t=634977&highlight=1668%3A1050+Actiontec+Electronics](http://ubuntuforums.org/showthread.php?t=634977&highlight=1668%3A1050+Actiontec+Electronics)

If you have a thumb drive, we can create text files to transfer from the laptop to a machine with an internet connection. Use this
```
sudo ifconfig >> ~/Desktop/ifconf.txt
```

---

### Post by Omegastick on 2010-01-17
Okay, this is what I got:
```
eth0      Link encap:Ethernet  HWaddr 00:1d:09:8d:7c:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


```

I seem to have the same problem as some of the people in that thread you posted.

---

### Post by halitech on 2010-01-17
are you able to connect using a wired connection for a bit so we can get the proper files downloaded?

---

### Post by Omegastick on 2010-01-17
Okay, I'll try to find my modem, I have a phone socket-thingy nearby and I'll plug it into that.

---

### Post by halitech on 2010-01-17
Do you not have a way of plugging the laptop into the router with a wired connection? would be much faster then using a dialup connection

---

### Post by Omegastick on 2010-01-17
I'm using a desktop computer, so it'll be really hard to plug it into the router. Also I've found that I can't plug in a modem anymore without having to set up another account with my ISP. Could I put the software on a USB or burn it to a cd and use it from that?

If that's impossibe I could temporarily move the router into my room, but it is used for work as well so it would be a hassle.

---

### Post by halitech on 2010-01-17
would be easier with a direct connection but you can do it with a usb stick. I know you need the driver file for windows, ndiswrapper, ndiswrapper-common but I'm not sure what other dependencies you may need. You could try installing them from the cd, not sure if they are there or not.

---

