---
title: "internet connection problem"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by hel on 2010-09-18
howdy frnz...,
i m posting for the first time so for please excuse me for any mistake.

i have a 64-bit dell inspiron i5 system, i m running ubuntu(9.04) and win7,
i m running internet through win7 and want to run net in ubuntu,
when i connect net in win7 then my dsl modem shows green led on( it means that the modem is been detected by os or the modem is connected to os)
problem is, that after creating a dsl connection in ubuntu, it shows-

DSL connection 1 : never

and apart from that when i run ubuntu my modem's green led doesn't glow....
although i used internet the same way on ubuntu(9.04) on my previous lenevo 32-bit laptop.
so please tell me how to configure my modem in my 64-bit system running ubuntu

thankyou!:)

---

### Post by jtarin on 2010-09-18
Give us some information on your modem. Make, model and manufacturer.

---

### Post by gotchanisa on 2010-09-18
Sorry to barge in... I'm having a similar problem. here are some details
Hi,

I tried a few steps ([http://ubuntuforums.org/showpost.php...stcount=12)and](http://ubuntuforums.org/showpost.php...stcount=12)and) it now connects for the first time, but the second page onwards it goes into an offline mode. I use a wired connection that is connected to a router. The other computers are windows and connect with no issues to the net. Initially I was able to ping any website but now I am not.
The ifconfig gives me the following

etho0 Link encap:Ethernet HWaddr 00:14:c5:47:6b
inet6 addr: fe80::214ff:fec5:476b/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:451 errors:2 dropped:0 overruns:0 frame:15
TX packets:404 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:324116 (324.1 KB) TX bytes:55282 (55.2KB)
Interrupt:16

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask.255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:648 errors:0 dropped:0 overruns:0 frame:0
TX packets:648 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:49648 (49.6 KB) TX bytes:49648 (49.6)

Whew....! That was some typing I had to do. Please bear with me, I'm new to Ubuntu (10.04). Help! 
I was able to install all the updates required. Just not able to browse now. I also get an error when I try to use the synaptic package manager. Some message about not being able to fetch some address.

---

### Post by jtarin on 2010-09-18
> **gotchanisa said:**
> Sorry to barge in... I'm having a similar problem. here are some details
Hi,


Start a separate post please it is too difficult trying to cross communicate with two separate problems.

---

### Post by hel on 2010-09-20
> **jtarin said:**
> Give us some information on your modem. Make, model and manufacturer.




hi jtarin, 
               i have a nokia siemens adsl c2110 modem
to check its image you can vist following link
 [http://www.calcutta.bsnl.co.in/dataoneinstall/mdm09.html](http://www.calcutta.bsnl.co.in/dataoneinstall/mdm09.html)
:)

---

### Post by jtarin on 2010-09-20
Are you connecting with Network Manager?

---

### Post by jtarin on 2010-09-20
Look in Synaptic package manager and see if you have a listing for pppoeconf?

---

### Post by perspectoff on 2010-09-20
> **gotchanisa said:**
> Sorry to barge in... I'm having a similar problem. here are some details
Hi,

I tried a few steps ([http://ubuntuforums.org/showpost.php...stcount=12)and](http://ubuntuforums.org/showpost.php...stcount=12)and) it now connects for the first time, but the second page onwards it goes into an offline mode. I use a wired connection that is connected to a router. The other computers are windows and connect with no issues to the net. Initially I was able to ping any website but now I am not.
The ifconfig gives me the following

etho0 Link encap:Ethernet HWaddr 00:14:c5:47:6b
inet6 addr: fe80::214ff:fec5:476b/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:451 errors:2 dropped:0 overruns:0 frame:15
TX packets:404 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:324116 (324.1 KB) TX bytes:55282 (55.2KB)
Interrupt:16

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask.255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:648 errors:0 dropped:0 overruns:0 frame:0
TX packets:648 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:49648 (49.6 KB) TX bytes:49648 (49.6)

Whew....! That was some typing I had to do. Please bear with me, I'm new to Ubuntu (10.04). Help! 
I was able to install all the updates required. Just not able to browse now. I also get an error when I try to use the synaptic package manager. Some message about not being able to fetch some address.

Yeah, that happens for me, too, every time my (dynamic) IP address changes. It started doing it in Karmic, and now in Lucid and Maverick. Never happened in previous versions.

It is fixed by restarting networking 

( sudo /etc/init.d/networking restart )

which I now do as a daily cron event. I have never been able to pinpoint the exact problem.

It happens whether I use Network Manager or not.

---

### Post by dineshs on 2010-09-22
hel,
Method-I
Configure modem in [COLOR="Blue"]PPPoE mode[/COLOR] following [this]("http://ernakulam.sancharnet.in/ernakulam/bbservice.html") link (under CPE /modem configuration)for an always ON internet connection
Method-II
Configure modem in[COLOR="Blue"] bridge mode[/COLOR] then connect /disconnect using Network manager following [this]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")
gotchanisa,
Can you run```
sudo dhclient eth0
```and see if *ifconfig -a* gives a valid IP?

---

### Post by hel on 2010-09-24
actually my problem is that my modem is detected in windows but not in ubuntu or backtrack...
so all that you fellas told me is concerned with net connection after your pc has detected modem,
but since my modem is not detected by ubuntu or bt4 therefore all that i tried went in vain...
frendz tell me how to make my system detect my modem...?
i am running dell inspirion intel i5 450, 
                            64 bit system


thankyou!

---

### Post by jtarin on 2010-09-24
I'm assuming from the link you gave your modem is USB? With modem connected, enter the command ```
lsusb 
```in a terminal and post here.

[USB modem setup]("http://www.kenneyjacob.com/2008/04/01/how-to-configure-bsnl-evdo-usb-broadband-in-linux/")

---

