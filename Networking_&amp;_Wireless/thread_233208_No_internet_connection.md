---
title: "No internet connection"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by Stephen_A on 2006-08-09
I’ve failed to get a box with Ubuntu 6.06 online. Here are my internet ISP details: 

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Broadcom NetXtreme Gigabit Ethernet
        Physical Address. . . . . . . . . : 00-16-41-12-BE-7F
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        Autoconfiguration IP Address. . . : 169.254.163.2
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

PPP adapter NETVIGATOR BROADBAND:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 219.79.107.20
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 219.79.107.20
        DNS Servers . . . . . . . . . . . : 218.102.32.208
                                            205.252.144.126
        NetBIOS over Tcpip. . . . . . . . : Disabled

Now, I’m obviously missing something really fundamental so please excuse my ignorance. First I’ve gone through the steps as detailed at: 
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

That is I typed ‘sudo pppoeconfig’ and went through all the steps. Then it says ‘To start your ADSL connection type: 

   sudo pon dsl-provider

I did this and something seemed to be happening. If I right click on the network icon (top right hand corner of the screen) to get connection properties the connection flashes between ‘idle’ and ‘receiving.’ However any attempt to use Fireforx gives the ‘Server not found’ error message. 

The command: 

  plog

Gives the following. 

Aug  9 13:37:40 localhost pppd[17034]: PPP session is 4221
Aug  9 13:37:40 localhost pppd[17034]: Using interface ppp0
Aug  9 13:37:40 localhost pppd[17034]: Connect: ppp0 <--> eth0
Aug  9 13:37:40 localhost pppd[17034]: PAP authentication failed
Aug  9 13:37:40 localhost pppd[17034]: Connection terminated.
Aug  9 13:38:10 localhost pppd[17034]: PPP session is 4248
Aug  9 13:38:10 localhost pppd[17034]: Using interface ppp0
Aug  9 13:38:10 localhost pppd[17034]: Connect: ppp0 <--> eth0
Aug  9 13:38:11 localhost pppd[17034]: PAP authentication failed
Aug  9 13:38:11 localhost pppd[17034]: Connection terminated.


The command 

   sudo ifconfig

Gives the following: 
stephen@stephen-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:56:E9:F0:C3
          inet6 addr: fe80::20d:56ff:fee9:f0c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:367620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:502143181 (478.8 MiB)  TX bytes:363232 (354.7 KiB)
          Interrupt:7

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:39352 (38.4 KiB)  TX bytes:39352 (38.4 KiB)

So then I tried pinging it with ‘ping –c5 10.0.0.2’

And I got ‘Network is unreachable.’ 

Here is the state of affairs on System>Administration>Networks. 
The ethernet connection is ‘active.’ Under ‘properties’ the ‘Enable this connection’ is ticked. Now here is where I’ve had conflicting advice. Someone said set ‘Configuration’ to ‘DCHP,’ but under this setting the Ip Address, Subnet mask and Gateway address are all greyed out and inactive. If I change ‘Configuration’ to ‘Static IP address’ and enter the details:
IP address 219.79.107.20
Subnet mask 255.255.255.255
Gateway address 219.102.32.208

I still can’t get online. I would warmly appreciate any suggestions and / or advice.

---

