---
title: "ufw/gufw/firestarter Block Outgoing Traffic"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by DenKain on 2008-08-15
Today I learned that Firestarter is a dead project and seems to crash alot on Hardy. So I looked into this ufw and thought okay thats not to bad. I also found gufw which is a nice GUI for this command. 

The one thing I wanted to know is can ufw, like Firestarter, block outbound traffic and how? I ask because I am extremely restrictive about what ports are allowed outbound traffic on my home box.

Also, I hear about Firestarter crashing alot. I have never seen the process actually stop so when we say "crashing" what are we talking about?

> **Vivaldi Gloria said:**
> 
I also heard that it crashes
 [QUOTE=Ayuthia;5590688]I just downloaded the source and confirm your  remarks.  You are also correct that it does crash.
 

[/QUOTE]

-DenKain

---

### Post by jerome1232 on 2008-08-15
Will from what I've seen firestarter and ufw together don't like each other so lets get rid of firestarter and make sure iptables is cleared out
```
sudo apt-get remove --purge firestarter
sudo iptables -F INPUT
sudo iptables -F FORWARD
sudo iptables -F OUTPUT
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
```

Now I haven't used gufw but ufw is really easy so I'll go with that
```
sudo ufw default deny
sudo ufw logging on
sudo ufw enable
```
Tells iptables to block all incoming connections, tells ufw to logg all blocked connections and finally has ufw load on boot.

Really though Ubuntu doesn't listen for connections so all ports are closed to begin with (unless you have installed server programs such as openssh-server or samba etc)

If you are behind a router it also acts as a firewall for inbound connections. (so once again no need for a host based firewall like iptables)

---

### Post by DenKain on 2008-09-11
With ufw is there a way to block all outbound connections expect those that I specify?

Such as every port but ports 80, 8080, 20, 21, 143, etc are blocked from sending packets out.

---

### Post by jerome1232 on 2008-09-11
Not to my knowldge I haven't seen any documentation for ufw blocking outgoing connections.

I **Strongly** feel that is a completely unnecessary and  a pain in the butt, why would you need to restrict what can initiate connections.

You would have to directly edit iptables, if you google iptable how-to you should find good examples.

But really... why would you do that?

---

### Post by DenKain on 2008-09-11
Because some illicit programs/services like to "phone home" on odd ports that are not the standard lower ports we use in our day to day lives. With white-listing outgoing ports I at least know that only the ports I use on a daily basis can talk to the outside world.

---

### Post by jerome1232 on 2008-09-11
Don't install programs like that...

---

### Post by DenKain on 2008-09-11
:-P

I will do my best not to install worms, trojans, rootkits and logic bombs, especially those that use zero day attacks, in the future but my guess is that at least the first one is going to happen one day.

EDIT:

Also, I did find this wonderful article:

