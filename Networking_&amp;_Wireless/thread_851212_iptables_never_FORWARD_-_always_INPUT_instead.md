---
title: "iptables never FORWARD - always INPUT instead"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by WARnux on 2008-07-06
The situation:

I do not have a router because the Linksys WRT routers I used to buy break all the time.  Hence my firewall and Linux workstation are one in the same right now.  I also have only one ethernet card.

I do not allow ssh on port 22 to the outside.  Instead I forward from another port to 22.  The problem is that PREROUTING natting and REDIRECT is supposed to FORWARD the packets.  This is not happening.  They are always passed as INPUT instead.

I worked around the problem by marking the packet.  I don't mind doing it, but I don't think I should have needed to.  Is this a bug?

```
#!/bin/sh

iface="eth0"
thisIP="`ifconfig $iface | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"
interface="-i $iface"
outInterface="-o $iface"
sshOuter="1025"
sshInner="22"
#/var/log/messages
log="-j LOG --log-prefix "

#port forwarding to another port on the firewall
#had to mark because they were always passed as INPUT, not FORWARD
iptables -A PREROUTING -p tcp -t mangle $interface --dport $sshOuter -j MARK --set-mark 22
iptables -A PREROUTING -t nat -p tcp $interface --dport $sshOuter -j REDIRECT --to-port $sshInner
iptables -A INPUT -m mark --mark 22 -j ACCEPT
```

---

### Post by kevdog on 2008-07-06
I think you said it yourself.  You have only one ethernet card.  Forwarding forwards a connection from one interface to another.  Without a second interface (second networking card) I don't see how this is possible, unless you are using some type of virtual interfaces which you have described.

If you are talking about nat -- which it seems you are doing, then that is another matter.  Am I way off base here?

---

### Post by WARnux on 2008-07-06
Nope, you're right on track.

Do you think creating a virtual interface is a better solution than what I'm currently doing?

---

### Post by kevdog on 2008-07-06
Ive worked with nat but never the mangle table before -- to tell you the truth I don't really understand the mangle table all that well.  fwknop -- a port knocking program -- does the exact thing that you are describing.  You can connect to a randomly defined port, and internally it forwards or routes the connection to port 22 (or the ssh port).  The source code is available, however I've never looked to see how it is actually done (other then messing with the nat table).  The author of the program may be able to give you some insight how the iptable rule is actually written.  I know for a fact however that this program does not create a virtual interface to accomplish the nat translation.

---

### Post by WARnux on 2008-07-06
Ok thanks.  I'll take a look at the code myself and post back if I find anything useful.

---

### Post by kevdog on 2008-07-06
Ive done some reading and I dont understand your connudrum. 

Ok your basic command structure looks good (example):

iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 \
        -j REDIRECT --to-port 3128

But I don't understand why you need to mark the chain.  Because the packet traverses the nat table prior to the input table, once the packet is alterated at the prerouting nat table, its either going to be passed to the forwarding or input mangle table.  

Why do you need to mark the packet?  Since you've redirected the packet to port 22, cant you set up a rule to ACCEPT any tcp port 22, rather than use the mark statement?

---

### Post by WARnux on 2008-07-06
>> cant you set up a rule to ACCEPT any tcp port 22, rather than use the mark statement

That would defeat the entire purpose of using a different outside port.  Anyone would be able to try and hack my network using the well-known port 22.

---

### Post by kevdog on 2008-07-06
Yes, I know that -- its basically like changing the ssh daemon to run on a different port.  Isn't that what you are really doing here??

But rereading your 1st post like 20 times -- that seems to be what you are describing.  Maybe I have missed something.

#port forwarding to another port on the firewall
#had to mark because they were always passed as INPUT, not FORWARD
iptables -A PREROUTING -p tcp -t mangle $interface --dport $sshOuter -j MARK --set-mark 22
iptables -A PREROUTING -t nat -p tcp $interface --dport $sshOuter -j REDIRECT --to-port $sshInner
iptables -A INPUT -m mark --mark 22 -j ACCEPT

The first PREROUTING statement -- your simply marking the packet defined by a specific port number.

The second PREROUTING statemtn -- your doing a DNAT to change the packet destination from one port to another

The third statement -- your accepting on the INPUT chain any marked packet.  

So you are doing a couple of things with this example
#1 -- You are marking a packet and then eventually accepting it
#2 -- You are doing a DNAT -- but to what end?  Where does this packet end up?  Its the same packet that was marked, and you are only filtering/accepting the packet based on marked criteria, not the new destination port criteria.

---

### Post by WARnux on 2008-07-06
Yep.  Is there something wrong with it?  I don't have port 22 open for the world to see.

---

### Post by WARnux on 2008-07-06
Only the first packet for each connection is marked.  After that, communication happens on 22.

---

### Post by WARnux on 2008-07-06
I didn't post my whole script above.  This is the first INPUT I process:
```
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```
which is why my former statement is true.

---

### Post by WARnux on 2008-07-06
This is not near all of my script but I think it is all that's relevant for this topic.
```
#!/bin/sh

