---
title: "Not sure about these commands"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by InsaniaEx on 2010-05-26
After "finishing" this tutorial, [http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN](http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN)

  I came to a comment claiming the OP had forgotten something 
```
 $IPTABLES -t nat -A PREROUTING -i $WAN_IF -p tcp --dport 3074 -j DNAT --to-destination $XBOX_IP
   $IPTABLES -t nat -A PREROUTING -i $WAN_IF -p udp -m multiport --dports 88,3074 -j DNAT --to-destination $XBOX_IP
   $IPTABLES -A FORWARD -i $WAN_IF -d $XBOX_IP -p tcp --dport 3074 -j ACCEPT
   $IPTABLES -A FORWARD -i $WAN_IF -d $XBOX_IP -p udp -m multiport --dports 88,3074 -j ACCEPT
```
I have no idea what to do with it, I put the first line in the terminal: -t not a command; put the whole thing in -t and -A not commands.

Help?

---

### Post by bodhi.zazen on 2010-05-26
Those are commands for iptabes and NAT

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

The "problem" with them is they are part of a script, and so $IPTABLES is a variable, probalby set to /sbin/iptables.

IMO there are better tools then scripts to manage iptables, and scripts often obscificate the rules.

As a fragment of a rule set it is difficult to impossible to say much other then NAT is basically a Firewall, so those rules are allowing traffic to the XBox.

---

### Post by BoneKracker on 2010-05-26
"$IPTABLES" is a variable.  Unless you have made an assignment to it, it has a null value.

So your shell interpreted the command as "null" -t blah blah blah.  It ignored null and tried to process "-t", and choked on it.  Then it coughed up the hairball, "-t not a command".

Start out with this:```
IPTABLES=$(which iptables)
```Then the rest of it will work.

I have not looked at the tutorial you linked to, so I have no idea what you were up to.  It is possible (probable, in fact) that this code block the author "forgot" is supposed to be inserted into a script you built during the tutorial, as opposed to being entered manually at the command line.

---

### Post by InsaniaEx on 2010-05-26
Thanks, [http://ubuntuforums.org/showthread.php?t=1493927](http://ubuntuforums.org/showthread.php?t=1493927)

If your interested in helping me out further, which you won't seeing as it pretty late, for me anyway...

---

### Post by BoneKracker on 2010-05-26
Okay, I glanced at the tutorial.

If you are going to be putting together your own iptables, it might be a good idea to bookmark this and learn about that first.  This is a good place to start:

[http://www.netfilter.org/documentation/index.html](http://www.netfilter.org/documentation/index.html)

Here is one of the many good tutorials available:
[http://www.frozentux.net/documents/iptables-tutorial/](http://www.frozentux.net/documents/iptables-tutorial/)
[http://www.higherpass.com/linux/Tutorials/Iptables-Primer/](http://www.higherpass.com/linux/Tutorials/Iptables-Primer/)

A related subject is ipsysctl:
[http://www.frozentux.net/ipsysctl-tutorial/chunkyhtml/index.html](http://www.frozentux.net/ipsysctl-tutorial/chunkyhtml/index.html)

And this page lists a collection of resources covering topics worth understanding if you're going to build your own firewall:
[http://linux-ip.net/html/links-doc.html](http://linux-ip.net/html/links-doc.html)

As bodhi.zazen hinted at, there are many iptables automation tools that make managing complex firewalls easier.  Some are for the uninitiated while others are for people who already understand the inner workings.  One I am fond of is called "shorewall".

As long as you are already protected somehow, I think learning iptables from the bottom up is a good exercise.  With a bit of reading, you should be able to build your own basic firewall (including NAT) and save it, or write a script to do that.

But it's not really a good idea to just copy what someone else has done without understanding it, particularly in a security-related area such as firewalls.

---

### Post by InsaniaEx on 2010-05-26
This wasn't the kind of answer I was hoping for. But there is no harm in learning something new.

---

### Post by BoneKracker on 2010-05-26
> **InsaniaEx said:**
> This wasn't the kind of answer I was hoping for. But there is no harm in learning something new.

If you don't want to fiddle with it yourself, then just use one of the many packages that do it for you based on minimal configuration.

---

