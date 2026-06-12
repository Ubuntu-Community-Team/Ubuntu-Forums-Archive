---
title: "Problem with ports"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by dmaxel on 2010-11-13
I'm trying to start a temporary "server" using Urban Terror, and when someone tries to connect to me, it doesn't work. This is over LAN, so the only problem would be my own firewall. Now I install gufw and tried to create a rule. However that didn't work and I just turned off the firewall using gufw. After that, it still didn't work. So now I'm lost...what am I doing wrong?

Running Maverick.

---

### Post by trucker33377 on 2010-11-13
this is just a guess but I have a PC setup that i connect too from another PC on the same line or behind the same router. what I did was goto dyndns.com for a free account for me it was an issue of loopback.
hope this helps

---

### Post by dmaxel on 2010-11-13
I'm not worried about people coming in from the outside. It's just that not even people in the same LAN network can get in, and that's the problem. So router firewalls have nothing to do with this, and I know this because when a Windows machine hosts a session, I can connect to it fine.

---

### Post by CharlesA on 2010-11-13
Are you running a firewall or some sort?

Post the output of this please:

```
 sudo iptables -L
```

```
netstat -ln
```

---

### Post by dmaxel on 2010-11-13
Well, like I said, I installed gufw, and after playing around with it for a while I just unchecked "Enable", so I would presume that the firewall is off.

