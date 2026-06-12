---
title: "Can't connect to the Internet"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-02-28
First off, I'm brand new to Linux, and this is my 1st attempt of use today. I just downloaded the Live CD today and loaded it up.  I tried using Firefox, but it appears that I have no Internet Connection. I'm wired via Ethernet to my DSL (2wire) modem.  I right clicked on the Networking Icon, and "enable networking" was already checked.  I unchecked it, and then rechecked it, and it shows Connection Established.  You are connected to Auto eth0.  This is as far as I've gotten.  I'd love to get on the internet and continue checking things out.  Also, any suggestions on how to set up my pop3 email? I've always used Outlook 2003 for my various addresses.  I just need to know the settings for Evolution, or if you can suggest another email manager similar to what outlook does.  Thanks in advance.

---

### Post by dorkdork777 on 2009-02-28
Whoa, slow down. Before you start talking about email, are you properly connected to the Internet on Ubuntu right now, or are you not? Open Firefox on Ubuntu and load a web page to find out.

---

### Post by js@lloyd on 2009-02-28
No, I'm not connected.  I opened firefox and tried to load a webpage, but it's not working.

---

### Post by Roofdaddy on 2009-02-28
Try opening a CLI (DOS) and give something a ping .

EX/ C: ping ip addy,or whateverhere.com     enter

This will give ppl more info on the problem. If you get a responce back it's Firefox .

---

### Post by ShutterAce on 2009-02-28
js,

open a terminal and type ifconfig. You should get output similar to that below. Paste the output here and we'll see if you've even got an ip address from your DSl modem.

```
eth0      Link encap:Ethernet  HWaddr 00:0b:db:84:da:4f  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe84:da4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71687 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:76519694 (72.9 MB)  TX bytes:13071168 (12.4 MB)
          Base address:0xdf40 Memory:feae0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14883 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8469232 (8.0 MB)  TX bytes:8469232 (8.0 MB)

```

---

### Post by js@lloyd on 2009-02-28
Here's what I got.

ubuntu@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0d:87:28:db:33   
          inet addr:192.168.16.2  Bcast:192.168.16.255  Mask:255.255.255.0 
          inet6 addr: fe80::20d:87ff:fe28:db33/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:19686 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1535 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:1266566 (1.2 MB)  TX bytes:295250 (295.2 KB) 
          Interrupt:19 Base address:0xe000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:446 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:446 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:28356 (28.3 KB)  TX bytes:28356 (28.3 KB) 
 
pan0      Link encap:Ethernet  HWaddr c2:6f:12:6d:85:f6   
          inet6 addr: fe80::c06f:12ff:fe6d:85f6/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)

---

### Post by albinootje on 2009-02-28
> **js@lloyd said:**
>  ubuntu@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0d:87:28:db:33   
          inet addr:192.168.16.2  Bcast:192.168.16.255  Mask:255.255.255.0 


Thanks. 
Please post also the output of this :
```

route -n
cat /etc/resolv.conf
ping -c4 194.109.21.51

```

---

### Post by js@lloyd on 2009-02-28
Sorry, i'm really new to this.  what is the command that you need me to type in?

---

### Post by ShutterAce on 2009-02-28
Well, so much for the easy road.:P

You could have one of many issues. It's possible that the DSL modem has dropped it's internet connection or is not passing along DNS resolution. Try pinging 4.2.2.2 from a terminal. If you get a response you have an internet connection. That means you most likely don't have any DNS servers set.

I'm no expert, just passing along my experiences.

---

### Post by albinootje on 2009-02-28
> **js@lloyd said:**
> Sorry, i'm really new to this.  what is the command that you need me to type in?

Those were three different commands :
```

route -n <enter>
cat /etc/resolv.conf <enter>
ping -c4 194.109.21.51 <enter>

```

The first one should show whether the default gateway is set or not, and if so, which one it is.
The second command should show your DNS-servers in use, if any.
The third one ping a public ip-address on the internet.

---

### Post by ShutterAce on 2009-02-28
Just cut and paste albinootje's code into a terminal.

> **js@lloyd said:**
> Sorry, i'm really new to this.  what is the command that you need me to type in?

