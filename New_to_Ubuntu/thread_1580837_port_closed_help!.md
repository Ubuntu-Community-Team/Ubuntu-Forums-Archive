---
title: "port closed? help!"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by gdtw on 2010-09-23
cannot open a port?

sudo ufw allow 1129
sudo ufw status shows 1129 "allow"

Still - the port is closed?

Please help!
Thanks

---

### Post by gdtw on 2010-09-24
I also wonder why after reboot, ufw is inactive?

---

### Post by baddog144 on 2010-09-24
How are you checking whether the port is open?

---

### Post by 3rdalbum on 2010-09-24
> **gdtw said:**
> cannot open a port?

sudo ufw allow 1129
sudo ufw status shows 1129 "allow"

Still - the port is closed?

Please help!
Thanks

Have you got a broadband router? These already have firewalls, which means you don't need ufw.

---

### Post by gdtw on 2010-09-24
> **baddog144 said:**
> How are you checking whether the port is open?

[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)

---

### Post by gdtw on 2010-09-24
> **3rdalbum said:**
> Have you got a broadband router? These already have firewalls, which means you don't need ufw.

Yes, its comcast with static IP. However, I never set up the firewall on the router. Actually its a modem. don't need a router.

Still, netstat does not show 1129 open..

---

### Post by baddog144 on 2010-09-24
Hrmmm. You should check your modem's configuration page to see if it has anything on port forwarding. Beyond that, I dunno.

---

### Post by gdtw on 2010-09-24
> **baddog144 said:**
> Hrmmm. You should check your modem's configuration page to see if it has anything on port forwarding. Beyond that, I dunno.

I am not sure I understand how port forwarding relates to opening a port?

---

### Post by baddog144 on 2010-09-24
It'll open it to everything outside your LAN. I don't know if your modem will restrict any of those by default.

---

### Post by gdtw on 2010-09-24
> **baddog144 said:**
> It'll open it to everything outside your LAN. I don't know if your modem will restrict any of those by default.

Comcast says the firewall on the gateway is off, so they are not blocking any ports...

my server is wired directly to the gateway. Now the gateway does not block, and ufw status shows 1129 allow..  doesn't 1129 allow mean that port 1129 is open?

---

### Post by mcduck on 2010-09-24
> **gdtw said:**
> [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)

Do you actually have something running that would respond to incoming connections on that port? If not, it's not going to show as open port.

Ubuntu, by default, doesn't actually have *any* ports closed. There's no need to, as there are no programs running that would listen fro incoming connections.

What comes to UFW not running, have you confirmed this by running "ufw status"? And of course have you actually enabled UFW ("sudo ufw enable")? It's not running by default...

---

### Post by gdtw on 2010-09-24
> **mcduck said:**
> Do you actually have something running that would respond to incoming connections on that port? If not, it's not going to show as open port.

Ubuntu, by default, doesn't actually have *any* ports closed. There's no need to, as there are no programs running that would listen fro incoming connections.

What comes to UFW not running, have you confirmed this by running "ufw status"? And of course have you actually enabled UFW ("sudo ufw enable")? It's not running by default...

I enabled ufw and then allow 1129. I then went back to my original problem which was that my server was unable to respond/receive incoming communication. After I open the port, i tested and the problem still exists.

According to what you are saying, my ufw was originally inactive, so all my ports are open? so why can my server not receive incoming messages (postback from an external credit card gateway) to start with?

---

### Post by mcduck on 2010-09-24
> **gdtw said:**
> I enabled ufw and then allow 1129. I then went back to my original problem which was that my server was unable to respond/receive incoming communication. After I open the port, i tested and the problem still exists.

According to what you are saying, my ufw was originally inactive, so all my ports are open? so why can my server not receive incoming messages (postback from an external credit card gateway) to start with?

hard to say why, as I don't know that much about what server you are running and how it's configured, or what type of Internet connection and devices you are using.

But it definitely isn't firewall that's blocking your connection, at least unless you yourself install a firewall and tell it to block the port.

The most common reason would be a router with NAT or a firewall enabled, but since you say you aren't using a router that's out of the question. If you have access to the gateway yourself I'd recommend checking it's settings. And of course the configuration of the server itself...

---