Either way, here is the output of "sudo iptables -L"
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination
```and of netstat -ln
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:17500           0.0.0.0:*               LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:54763           0.0.0.0:*                          
udp        0      0 0.0.0.0:65519           0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:17500           0.0.0.0:*                          
udp6       0      0 :::5353                 :::*                               
udp6       0      0 :::65519                :::*                               
udp6       0      0 :::58465                :::*                               
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     8711     /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     6193     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     8273     /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     12439    /tmp/orbit-dmaxel/linc-6fa-0-6cc5f109ac8a4
unix  2      [ ACC ]     STREAM     LISTENING     8718     @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     8023     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     8423     @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     12446    /tmp/keyring-AdEPL7/ssh
unix  2      [ ACC ]     STREAM     LISTENING     12465    /tmp/orbit-dmaxel/linc-6f5-0-1660df86b5f18
unix  2      [ ACC ]     STREAM     LISTENING     13498    /tmp/orbit-dmaxel/linc-743-0-57f220ffaea88
unix  2      [ ACC ]     STREAM     LISTENING     12852    /tmp/orbit-dmaxel/linc-72a-0-3d22d362dacd
unix  2      [ ACC ]     STREAM     LISTENING     13352    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     13355    /home/dmaxel/.pulse/bc1942feed18498a3db150df00000007-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     13415    /tmp/orbit-dmaxel/linc-741-0-5cb81a1584a9a
unix  2      [ ACC ]     STREAM     LISTENING     13449    /tmp/orbit-dmaxel/linc-752-0-21d3aca91728
unix  2      [ ACC ]     STREAM     LISTENING     8424     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     150146   /tmp/aptdaemon-Fr7jUC/debconf.socket
unix  2      [ ACC ]     STREAM     LISTENING     11869    /tmp/ssh-jWSsXb1737/agent.1737
unix  2      [ ACC ]     STREAM     LISTENING     11909    /tmp/.ICE-unix/1737
unix  2      [ ACC ]     STREAM     LISTENING     11950    /tmp/orbit-dmaxel/linc-6f2-0-50c6c61d5f2aa
unix  2      [ ACC ]     STREAM     LISTENING     12222    /tmp/orbit-dmaxel/linc-6c9-0-7d29c5d268a0b
unix  2      [ ACC ]     STREAM     LISTENING     12426    /tmp/keyring-AdEPL7/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     13472    /tmp/orbit-dmaxel/linc-748-0-535924a39c467
unix  2      [ ACC ]     STREAM     LISTENING     16814    /tmp/orbit-dmaxel/linc-963-0-78c5b62cda107
unix  2      [ ACC ]     STREAM     LISTENING     15349    /home/dmaxel/.dropbox/command_socket
unix  2      [ ACC ]     STREAM     LISTENING     15398    /home/dmaxel/.dropbox/iface_socket
unix  2      [ ACC ]     STREAM     LISTENING     152081   /tmp/orbit-dmaxel/linc-588d-0-3a9746683c61d
unix  2      [ ACC ]     STREAM     LISTENING     156313   /tmp/orbit-dmaxel/linc-5a96-0-30d6de5911ddd
unix  2      [ ACC ]     STREAM     LISTENING     157383   /tmp/orbit-dmaxel/linc-5b69-0-6e45c3e862189
unix  2      [ ACC ]     STREAM     LISTENING     11618    /tmp/keyring-AdEPL7/control
unix  2      [ ACC ]     STREAM     LISTENING     13881    /tmp/orbit-dmaxel/linc-767-0-502ff3b3da050
unix  2      [ ACC ]     STREAM     LISTENING     14528    /tmp/orbit-dmaxel/linc-708-0-d41aefc6872a
unix  2      [ ACC ]     STREAM     LISTENING     14559    /tmp/orbit-dmaxel/linc-79f-0-42e14fbc9324b
unix  2      [ ACC ]     STREAM     LISTENING     14563    /tmp/orbit-dmaxel/linc-79e-0-3318d00393432
unix  2      [ ACC ]     STREAM     LISTENING     14567    /tmp/orbit-dmaxel/linc-799-0-5994541198fbc
unix  2      [ ACC ]     STREAM     LISTENING     14573    /tmp/orbit-dmaxel/linc-79d-0-27aec138991cf
unix  2      [ ACC ]     STREAM     LISTENING     9286     @/tmp/gdm-greeter-jYCJSJCJ
unix  2      [ ACC ]     STREAM     LISTENING     14579    /tmp/orbit-dmaxel/linc-797-0-6c0fa86199423
unix  2      [ ACC ]     STREAM     LISTENING     14594    /tmp/orbit-dmaxel/linc-79a-0-25f8be119cec8
unix  2      [ ACC ]     STREAM     LISTENING     8128     /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     14896    /tmp/orbit-dmaxel/linc-7d6-0-53dae1dec8ed9
unix  2      [ ACC ]     STREAM     LISTENING     8648     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     14997    /tmp/orbit-dmaxel/linc-7a7-0-11a00f4888a82
unix  2      [ ACC ]     STREAM     LISTENING     15070    /tmp/orbit-dmaxel/linc-798-0-2e412598c0a2c
unix  2      [ ACC ]     STREAM     LISTENING     15158    /tmp/orbit-dmaxel/linc-747-0-6b7fce6bf0a62
unix  2      [ ACC ]     STREAM     LISTENING     15184    /tmp/orbit-dmaxel/linc-72e-0-4286a1692013d
unix  2      [ ACC ]     STREAM     LISTENING     15315    /tmp/orbit-dmaxel/linc-840-0-4cf9c876dbde7
unix  2      [ ACC ]     STREAM     LISTENING     15420    /tmp/orbit-dmaxel/linc-854-0-da7587b44b17
unix  2      [ ACC ]     STREAM     LISTENING     15997    /tmp/orbit-dmaxel/linc-8d5-0-640789028e5be
unix  2      [ ACC ]     STREAM     LISTENING     147101   /tmp/orbit-dmaxel/linc-55d4-0-12dcdd36d2545
unix  2      [ ACC ]     STREAM     LISTENING     9436     @/tmp/gdm-session-kRTJYUTC
unix  2      [ ACC ]     STREAM     LISTENING     29267    /tmp/orbit-dmaxel/linc-ffe-0-1082c340f1069
unix  2      [ ACC ]     STREAM     LISTENING     11882    @/tmp/dbus-WvozRfV6xz
unix  2      [ ACC ]     STREAM     LISTENING     11908    @/tmp/.ICE-unix/1737
```At the time these commands were issues, Urban Terror is running, but isn't running a server (just sitting at the main menu).

---

### Post by CharlesA on 2010-11-13
Try running this and then launching the server.

```
sudo iptables -F
```

---

### Post by dmaxel on 2010-11-20
Still no luck. I'm also using Network Tools from the Administrator menu to check what ports are even detected, and all I get are about 3-4 random ports that it says are open. None of them are remotely close to what UrbanTerror uses. Also tried to reset my config using gufw, which disables it, but it's still not going through. If anyone wants to see screenshots (cuz this is weird), I'll gladly post them.

