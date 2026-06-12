---
title: "[SOLVED] Firestarter doesn't help against port scan services"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by meindian523 on 2007-09-03
My net connection is through the ISP called MTNL,in Bombay,India.(I believe my machine is connected to the Net through a proxy which assigns me a dynamic IP addres.I have installed Firestarter firewall but when I try to scan my PC by the [ShieldsUP! ]("https://www.grc.com/x/ne.dll?bh0bkyd2") resource,it shows me that ports 21,22,23 and 80 are open while 25 is stealthed and others are closed.Though I'm at a home-desktop,I wouldn't want my machine to be part of a zombie network implicated in a DoS attack.My machine also replied to pings.

Now,I don't know whether this analysis tested my machine or just the proxy,but I would prefer if someone could help me setup an iptables firewall(I guess it's the strongest??).I've tried various Google searches and searches of these forums but none of them described a procedure to setup an iptables firewall without going through the intricacies of iptables,NAT and masquerading.I have no objection to learning them but I would prefer my computer to be safe before I start understanding exactly how he firewalls work.Another port scan service went through the proxy and revealed my private IP address to me,therefore I'm seriously worried.Can someone help?

---

### Post by meindian523 on 2007-09-03
bumpetty bump

---

### Post by nvteighen on 2007-09-03
Let's see. You should know Firestarter it's just a graphical interface for iptables. So, simply put Firestarter = iptables.

Could you please answer to these questions?
1) Have you any server software installed? (Apache, online games, etc...) If so, then, you'll get open ports and you'll have to configure the firewall, or remove software you no longer use but it's running in the background.
2) If you have installed firestarter and configured, does it start at reboot or do you have to explicitly open it to make it work? If it doesn't start automatically, [go here]("http://ubuntuforums.org/showthread.php?p=3071503") (that's a problem I had).

---

### Post by meindian523 on 2007-09-03
> **nvteighen said:**
> Let's see. You should know Firestarter it's just a graphical interface for iptables. So, simply put Firestarter = iptables.

Could you please answer to these questions?
1) Have you any server software installed? (Apache, online games, etc...) If so, then, you'll get open ports and you'll have to configure the firewall, or remove software you no longer use but it's running in the background.
Nope,no games other than waht came installed with Ubuntu....I'm not running any server,AFAIK.I've not installed any server software unless it came with the Live CD.....
> **nvteighen said:**
> 
2) If you have installed firestarter and configured, does it start at reboot or do you have to explicitly open it to make it work? If it doesn't start automatically, [go here]("http://ubuntuforums.org/showthread.php?p=3071503") (that's a problem I had).

I don't keep my Net on at all time,I switch on the router  when I need it(D-Link DSL 502T) and put it off when I don't.I don't guess I need an always-on firewall.

