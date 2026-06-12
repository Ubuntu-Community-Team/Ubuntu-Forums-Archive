---
title: "kern.log and syslog flooded with wlan3 messages"
date: 2014-02-26
forum: Networking &amp; Wireless
---

### Post by two4two on 2014-02-26
These messages keep flooding my logs:


Feb 26 10:48:17 Dad-Stubuntu kernel: [ 4626.009111] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47097 DPT=32412 LEN=29 
Feb 26 10:48:17 Dad-Stubuntu kernel: [ 4626.009217] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34583 DPT=32414 LEN=29 
Feb 26 10:48:21 Dad-Stubuntu kernel: [ 4630.060231] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=201 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=181 
Feb 26 10:48:22 Dad-Stubuntu kernel: [ 4631.009095] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47097 DPT=32412 LEN=29 
Feb 26 10:48:22 Dad-Stubuntu kernel: [ 4631.009205] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34583 DPT=32414 LEN=29 
Feb 26 10:48:27 Dad-Stubuntu kernel: [ 4636.009079] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47097 DPT=32412 LEN=29 
Feb 26 10:48:27 Dad-Stubuntu kernel: [ 4636.009188] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34583 DPT=32414 LEN=29 
Feb 26 10:48:32 Dad-Stubuntu kernel: [ 4641.009086] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47097 DPT=32412 LEN=29 
Feb 26 10:48:32 Dad-Stubuntu kernel: [ 4641.009196] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34583 DPT=32414 LEN=29 
Feb 26 10:48:37 Dad-Stubuntu kernel: [ 4646.009117] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47097 DPT=32412 LEN=29 
Feb 26 10:48:37 Dad-Stubuntu kernel: [ 4646.009228] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34583 DPT=32414 LEN=29 
Feb 26 10:48:37 Dad-Stubuntu kernel: [ 4646.070367] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=199 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=179 
Feb 26 10:48:39 Dad-Stubuntu kernel: [ 4648.005864] Inbound IN=wlan3 OUT= MAC=ff:ff:ff:ff:ff:ff:e0:c9:7a:88:e8:fe:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=255 ID=65003 PROTO=UDP SPT=68 DPT=67 LEN=308 
Feb 26 10:48:42 Dad-Stubuntu kernel: [ 4651.009092] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47097 DPT=32412 LEN=29 
Feb 26 10:48:42 Dad-Stubuntu kernel: [ 4651.009208] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34583 DPT=32414 LEN=29 
Feb 26 10:48:47 Dad-Stubuntu kernel: [ 4656.009090] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47097 DPT=32412 LEN=29 
Feb 26 10:48:47 Dad-Stubuntu kernel: [ 4656.009204] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34583 DPT=32414 LEN=29 
Feb 26 10:48:52 Dad-Stubuntu kernel: [ 4661.009090] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47097 DPT=32412 LEN=29 
Feb 26 10:48:52 Dad-Stubuntu kernel: [ 4661.009200] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34583 DPT=32414 LEN=29 
Feb 26 10:48:52 Dad-Stubuntu kernel: [ 4661.080234] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=201 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=181 
Feb 26 10:48:57 Dad-Stubuntu kernel: [ 4666.009108] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47097 DPT=32412 LEN=29 
Feb 26 10:48:57 Dad-Stubuntu kernel: [ 4666.009218] Inbound IN=wlan3 OUT= MAC= SRC=192.168.1.18 DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34583 DPT=32414 LEN=29 