---

### Post by CharlesA on 2010-11-20
Are you running it in Wine by chance? I saw a thread earlier about problems with Wine and ports or some such thing.

---

### Post by uRock on 2010-11-20
Now that I have checked out some more angles. Everything below the "Active UNIX domain sockets (only servers)" line has nothing to do with your NIC.

---

### Post by uRock on 2010-11-20
```
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     5838     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     35057    /tmp/orbit-rabbit/linc-e3e-0-7d72f95611c43
unix  2      [ ACC ]     STREAM     LISTENING     9212     /tmp/.esd-1000/socket
```
Notice that it says Inode instead of port.

---

### Post by dmaxel on 2010-11-20
No sir, not using Wine, but the Linux version of UrbanTerror.

I don't have any other computers that I can test the connect with that already have UT installed, so I'm in the process of installing UT on another system in the hopes that I can conduct a lot more tests.

@uRock: is there anything in what you said that can help me? :D

---

### Post by uRock on 2010-11-20
Nevermind. I reread the thread as I thought your were looking to block ports, not unblock them.

Sorry.

---

### Post by CharlesA on 2010-11-20
> **dmaxel said:**
> No sir, not using Wine, but the Linux version of UrbanTerror.

I don't have any other computers that I can test the connect with that already have UT installed, so I'm in the process of installing UT on another system in the hopes that I can conduct a lot more tests.

@uRock: is there anything in what you said that can help me? :D

That's what's puzzling, if the server is actively listening for connections, it would show up in netstat.

Have you asked over here: [http://forums.urbanterror.info/forum/15-linux-support/](http://forums.urbanterror.info/forum/15-linux-support/)

---

### Post by holiday on 2010-11-20
Do you mean that people on your LAN can't connect, or are you talking about outsiders? 

If you're talking about connections from the internet, you have to tell your router to forward requests to your LAN address.

---

### Post by uRock on 2010-11-20
nmap does a better job at showing what ports are actually listening.

You will be looking for this part of the output to see exactly what ports are listening. While netstat tells you what services are listening. Even though a service is listening, they are listening to other local processes and not data from the network interface.

```
rabbit@rabbit-desktop:~$ nmap 187.168.1.0/24

Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-20 19:51 PST
Interesting ports on 187.168.1.10:
Not shown: 996 closed ports
[COLOR=Red]PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
631/tcp open  ipp[/COLOR]

Interesting ports on 187.168.1.17:
Not shown: 999 closed ports
[COLOR=Red]PORT   STATE SERVICE
22/tcp open  ssh[/COLOR]

Interesting ports on 187.168.1.1:
Not shown: 998 closed ports
[COLOR=Red]PORT   STATE SERVICE
53/tcp open  domain
80/tcp open  http[/COLOR]

Nmap done: 256 IP addresses (3 hosts up) scanned in 29.72 seconds

```

---

### Post by CharlesA on 2010-11-20
> **holiday said:**
> Do you mean that people on your LAN can't connect, or are you talking about outsiders? 

If you're talking about connections from the internet, you have to tell your router to forward requests to your LAN address.

Could have sworn that they mentioned LAN games, but I could be mistaken.

EDIT: Yep they said the machines were on the same LAN in the OP.

> **uRock said:**
> nmap does a better job at showing what ports are actually listening.

Good point. I normally just use netstat or lsof to see which ports are listening on an external interface but I know what to look for [noparse](*:port).[/noparse]

nmap would work well.

---

### Post by dmaxel on 2010-11-20
Hehehe, well this is funny. I guess my firewall was working correctly after all. For some super strange reason, my server was listening on port 58197 instead of the default 27960. Don't know why, but when I saw in gufw that UT was listening on that port, I had to try it out, and it worked (when connecting to 58197). Now to see how I can get it back to default....thanks a lot guys haha. I have to keep on remembering that some problems come with easy solutions. :P

And yes, UT is supposed to work with LAN, which it now does. :)

EDIT: Actually, it keeps looking for new ports to listen on, so it's randomizing every time. Darn. Either way, I think all the problems that I can solve in this forum are solved. Thanks again for your help. :D

---

