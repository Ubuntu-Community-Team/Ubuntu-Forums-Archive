---
title: "The System Network services are not compatible with this version"
date: 2016-05-13
forum: Networking &amp; Wireless
---

### Post by gordon33 on 2016-05-13
Hello all

Using HP 15 - r031ds wireless lap top with Ubuntu 14.04 firefox.

Unable to get on line. 

I was on line earlier and shut the lab top down and 20 minutes later tried to get on line and got the message "Server not found".


 Went to System Settings - Networks - and a box popped up with the message "The System Network services are not compatible with this version"

I am still a beginner when it comes to fixing problems.  Please let me know what checks to make to be helpful.

Gordon33

---

### Post by gordon33 on 2016-05-13
Hello All

Do you think updating to Ubuntu 15.01 would eliminate the proble with the network?

Gordon

---

### Post by filipposanfilippo on 2016-05-13
I am having the same problem. This happened after installing the latest updates. Any suggestions on how to fix this?

---

### Post by Bashing-om on 2016-05-13
et al ; Yeah .

Updates broke network-manager , fix in the latest network-manager.
see:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634)
[http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841](http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841)

One can manually install the updated package:
[https://launchpad.net/ubuntu/+source/network-manager/0.9.8.8-0ubuntu7.3](https://launchpad.net/ubuntu/+source/network-manager/0.9.8.8-0ubuntu7.3)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by filipposanfilippo on 2016-05-14
I have manually install the updated package

---

### Post by gordon33 on 2016-05-14
Hello Bashing-om,and filipposanfilippo

Thank you for the reply.  I will look the links later and see what happens.  Others are having the same problem. Below I a link to some one who soled the problem.


[http://ubuntuforums.org/showthread.php?t=2324429](http://ubuntuforums.org/showthread.php?t=2324429)


Godon33

---

### Post by jkeenan on 2016-05-14
I also got bit by this bug today.  I followed the instructions here:  [http://ubuntuforums.org/showthread.php?t=2324504](http://ubuntuforums.org/showthread.php?t=2324504)

And the problem was swiftly resolved (as evidenced by my ability to send this post!).

---

### Post by JvdB01 on 2016-05-15
I solved it by following the second answer in this link: [http://askubuntu.com/questions/55805/how-do-i-re-install-network-manager-without-an-internet-connection](http://askubuntu.com/questions/55805/how-do-i-re-install-network-manager-without-an-internet-connection)
and for ease of reading (seeing as how many who have this problem are probably on mobile) i'll paste it here:
> 
 The following describes how to establish a wireless network connection via command line utilities.

  I think this is a better option because it gives you the useful ability to interface with relevant command line utilities. 
  
[LIST=1]
[*]Use ifconfig -a to identify your wireless card. From hence forward, I will assume it's eth1. 
[*]sudo ifconfig eth1 up 
[*]iwlist eth1 scan to find available networks. iwlist eth1 scan | less if it's a long list. 
[*]sudo iwconfig eth1 essid [network] [key [pass]] Also, read man iwconfig to figure out how the wifi password is entered. You might also need to configure the channel and stuff.
[LIST=1]
[*]If you use WPA, wpa_supplicant will be necessary. [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136) 
[/LIST]
  
[*]sudo dhclient eth1 
[/LIST]
     


---

### Post by gordon33 on 2016-05-17
Hello all

Following Bashing- om's direction: I can go to a web site make copy, download it to a computer and then _never been successful_ at using the terminal to do the install.  So I went to Synaptic Package Manager and clicked on the 3 libnl3, libnl-3-200, libn-genl-3-200, and libn-route-3-200.  did a restart and still no network.

So I started on JvdB01's directions below is the result of the first terminal command.  JvdB01 said the command would identify the wireless card.  JvdB01 said "I will assume it's eth1."  Did not see eth1 so I am unsure of my next move.  Below is the results of  ifconfig -a  .  Oh should I substitute eth0 for eth1 in JvdB01's following commands?


ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 38:63:bb:c8:f0:86  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:65536  Metric:1 
          RX packets:193 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:193 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:27268 (27.2 KB)  TX bytes:27268 (27.2 KB) 

wlan0     Link encap:Ethernet  HWaddr ec:0e:c4:6f:42:33  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by gordon33 on 2016-05-17
Hello All

Decided to continue by replacing JvdB01's commands with eth0 instead of eth1.  Got to JvdB01's step 3 and got toe message will not scan.  So what can I do now? 

gordon@gordon-HP-15-Notebook-PC:~$ sudo ifconfig eth0 up 
[sudo] password for gordon: 
gordon@gordon-HP-15-Notebook-PC:~$ iwlist eth0 scan 
eth0      Interface doesn't support scanning. 

gordon@gordon-HP-15-Notebook-PC:~$

---

### Post by gordon33 on 2016-05-23
hello all

Still no luck The libnl-3-200=3.2.21-1 libnl-genl-3-200=3.2.21-1 \ libnl-route-3-200=3.2.21-1 packages have to be selected for AMD64 or i386 what is that all about and how do I find out what to use?  Each of the steps i have read about are new to me.  i will need to learn how to do each step.

Please help.

Gordon33

---