192.168.1.18 is my current local IP (as in my router), and so 192.168.1.255 is my broadcast IP?  I don't know what the MAC=ff:ff:ff:ff:ff:ff:e0:c9:7a:88:e8:fe:08:00 refers to.  WLAN3 is my ASUS N13 wireless adapter.  The driver is the one from RealTek, since my kernel didn't have a driver for it I installed this one.  And in the process I disabled the power-save mode.  (I did the same thing in another Ubuntu instance and don't get this flood of messages there.)  Also, a while back, the 192.168.1.18 was the IP of my network printer.  But that has changed and now the printer is 192.168.1.3 and this computer has the 192.168.1.18 IP.  


All I want to do is learn what process and service, etc is responsible for spitting out these log messages and turn it off or turn off its logging.  Thank you for anyone who can help.  And if you need more info just specify how to provide it and I will.  Thank you.

Oh, BTW, the is 11.04 Ubuntu Studio.  I know it is not supported.  Still, maybe people with more knowledge than I have can help.  Thanks.

---

### Post by ian-weisser on 2014-02-26
Looks like iptables packet logs.
iptables is, among other things, your system's firewall.
It's part of the kernel, not a separate application.

Did you, at some point, set your firewall to log anything?

To explore which applications are sending/receiving those packets, one way is to use the 'netstat' command.
This example shows the applications using port 631: cupsd (PID 7635) and cups-browsed (PID 1063)
```
$ sudo netstat -tulpn | grep 631
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      7635/cupsd      
tcp6       0      0 ::1:631                 :::*                    LISTEN      7635/cupsd      
udp        0      0 0.0.0.0:631             0.0.0.0:*                           1063/cups-browsed
```

---

### Post by two4two on 2014-02-26
> **ian-weisser said:**
> Looks like iptables packet logs.
iptables is, among other things, your system's firewall.
It's part of the kernel, not a separate application.

Did you, at some point, set your firewall to log anything?

To explore which applications are sending/receiving those packets, one way is to use the 'netstat' command.
This example shows the applications using port 631: cupsd (PID 7635) and cups-browsed (PID 1063)
```
$ sudo netstat -tulpn | grep 631
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      7635/cupsd      
tcp6       0      0 ::1:631                 :::*                    LISTEN      7635/cupsd      
udp        0      0 0.0.0.0:631             0.0.0.0:*                           1063/cups-browsed
```

I sniffed the packets for a bit, and I did the netstat that you showed.  I found a lot of the activity is Plex Media Server broadcasting, and then all the DLNA devices on our home network answering back.  It accounts for quite a bit of the logging.  I don't mind the Plex network traffic, but I do mind the logging.  How do I make it so that the traffic is not logged.  I make sure the settings in Plex do not log anything, but I don't know how to stop/restart the server if that is required to make it so.  I suppose re-boot would do it, but would that actually stop the logging?




I have an app called Firestarter.  It is the frontend that I would use to turn on my firewall.  I don't think it is a service or task that is always running.  It is not in System Monitor.  But if I start Firestarter it shows up in system monitor.  So I don't think a firewall is what's generating the log messages.

Also, the network printers are ringing in as well.  A percentage of the inbound packets come from them.


Also, what is the process named nmbd?

---

### Post by ian-weisser on 2014-02-27
Log entries from applications look different, and often show up in  different logs. Also, your entries say they are from the kernel.
> Feb 26 10:48:47 Dad-Stubuntu **kernel**: [  4656.009090] Inbound IN=wlan3  OUT= MAC= SRC=192.168.1.18  DST=192.168.1.255 LEN=49 TOS=0x00 PREC=0x00  TTL=64 ID=0 DF PROTO=UDP  SPT=47097 DPT=32412 LEN=29

There are *always* a lot of packets from devices on your network. They  ping to ensure they are connected, they ping to advertise their service,  they ping when they get lonely.

Try the command ```
sudo iptables -L
```
This will list all your firewall rules in proper iptables language, without all the (unintended) obfuscation from Firestarter and other helpers.
Look for the word "log". If in doubt, post the entire output here.
iptables is part of the kernel. It runs 100% of the time that your system is turned on. It's not a separate application, and won't show up on System Monitor.
The log entries could be coming from a rsyslog rule, but that's less likely. Let's check the most-common-by-far source first.

---

### Post by chili555 on 2014-02-27
Just to add a bit more information to the mix, firewall logs are:> [497.708918] [**UFW BLOCK**] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:38:
<snip>

---

### Post by two4two on 2014-02-27
> **chili555 said:**
> Just to add a bit more information to the mix, firewall logs are:
[497.708918] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:38:

chili555, 
Hi,  I'm the user you helped with getting rid of the ASUS/Ubuntu driver for the N-13 on my Ubuuntu 12.06 and Linux Mint 13 instances.  I have two identicle of these Ubuntu 11.04 instances and on both of them I recently re-compiled/installed the N-13 RealTek driver to eliminate the power-save messages that were flooding the log.  On one of the instances: no more flooding.  On the instance I refer to in this post I got rid of the power-save messages, but then THESE messages started appearing.  When I first installed 11.04 way back when I used a D-Link DWA-160 USB adapter and it flooded the log with these very same messages.  It also had weak reception at half speed and would lose connection  frequently.  Those two problems is why I got rid of it and went with this ASUS instead.

So, in your sample firewall log message, you say "UFW BLOCK".  Is that literally what it will say, or are you substituting that phrase to denote some other actual text?


ian-weisser,
Once I get home from work I'll list that IPTABLES as you specify and post here.



Thanks guys!

---

### Post by two4two on 2014-02-28
> **ian-weisser said:**
> Log entries from applications look different, and often show up in  different logs. Also, your entries say they are from the kernel.


There are *always* a lot of packets from devices on your network. They  ping to ensure they are connected, they ping to advertise their service,  they ping when they get lonely.

Try the command ```
sudo iptables -L
```
This will list all your firewall rules in proper iptables language, without all the (unintended) obfuscation from Firestarter and other helpers.
Look for the word "log". If in doubt, post the entire output here.
iptables is part of the kernel. It runs 100% of the time that your system is turned on. It's not a separate application, and won't show up on System Monitor.
The log entries could be coming from a rsyslog rule, but that's less likely. Let's check the most-common-by-far source first.

Alrighty, here is the iptables.  Can anyone see how this relates to the gazillion log records that I sampled at the beginning of this thread?  Let's hope no one can use this to hack my computer!

dad@Dad-Stubuntu:~$ sudo iptables -L
[sudo] password for dad: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.1.1          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.18         192.168.1.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.1.18         192.168.1.1         udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
dad@Dad-Stubuntu:~$

---

### Post by ian-weisser on 2014-02-28
> **two4two said:**
> Alrighty, here is the iptables.  Can anyone see how this relates to the gazillion log records that I sampled at the beginning of this thread?

Yes.
Here (input chain):
> **two4two said:**
> 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

And here (forward chain):
> **two4two said:**
> 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

And here (output chain):
> **two4two said:**
> 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

And your LOG_FILTER chain...
And all over your LSI chain...
And all over your LSO chain...

You are repeatedly telling your system to log packets for various reasons.
Well, it's logging them for you.

Maybe you're using Firestarter, maybe you're using UFW, maybe something else. They are all just front-ends for iptables, and iptables does the real work.

---

### Post by two4two on 2014-02-28
Thank you ian-weisser.  So, how do I turn it all off?  I have another Ubuntu 11.04 partition which is a clone of this one.  In both of these partitions I recently re-compiled my wireless driver to get rid of the power-save mode.  Here in this partition I get all these messages but in the other partition I don't.  I don't know what's different between them though.  I'll try to compare them more.  So you say look at Firestarter?  I did use Firestarter in this partition lately but not in the other.  That's a place to start then.  But if you have some direct suggestion I'd love to hear it.

---

### Post by two4two on 2014-02-28
Holy ^#@* ian-weisser.  You are a genius.  I turned off the firewall using Firestarter and the messages stopped.  Now I'd like to re-start the firewall but I don't know where to set the preferences to do it.  Do you know?

---

### Post by ian-weisser on 2014-02-28
I'll need to pass the baton to another community member with Firestarter experience.
Unfortunately, I have zero experience with the application.

---

### Post by two4two on 2014-02-28
You did say Firestarter was merely a frontend and as such simply turns the firewall on or off.  I'm thinking it uses a command line to do it and probably the command line ends up turning on all that logging.  I'd like to find that command line and turn the firewall on or off by way of terminal.  Maybe UFW?  Anyone?

---