### Post by drtvasudevan on 2006-08-09
look at [http://ubuntuforums.org/showthread.php?t=231886](http://ubuntuforums.org/showthread.php?t=231886)

---

### Post by RedBoot on 2006-08-09
Are these printouts from Windows? They look like it.  

I'm not clear about your devices yet. You have one NIC in your PC ( the Broadcom) that is a wired connection, right?

The PPP Adapter: Is that IN the PC or connected to the NIC with a patch cable?  One thing that seems very odd is that your IP address is the same as your default gateway.

---

### Post by Stephen_A on 2006-08-10
Here is the really embarrassing part. The printouts were from another machine and I assumed they would just give information about the IP address. If you kindly tell me how to get the same info from the other machine, I will gladly post it.

---

### Post by RedBoot on 2006-08-10
Let's try DHCP. It IS normal for the fields to go blank. 

In the networking dialog, click on deactivate. Then choose DHCP, okay, then activate and close the windows.  Then run an ifconfig to see if an IP address is assigned.

Also, what is the patch cable plugged into (both ends)?

---

### Post by Stephen_A on 2006-08-10
Thanks for your reply. OK, I'll give that a try and let you know what the result is. One end of the patch cable (RJ-45 jack) goes into the appropriate socket on the Dell laptop with Ubuntu installed. The other end goes into an NTA-3110 router. A phone cable goes from that into the phone socket in the wall. If I take the cable on which I'm trying to connect the Dell and put it into another machine (IBM Thinkpad), then that goes online without any trouble.

---

### Post by Stephen_A on 2006-08-10
I deactivated and reactivated the connection in Netword settings and ran ifconfig. Here is the result: 

stephen@stephen-laptop:~$ sudo ifconfig
Password:
eth0      Link encap:Ethernet  HWaddr 00:0D:56:E9:F0:C3
          inet addr:219.79.107.20  Bcast:219.79.107.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fee9:f0c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5343 (5.2 KiB)  TX bytes:2264 (2.2 KiB)
          Interrupt:7

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1676 (1.6 KiB)  TX bytes:1676 (1.6 KiB)

---

### Post by RedBoot on 2006-08-10
That looks good. I guess you tried Firefox with no succeess?

Run the route command to show you the default gateway assigned and jot it down. It's on the line that starts with 'default' in the column 'gateway'
Also, in the System, Administration, Networking dialog under the DNS tab does it have one or more DNS IP addresses?

Can you ping 127.0.0.1? 
Can you ping 219.79.107.20?
Can you ping the default gateway?
Can you ping the DNS IP?

---

### Post by Stephen_A on 2006-08-10
Yes I tried Firefox, to no avail. I also tried the trick of typing 'about:config' in the URL box and then 'ipv6.' I double clicked on the top line and it changed to 'true.' Still no luck. 
Route command. With that I get: 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
219.79.107.0    *               255.255.255.0   U     0      0        0 eth0
stephen@stephen-laptop:~$

In Network Settings, under the DNS tab there is nothing. I did put my IP address in there earlier, but it has disappeared. When I did put it in, I still could not get online. 

I can ping 127.0.0.1

219.79.107.20 is I believe the Deafault Gateway and I can ping that. I can't pin the DNS Servers' addresses. I presume I need to add the DNS servers in the DNS section of Netword settings.

---

### Post by RedBoot on 2006-08-10
Stephen,
The lack of a second line from the route command indicates that you do not yet have a default gateway specified. 
> ...A phone cable goes from that into the phone socket in the wall. If I take the cable on which I'm trying to connect the Dell and put it into another machine (IBM Thinkpad), then that goes online without any trouble.
Can you go to that computer, hook it up so you can get on the internet, then issue a ipconfig/all and post it? (I hope I'm not having you re-do what you did way back at post #1!)

---

### Post by drtvasudevan on 2006-08-10
here is a suggestion from a total newbie
start network settings.
create a location by pulling down menu from the box on top.
you need to have these entered.
connection:click on ethernet connection>properties. enter the details in:
configuration static ip
 ip address, 
subnet mask
gateway address
see that enable this connection box is ticked.
ok
under general: host name (name of your pc) and domain name (important)
under dns: click add dns servers >enter the value
click ok.

that is all. if you connect fine.
if you connect but the settings are not there on reboot, open network settings and click on the location box and you will see the location you entered.click on that and the settings will be changed.
best of luck.

---

### Post by Stephen_A on 2006-08-11
Now I've entered all the DNS servers data. The command ifconfig gives: 
stephen@stephen-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:56:E9:F0:C3
          inet addr:219.79.107.20  Bcast:219.79.107.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fee9:f0c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:714858 (698.1 KiB)  TX bytes:60112 (58.7 KiB)
          Interrupt:7

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22624 (22.0 KiB)  TX bytes:22624 (22.0 KiB)

I can ping the IP address and the default gateway. But trying to ping the DNS Servers just gives 'Network is unreachable.'

---

### Post by Stephen_A on 2006-08-11
Going back to Redboot's earlier request of going back to the other (Windows) machine. Here is what ipconfig/all gives:

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Broadcom NetXtreme Gigabit Ethernet
        Physical Address. . . . . . . . . : 00-16-41-12-BE-7F
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        Autoconfiguration IP Address. . . : 169.254.163.2
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

PPP adapter NETVIGATOR BROADBAND:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 218.102.238.86
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 218.102.238.86
        DNS Servers . . . . . . . . . . . : 218.102.32.208
                                            205.252.144.126
        NetBIOS over Tcpip. . . . . . . . : Disabled

C:\>

---

### Post by drtvasudevan on 2006-08-11
since packets are sent and received and there are no errors....
can you try this simple fix first?
in the firefox address bar type about:config 
and in the filter bar type ipv6 
and change from false to true -just double click it 
exit from firefox
restart firefox and see.

---

### Post by Stephen_A on 2006-08-12
Sorry for taking so long. Here's the ipconfig/all from the other machine. 
Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Broadcom NetXtreme Gigabit Ethernet
        Physical Address. . . . . . . . . : 00-16-41-12-BE-7F
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        Autoconfiguration IP Address. . . : 169.254.163.2
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

PPP adapter NETVIGATOR BROADBAND:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Physical Address. . . . . . . . . : 00-53-45-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 218.103.221.241
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 218.103.221.241
        DNS Servers . . . . . . . . . . . : 218.102.32.208
                                            205.252.144.126
        NetBIOS over Tcpip. . . . . . . . : Disabled

C:\>

---

### Post by RedBoot on 2006-08-12
Sorry to say my DSL service is not using PPPoE. I'm fresh out of ideas. Maybe someone else who has set up this type of broadband connection can help.

---

### Post by Stephen_A on 2006-08-12
That's OK. Thanks for your help anyway; I've learnt a lot. If I do fix it, I'll let you know.

---