iface="eth0"
thisIP="`ifconfig $iface | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"
interface="-i $iface"
outInterface="-o $iface"
sshOuter="1025"
sshInner="22"
#/var/log/messages
log="-j LOG --log-prefix "

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#port forwarding to another port on the firewall
#had to mark because they were always passed as INPUT, not FORWARD
iptables -A PREROUTING -p tcp -t mangle $interface --dport $sshOuter -j MARK --set-mark 22
iptables -A PREROUTING -t nat -p tcp $interface --dport $sshOuter -j REDIRECT --to-port $sshInner
iptables -A INPUT -m mark --mark 22 -j ACCEPT
```

---

### Post by kevdog on 2008-07-06
So why dont you just run your ssh daemon on a different port?   As  you have your script right now -- there is always an open port to your ssh server -- just through a convoluted route.  internet->outport->inport->ssh daemon.  Not that there is anything wrong with this but isn't it the same effect as running your ssh server over a different port as specified in the sshd_config file?  If you need dynamic ports to open and close, I would suggest a port knocker utility such as fwknop -- the only catch with this is that you always need a client involved in the process -- which can sometimes add a layer of complexity.

---

### Post by WARnux on 2008-07-06
Two good points.

Point 1:
Yes, I could configure ssh to listen on port X, but that would take away the fun of the power in iptables.

Point 2:
I'm a programmer myself.  I think there is a way to have iptables filter packets/requests through a program but I could not find it when I looked recently.  I don't need anything complex.  fwknop is a little over the top for my taste.  I'd rather keep things simple.  I'm also not fond of perl.

If I made a server type program I would think I could just use telnet to send a special string to it as it listens on a port, as a port-knocker server does, I guess.  That way I could open the port from any computer without the need for a certain client.

---

### Post by kevdog on 2008-07-06
Ok, great, as long as we are on the same page..I thought I was missing something.

---

### Post by WARnux on 2008-07-06
Also a good technique to descourage attacks.  The attacker will have to wait 2 minutes between every 2 attempts.  I'm posting this for the benefit of our other fellow Linux users.

```
#SSH brute force protection
#User can try hitcount-1 times before waiting
sshAttack="iptables -A INPUT -p tcp --dport $sshInner -m recent --seconds 120 --hitcount 3 --name SSH"
$sshAttack --rcheck $log "iptables_ssh_attack: "
$sshAttack --update -j DROP
iptables -A INPUT -p tcp --dport $sshInner -m state --state NEW -m recent --set --name SSH -j ACCEPT
```

---

### Post by WARnux on 2008-07-06
From
[http://www.debian-administration.org/articles/268](http://www.debian-administration.org/articles/268)
```
# Netfilter/IPtables - example of multiple-port knocking
# Note: Knock ports 100,200,300,400 to open SSH port for 5 seconds.
# Nice thing to knock TCP with is `telnet' program:
# $> alias k='telnet ip_address_or_hostname'
# $> k 100 ; k 200 ; k 300 ; k 400 ; ssh ip_address_or_hostname
# Then press Ctrl-C 4 times. That's all. Enjoy.

HOST_IP="12.34.56.78"

/sbin/iptables -N INTO-PHASE2
/sbin/iptables -A INTO-PHASE2 -m recent --name PHASE1 --remove
/sbin/iptables -A INTO-PHASE2 -m recent --name PHASE2 --set
/sbin/iptables -A INTO-PHASE2 -j LOG --log-prefix "INTO PHASE2: "

/sbin/iptables -N INTO-PHASE3
/sbin/iptables -A INTO-PHASE3 -m recent --name PHASE2 --remove
/sbin/iptables -A INTO-PHASE3 -m recent --name PHASE3 --set
/sbin/iptables -A INTO-PHASE3 -j LOG --log-prefix "INTO PHASE3: "

/sbin/iptables -N INTO-PHASE4
/sbin/iptables -A INTO-PHASE4 -m recent --name PHASE3 --remove
/sbin/iptables -A INTO-PHASE4 -m recent --name PHASE4 --set
/sbin/iptables -A INTO-PHASE4 -j LOG --log-prefix "INTO PHASE4: "

/sbin/iptables -A INPUT -m recent --update --name PHASE1

/sbin/iptables -A INPUT -p tcp --dport 100 -m recent --set --name PHASE1
/sbin/iptables -A INPUT -p tcp --dport 200 -m recent --rcheck --name PHASE1 -j INTO-PHASE2
/sbin/iptables -A INPUT -p tcp --dport 300 -m recent --rcheck --name PHASE2 -j INTO-PHASE3
/sbin/iptables -A INPUT -p tcp --dport 400 -m recent --rcheck --name PHASE3 -j INTO-PHASE4

/sbin/iptables -A INPUT -p tcp -s $HOST_IP --dport 22 -m recent --rcheck --seconds 5 --name PHASE4 -j ACCEPT
```

---

### Post by kevdog on 2008-07-06
Have you tried that implementation -- does that actually work?  Bad part about telnet is that the packets are unencrypted.  If you were using a wireless connection, the combination could be sniffed.

As far as hitcount -- definitely a good implementation, however something similar could be done with the limit option with the limit and limit-burst arguments.  One tutorial I read warned against used the recent module if you don't have to since it is quite complex and is rather slow!!

---

### Post by WARnux on 2008-07-06
>> One tutorial I read warned against used the recent module if you don't have to since it is quite complex and is rather slow

Yes, I can see that being a problem.

>> limit and limit-burst

I'll have to look into that.

---

### Post by kevdog on 2008-07-07
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html#LIMITMATCH](http://iptables-tutorial.frozentux.net/iptables-tutorial.html#LIMITMATCH)

---

### Post by WARnux on 2008-07-07
I didn't have time to look over the link yet.

Does limiting limit to everyone together or by IP?  If everyone, I'd rather use what I'm using now because I don't want to punish every user for what some hacker is doing.

---