Thanks for replying,After all the newbies(what am I saying,I'm one myself:) ) said that they got the fastest help here,I was thinking,why is no -one replying??

---

### Post by meindian523 on 2007-09-03
One second,I just put firestarter in the sessions,lemme logout and check whether it starts automatically

---

### Post by nvteighen on 2007-09-03
> **meindian523 said:**
> Nope,no games other than waht came installed with Ubuntu....I'm not running any server,AFAIK.I've not installed any server software unless it came with the Live CD.....

No, the Desktop Live CD comes without any server, so that's discarded. But, to be sure, please, **close any application that access the Internet**, enter a Terminal (Applications --> Accessories --> Terminal) and type:

```

netstat -tl

```

You should only get ports listening from "localhost" (no problem at all, it's your pc listening to itself).

> I don't keep my Net on at all time,I switch on the router  when I need it(D-Link DSL 502T) and put it off when I don't.I don't guess I need an always-on firewall.

Actually, I wasn't clear enough. Iptables is always on; Firestarter is just a graphical program to configure it and it doesn't need to be always running, but it must be started automatically so iptables gets configured at boot. We'll need to run another "test" to see if it is working properly, but it can involve a reboot, so firstly please the one I told you above.

---

### Post by meindian523 on 2007-09-03
> **nvteighen said:**
> No, the Desktop Live CD comes without any server, so that's discarded. But, to be sure, please, **close any application that access the Internet**, enter a Terminal (Applications --> Accessories --> Terminal) and type:

```

netstat -tl

```

You should only get ports listening from "localhost" (no problem at all, it's your pc listening to itself).
```

easwarh@l1nuxr0cks:~$ sudo netstat -tl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:x11-1                 *:*                     LISTEN     
tcp6       0      0 *:x11-1                 *:*                     LISTEN     
easwarh@l1nuxr0cks:~$ 
```

> **nvteighen said:**
> 
Actually, I wasn't clear enough. Iptables is always on; Firestarter is just a graphical program to configure it and it doesn't need to be always running, but it must be started automatically so iptables gets configured at boot. We'll need to run another "test" to see if it is working properly, but it can involve a reboot, so firstly please the one I told you above.

No probs with a reboot,I'm on a home-desktop.....;)

---

### Post by nvteighen on 2007-09-03
> **meindian523 said:**
> ```

easwarh@l1nuxr0cks:~$ sudo netstat -tl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:x11-1                 *:*                     LISTEN     
tcp6       0      0 *:x11-1                 *:*                     LISTEN     
easwarh@l1nuxr0cks:~$ 
```

That's weird... No, do it without sudo. And, have you your connection on? (I meant to close applications, like Firefox or Evolution...)

The other test is to reboot and do:

```

sudo iptables --list

```

---

### Post by meindian523 on 2007-09-03
```
easwarh@l1nuxr0cks:~$ netstat -tl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:x11-1                 *:*                     LISTEN     
tcp6       0      0 *:x11-1                 *:*                     LISTEN     
easwarh@l1nuxr0cks:~$ 

```

I noticed that after listing the first entry namely **tcp 0 0 *:x11-1 *:* LISTEN**,it halted for a while,like if it was a GUI,I would have said hung and then after a few seconds,it put in the second entry namely the tcp6 .... one.

Do you want me to reboot and try sudo iptables --list?And firestarter when added to the sessions list didn't start(atleast I didn't see the icon in the taskbar) and when I did System>>Administration>>Firestarter,it asked me password and then the icon came along.....

---

### Post by nvteighen on 2007-09-03
Yes, reboot and use "sudo iptables --list" or "sudo iptables -nL". It's the same, just a bit quicker, without "hanging" (that's because it's checking the connections; it's normal both for netstat and iptables).

If you should **not** get the following:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by meindian523 on 2007-09-03
```
easwarh@l1nuxr0cks:~$ sudo iptables --list
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
easwarh@l1nuxr0cks:~$ 

```

I got exactly that.:(This should be done with the connection inactive(the router off,firestarter not started),correct?

---

### Post by nvteighen on 2007-09-03
Well, then do this:

Open a terminal and type:
```

gksudo gedit /etc/firestarter/firestarter.sh

```

Locate the following "paragraph" (it's near the beginning):

```

if [ "$MASK" = "" -a "$1" != "stop" ]; then
        echo "External network device $IF is not ready. Aborting.."
        exit 2
fi

```

And make it look this way (put a # in front of all lines):
```

#if [ "$MASK" = "" -a "$1" != "stop" ]; then
        #echo "External network device $IF is not ready. Aborting.."
        #exit 2
#fi

```

EDIT: Don't touch anything else than that paragraph!
Save and reboot. Don't worry, a backup of the original is automatically created. This should make Firestarter correctly configure iptables at start. You won't see anything. To check if it worked, do "sudo iptables -nL" again and you should not see what you got before. Then, go to Shields Up again.

---

### Post by meindian523 on 2007-09-03
```
easwarh@l1nuxr0cks:~$ sudo iptables -nL
Password:
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  208.67.222.222       0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  208.67.222.222       0.0.0.0/0           
ACCEPT     tcp  --  208.67.220.220       0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  208.67.220.220       0.0.0.0/0           
ACCEPT     tcp  --  192.168.1.1          0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  192.168.1.1          0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
DROP       0    --  0.0.0.0/0            255.255.255.255     
DROP       0    --  224.0.0.0/8          0.0.0.0/0           
DROP       0    --  0.0.0.0/0            224.0.0.0/8         
DROP       0    --  255.255.255.255      0.0.0.0/0           
DROP       0    --  0.0.0.0/0            0.0.0.0             
DROP       0    --  0.0.0.0/0            0.0.0.0/0           state INVALID 
LSI        0    -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
INBOUND    0    --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
DROP       0    --  224.0.0.0/8          0.0.0.0/0           
DROP       0    --  0.0.0.0/0            224.0.0.0/8         
DROP       0    --  255.255.255.255      0.0.0.0/0           
DROP       0    --  0.0.0.0/0            0.0.0.0             
DROP       0    --  0.0.0.0/0            0.0.0.0/0           state INVALID 
OUTBOUND   0    --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
LSI        0    --  0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
LOG        icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
REJECT     0    --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
easwarh@l1nuxr0cks:~$ 
```

I hope this is what is expected.....

How did commenting out those lines help?

---

### Post by nvteighen on 2007-09-03
Perfect! Have you tried Shields Up?

The problem seems to be a conflict between Firestarter and Network Manager. It seems that is a problem related to the order in which both boot. Commenting that out forces firestarter to continue loading.

(Maybe now you should look in Firestarter if your configuration is right (use the wizard): that depends on what you like/need. Of course, block all incoming connections...)

---

### Post by meindian523 on 2007-09-03
No difference,21,22,23 and 80 are still open.Do ya think this could be due to the service scanning the proxy and not my machine.But 1 advantage did come out.....they couldn't trace my location thru Reverse DNS which they could earlier.Also ping was replied to too.....

---

### Post by meindian523 on 2007-09-03
Where do I find the wizard?

---

### Post by nvteighen on 2007-09-03
> **meindian523 said:**
> No difference,21,22,23 and 80 are still open.Do ya think this could be due to the service scanning the proxy and not my machine.But 1 advantage did come out.....they couldn't trace my location thru Reverse DNS which they could earlier.Also ping was replied to too.....

Well, I don't know that much, but it seems so... But now you have the firewall working, so I would be more calmed (and the reverse DNS failure is good news). Remember: you don't need to have Firestarter open all the time, but from time to time get into Firestarter and look at the events that were catched; then, you could google about them.

Sorry, I'll have to go. I'm glad to have been able to help you a bit.

---

### Post by nvteighen on 2007-09-03
> **meindian523 said:**
> Where do I find the wizard?
Ah! Open Firestarter and go to "Firewall"  menu--> Wizard.

---

### Post by meindian523 on 2007-09-03
Thanx a million.....:)

---

### Post by CowzRule on 2007-09-03
> **meindian523 said:**
> No difference,21,22,23 and 80 are still open.Do ya think this could be due to the service scanning the proxy and not my machine.But 1 advantage did come out.....they couldn't trace my location thru Reverse DNS which they could earlier.Also ping was replied to too.....

To prevent Ping from being replied to open Firestarter, click the Preferences button, click ICMP Filtering, click the box next to Enable ICMP filtering and make sure none of the boxes under Allow the following ICMP packets type is checked.

[IMG]http://i14.tinypic.com/6fa8bx3.png[/IMG]

---