[http://www.cyberciti.biz/tips/linux-iptables-6-how-to-block-outgoing-access-to-selectedspecific-ip-address.html]("http://www.cyberciti.biz/tips/linux-iptables-6-how-to-block-outgoing-access-to-selectedspecific-ip-address.html")

---

### Post by megandy on 2008-11-07
It's in addition useful to block outgoing traffic when you are using a mobile internet connection (which you often pay per byte) instead of a flat rate. Then it would be useful if only my browser and my e-mail program would cause outbound traffic and not my update manager, my dyndns client, my instant messanger, ...

It would be great if it could be easily manageble via a GUI.

---

### Post by xoros on 2009-04-28
Most programs have documentation on which ports they use. 
You could also watch to see what ip address they connect to.

In gufw, you can go under advanced tab and block the ports and/or the ip addresses respective to the application.

It would be nice if you could filter by selecting the program instead of by it's ports.  I have not found a way to do that yet.

EDIT:
I've found a program called Tuxguardian.
[http://tuxguardian.sourceforge.net/index.php](http://tuxguardian.sourceforge.net/index.php)

> With TuxGuardian you'll be able to implement access control policies to the network resources in order to identify and control every application that tries to access the network. 

I have not tested it yet, so not sure how well it works.

============================
You can also block apps by setting up files and using iptables:
[http://www.linux.com/feature/121374](http://www.linux.com/feature/121374)

> Create a file that holds the IP addresses that you wish to block. Use one address per line, and add comments with the pound sign (#). (Your file could have line after line of IP addresses, no comments, and no blank lines, but it wouldn't be very understandable.)

# IP addresses blocked for msn messenger
# ********************************

# sales, office 2
192.168.100.10

# accounting (all)
192.168.100.23
192.168.100.24
192.168.100.25

# production, building A
192.168.100.50

Name this file as you wish; I called mine ip_msn. Now run the following command to remove the comments and the blank lines and create a temporary file that will become part of the iptables rules:

grep -v "#" /your/path/ip_msn | sed -e '/^$/d' > /tmp/temp

grep -v outputs the lines that don't start with #, and sed eliminates empty lines and redirects the output to the temporary file.

Now create a short script (you can include the above command) that reads every address from this file and adds the iptables rules:

grep -v "#" /your/path/ip_msn | sed -e '/^$/d' > /tmp/temp
while read IP ; do
 /sbin/iptables -t mangle -A PREROUTING -s $IP -p tcp --dport 1863 -j REJECT
done < /tmp/temp


---

### Post by xoros on 2009-04-28
Here is a way to block outgoing by process id
First, use "**ps aux**" to find the process name.

Then for a script:
Assign a variable the id number, then you do the rule:
```

PID=`ps aux |grep <process name here> |head -n 1 |cut -b 10-14`
/sbin/iptables -A OUTPUT -p TCP -m owner --pid-owner $PID -j DROP

```

So for example:
```

PID=`ps aux |grep bluetooth-applet |head -n 1 |cut -b 10-14`
/sbin/iptables -A OUTPUT -p TCP -m owner --pid-owner $PID -j DROP
```

---

### Post by xoros on 2009-04-28
ufw cannot block outgoing.

---

### Post by narnie on 2009-08-23
I just tried this on my jaunty box, but and checked an ufw status which showed.

```
Status: active

To                         Action  From
--                         ------  ----
1:65535/udp                DENY    192.168.1.102
1:65535/tcp                DENY    192.168.1.102
```

but it didn't block any outgoing traffic. E.g., I could browse the web just fine.

in the insterest of proving I put in the right IP # for my box, ifconfig|grep 192 shows
```
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
```

my iptables-save shows

```
# Generated by iptables-save v1.4.1.1 on Sun Aug 23 00:20:24 2009
*filter
:INPUT DROP [98:6829]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [3:120]
:ufw-after-forward - [0:0]
:ufw-after-input - [0:0]
:ufw-after-logging-forward - [0:0]
:ufw-after-logging-input - [0:0]
:ufw-after-logging-output - [0:0]
:ufw-after-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-before-input - [0:0]
:ufw-before-logging-forward - [0:0]
:ufw-before-logging-input - [0:0]
:ufw-before-logging-output - [0:0]
:ufw-before-output - [0:0]
:ufw-logging-allow - [0:0]
:ufw-logging-deny - [0:0]
:ufw-not-local - [0:0]
:ufw-reject-forward - [0:0]
:ufw-reject-input - [0:0]
:ufw-reject-output - [0:0]
:ufw-user-forward - [0:0]
:ufw-user-input - [0:0]
:ufw-user-limit - [0:0]
:ufw-user-limit-accept - [0:0]
:ufw-user-logging-forward - [0:0]
:ufw-user-logging-input - [0:0]
:ufw-user-logging-output - [0:0]
:ufw-user-output - [0:0]
-A INPUT -j ufw-before-logging-input 
-A INPUT -j ufw-before-input 
-A INPUT -j ufw-after-input 
-A INPUT -j ufw-after-logging-input 
-A INPUT -j ufw-reject-input 
-A FORWARD -j ufw-before-logging-forward 
-A FORWARD -j ufw-before-forward 
-A FORWARD -j ufw-after-forward 
-A FORWARD -j ufw-after-logging-forward 
-A FORWARD -j ufw-reject-forward 
-A OUTPUT -j ufw-before-logging-output 
-A OUTPUT -j ufw-before-output 
-A OUTPUT -j ufw-after-output 
-A OUTPUT -j ufw-after-logging-output 
-A OUTPUT -j ufw-reject-output 
-A ufw-after-input -p udp -m udp --dport 137 -j RETURN 
-A ufw-after-input -p udp -m udp --dport 138 -j RETURN 
-A ufw-after-input -p tcp -m tcp --dport 139 -j RETURN 
-A ufw-after-input -p tcp -m tcp --dport 445 -j RETURN 
-A ufw-after-input -p udp -m udp --dport 67 -j RETURN 
-A ufw-after-input -p udp -m udp --dport 68 -j RETURN 
-A ufw-after-input -m addrtype --dst-type BROADCAST -j RETURN 
-A ufw-after-logging-forward -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] " 
-A ufw-after-logging-input -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] " 
-A ufw-before-forward -j ufw-user-forward 
-A ufw-before-input -i lo -j ACCEPT 
-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A ufw-before-input -m state --state INVALID -j ufw-logging-deny 
-A ufw-before-input -m state --state INVALID -j DROP 
-A ufw-before-input -p icmp -m icmp --icmp-type 3 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 4 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 11 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 12 -j ACCEPT 
-A ufw-before-input -p icmp -m icmp --icmp-type 8 -j ACCEPT 
-A ufw-before-input -p udp -m udp --sport 67 --dport 68 -j ACCEPT 
-A ufw-before-input -j ufw-not-local 
-A ufw-before-input -s 224.0.0.0/4 -j ACCEPT 
-A ufw-before-input -d 224.0.0.0/4 -j ACCEPT 
-A ufw-before-input -j ufw-user-input 
-A ufw-before-output -o lo -j ACCEPT 
-A ufw-before-output -p tcp -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT 
-A ufw-before-output -p udp -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT 
-A ufw-before-output -j ufw-user-output 
-A ufw-logging-allow -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW ALLOW] " 
-A ufw-logging-deny -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] " 
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN 
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN 
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN 
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny 
-A ufw-not-local -j DROP 
-A ufw-user-input -s 192.168.1.102/32 -p tcp -m multiport --dports 1:65535 -j DROP 
-A ufw-user-input -s 192.168.1.102/32 -p udp -m multiport --dports 1:65535 -j DROP 
-A ufw-user-limit -m limit --limit 3/min -j LOG --log-prefix "[UFW LIMIT BLOCK] " 
-A ufw-user-limit -j REJECT --reject-with icmp-port-unreachable 
-A ufw-user-limit-accept -j ACCEPT 
COMMIT
# Completed on Sun Aug 23 00:20:24 2009
```

Any idea why this doesn't block outgoing traffic, including http on port 80?

With thanks,
Narnie

---

### Post by dmizer on 2009-08-23
Perfectly easy to do if you poke around in the gufw settings.

You can either deny preconfigured settings, or you can deny specific ports or IP addresses (under "add a new rule" > preconfigured or advanced). Just switch the setting from "allow" to "deny" and add localhost to the from field.

---

### Post by airtonix on 2010-01-28
> **jerome1232 said:**
> Don't install programs like that...

This is hardly helpful advice and definitely will not stop a program from "phoning home"...

I assume you've scanned all your softwares source code for elements that might be "phoning home"?

all twelve trillion accumulated lines of it ? 

No i didn't think so...


> **narnie said:**
> I just tried this on my jaunty box, but and checked an ufw status which showed.

...

Any idea why this doesn't block outgoing traffic, including http on port 80?

With thanks,
Narnie

I assume you tried using localhost or 127.0.0.1 instead ? 


----

Honestly I think more minds would put at ease if a application-based-firewall were compiled and provided in the ubuntu repositories....

application-based firewalls : 

[LIST]
[*] tuxguardian : [http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)
[*] Program Guard : [http://pgrd.sourceforge.net/](http://pgrd.sourceforge.net/)
[*] SysTrace : [http://www.citi.umich.edu/u/provos/systrace/](http://www.citi.umich.edu/u/provos/systrace/)
[/LIST]

It is supposed to do exactly what the original-poster desires.

---

### Post by dmizer on 2010-01-28
> **airtonix said:**
> Honestly I think more minds would put at ease if a application-based-firewall were compiled and provided in the ubuntu repositories....

This already exists in Ubuntu by default, it just needs to be configured: [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by nopedx on 2010-02-17
jerome1232, your post is 100% right on. Forget **Firestarter**, not that it's bad software! UFW is just so uncomplicated. Your explicit directions are indeed all that is needed for the firewall providing safe downloading, following fresh install of 9.10, this was the final touch.
This was your input:


Code:
remove firestarter:
sudo apt-get remove --purge firestarter
reset iptables:
sudo iptables -F INPUT
sudo iptables -F FORWARD
sudo iptables -F OUTPUT
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT

"Now I haven't used gufw but ufw is really easy so I'll go with that"
AMEN!
Code:
sudo ufw default deny
sudo ufw logging on
sudo ufw enable

SO UNCOMPLICATED!

Thanks jerome1232

---

### Post by megandy on 2010-02-18
There's even a gui for gnome: gufw

---

### Post by xoros on 2010-05-11
Block all outgoing traffic:
```
sudo iptables -A OUTPUT -p udp -j DROP 
sudo iptables -A OUTPUT -p tcp -j DROP 
```

Enable all outgoing traffic:
```
sudo iptables -D OUTPUT -p udp -j DROP 
sudo iptables -D OUTPUT -p tcp -j DROP 
```

---