---

### Post by js@lloyd on 2009-02-28
Sorry for the delay.  Here are the results.

ubuntu@ubuntu:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.16.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
0.0.0.0         192.168.16.1    0.0.0.0         UG    0      0        0 eth0 
ubuntu@ubuntu:~$ cat /etc/reslov.conf 
cat: /etc/reslov.conf: No such file or directory 
ubuntu@ubuntu:~$ ping -c4 194.109.21.51 
PING 194.109.21.51 (194.109.21.51) 56(84) bytes of data. 
 
--- 194.109.21.51 ping statistics --- 
4 packets transmitted, 0 received, 100% packet loss, time 3013ms 
 
ubuntu@ubuntu:~$

---

### Post by albinootje on 2009-02-28
> **js@lloyd said:**
> Sorry for the delay.  Here are the results.

ubuntu@ubuntu:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.16.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
0.0.0.0         192.168.16.1    0.0.0.0         UG    0      0        0 eth0 
ubuntu@ubuntu:~$ cat /etc/reslov.conf 
cat: /etc/reslov.conf: No such file or directory 
ubuntu@ubuntu:~$ ping -c4 194.109.21.51 
PING 194.109.21.51 (194.109.21.51) 56(84) bytes of data. 
 
--- 194.109.21.51 ping statistics --- 
4 packets transmitted, 0 received, 100% packet loss, time 3013ms 
 
ubuntu@ubuntu:~$

Thanks for the output.

You made a small typo (should be resolv) :
```

cat /etc/resolv.conf 

```
You do get an ip-address, and the default gateway seems to be fine too.
Can you try the following in a terminal, and see whether that gives you something, or just errors ? :
```

mtr ping.xs4all.nl

```

---

### Post by js@lloyd on 2009-02-28
here you go. i corrected my original mistake.
To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 
 
ubuntu@ubuntu:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.16.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
0.0.0.0         192.168.16.1    0.0.0.0         UG    0      0        0 eth0 
ubuntu@ubuntu:~$ cat /etc/resolv.conf 
# Generated by NetworkManager 
nameserver 192.168.16.1 
ubuntu@ubuntu:~$ ping -c4 194.109.21.51  
PING 194.109.21.51 (194.109.21.51) 56(84) bytes of data. 
 
--- 194.109.21.51 ping statistics --- 
4 packets transmitted, 0 received, 100% packet loss, time 2999ms 
 
ubuntu@ubuntu:~$ mtr ping.xs4all.nl 
Name or service not known: No such file or directory 
ubuntu@ubuntu:~$

---

### Post by albinootje on 2009-02-28
> **js@lloyd said:**
> 
ubuntu@ubuntu:~$ mtr ping.xs4all.nl 
Name or service not known: No such file or directory 


Thanks, can you ping the gateway ?
```

ping -c4 192.168.16.1

```
And can you please post the output (screenshot) from the following from your MS-Windows machine ? 
```

ipconfig /all

```

---

### Post by js@lloyd on 2009-02-28
sorry, can't figure out how to cut and paste, or instert a jpg...it's attached.

results from ping

To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 
 
ubuntu@ubuntu:~$ ping -c4 192.168.16.1 
PING 192.168.16.1 (192.168.16.1) 56(84) bytes of data. 
 
--- 192.168.16.1 ping statistics --- 
4 packets transmitted, 0 received, 100% packet loss, time 3012ms 
 
ubuntu@ubuntu:~$

---

### Post by ShutterAce on 2009-03-01
Is that Windows output from a different machine or did you just reboot into Windows on the same box? The reason I ask is that the IP is the same as the Linux ifconfig result you posted. Two machines with the same IP address on the same network won't work.

---

### Post by js@lloyd on 2009-03-01
that is the same machine....rebooted it.

---

### Post by ShutterAce on 2009-03-01
And Windows works fine I expect?

Hmmmmm....:confused:

If Windows works and Linux doesn't you might try setting up a static IP in Ubuntu through Network Manager and make it something other than 192.168.16.2

192.168.16.3. would be fine

Maybe the DSL Modem is confused, although I don't know why it would be.

---