### Post by fly-by-night on 2010-09-24
Just a little something that might help.  
Deny rules take precedence over allow rules.  It is my understanding from playing around with ufw that a general deny rule can sometimes override a more specific allow rule (correct me if I'm wrong).  Then again I might have messed up my rules to the point where it appear this way.

---

### Post by gdtw on 2010-09-24
> **fly-by-night said:**
> Just a little something that might help.  
Deny rules take precedence over allow rules.  It is my understanding from playing around with ufw that a general deny rule can sometimes override a more specific allow rule (correct me if I'm wrong).  Then again I might have messed up my rules to the point where it appear this way.

That sounds interesting...
theoretically as i understand, the whole point of a firewall is to deny everything with only certain exceptions..

---

### Post by fly-by-night on 2010-09-24
> **gdtw said:**
> That sounds interesting...
theoretically as i understand, the whole point of a firewall is to deny everything with only certain exceptions..

About two days ago, I "studied" iptables for about 20 minutes and there was something that might explain my reason for disabling ufw.

I set deny all incoming/outgoing.  Then I tried allowing specific apps like Firefox and update manager etc.  Nothing worked - not even resetting and restarting.

Back to my 20 minutes with iptables:  Apparently there's a table with rules and I think INSERT and APPEND etc.  Depending which one you use the rule is added to the top or bottom of the list of rules.  The order in which the rules are processed determine the outcome.  But to make it (more) interesting there's that bit about the deny rule messing with my head even more.  ufw supposedly make all this easier by configuring the tables with simple commands...

The Security section of the Ubuntuforums is the place where the people that really know explain these things.  The resident expert is bodhi.zazen (and others).

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by endotherm on 2010-09-24
just to clarify, you do understand that for a port to be open, and application has to be listening on it, right? I don't have a service running on port 345, so if I allowed 345 in iptables, the port would still be closed. 

think of the terminology this way:
*Open/Closed* deals with whether you have a service on that port. if there is no app, it;'s closed. 

*Blocked/Allowed* deals with whether your firewall will let traffic reach that port. 

so you have allowed the port, but unless I'm missing something, you don;'t have an app listening on that port so it is still closed. allowed but closed is just as useless as open but blocked.

this command should show you all the listening ports on your system (don't panic, most of them are local-only connections)
```
netstat -ntlup
```

if the port you want is not listening, it won't work.

---

### Post by gdtw on 2010-09-24
My original problem turned out to be not related to the port opening. I did learn some interesting things along the way.

I do want to have ufw set up. However, i noticed that reboot renders ufw inactive. My question is: how do I keep ufw active after reboot?

thanks

---

### Post by perspectoff on 2010-09-24
> **gdtw said:**
> That sounds interesting...
theoretically as i understand, the whole point of a firewall is to deny everything with only certain exceptions..

Depends on how you set it up. You can block all incoming traffic while allowing all outgoing traffic, or vice versa. You can allow all traffic at certain times and allow only certain traffic at other times.

While clearly there is no traffic when the computer is off or no apps or services are actually running (i.e. no traffic = closed ports) the default setup of Ubuntu is to allow all traffic. There is no default firewall security at installation, until you set it up the way you like it.

---

### Post by endotherm on 2010-09-24
> **gdtw said:**
> My original problem turned out to be not related to the port opening. I did learn some interesting things along the way.

I do want to have ufw set up. However, i noticed that reboot renders ufw inactive. My question is: how do I keep ufw active after reboot?

thanks
what is leading you to believe that it is inactive? what process are you using to evaluate it;s status?

---

### Post by gdtw on 2010-09-24
> **endotherm said:**
> what is leading you to believe that it is inactive? what process are you using to evaluate it;s status?


yes - status.

---

### Post by endotherm on 2010-09-24
I've found a bug involving the use of other firewall config tools (firestarter/guarddog) causing this problem for gufw. do you have any of these installed?
[https://bugs.launchpad.net/ufw/+bug/404971](https://bugs.launchpad.net/ufw/+bug/404971)

---

### Post by scrooge_74 on 2010-09-24
> **gdtw said:**
> My original problem turned out to be not related to the port opening. I did learn some interesting things along the way.

I do want to have ufw set up. However, i noticed that reboot renders ufw inactive. My question is: how do I keep ufw active after reboot?

thanks

As a good friend always says to me: "read the manual"

Or in this case the config file /etc/ufw.conf

It says:

# Set to yes to start on boot. If setting this remotely, be sure to add a rule
# to allow your remote connection before starting ufw. Eg: 'ufw allow 22/tcp'
ENABLED=no


Also I'm no expert on firewalls, but sometimes ufw can't handle some configs, in those cases a go for firehol (but that is just me)

---

### Post by gdtw on 2010-09-24
> **scrooge_74 said:**
> As a good friend always says to me: "read the manual"

Or in this case the config file /etc/ufw.conf

It says:

# Set to yes to start on boot. If setting this remotely, be sure to add a rule
# to allow your remote connection before starting ufw. Eg: 'ufw allow 22/tcp'
ENABLED=no


Also I'm no expert on firewalls, but sometimes ufw can't handle some configs, in those cases a go for firehol (but that is just me)

i have no such file /etc/ufw.conf. should i just create one? or is it in a different location?

---

### Post by scrooge_74 on 2010-09-25
sorry is /etc/ufw/ufw.conf

---

