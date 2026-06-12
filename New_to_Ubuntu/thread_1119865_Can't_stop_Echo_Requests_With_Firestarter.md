---
title: "Can't stop Echo Requests With Firestarter"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by zoey_s on 2009-04-08
Shields Up shows port 22 as open and vulnerable.  I have Firestarter ICMP Filtering set for NO response to echo requests (no ping or pong), but port 22 responds to Shields Up pings anyway.  Is there a way to stealth port 22?  I can figure out Firestarter better than other Linux Firewall guis, but it won't do what I want it to.  I tried gufw and couldn't figure out how to manage it.

Thanks, zoey](*,)

---

### Post by Nostalos on 2009-04-08
ICMP Filtering has nothing to do with whether or not port 22 will show up in any kind of scan.   If you want to see if port 22 is open, you don't have to ping it first,  you just open it.

If you don't want it to show up, then don't allow access to port 22 or at least only allow it to be accessed from a limited set of IP addresses.

---

### Post by zoey_s on 2009-04-08
> **Nostalos said:**
> ICMP Filtering has nothing to do with whether or not port 22 will show up in any kind of scan.   If you want to see if port 22 is open, you don't have to ping it first,  you just open it.

If you don't want it to show up, then don't allow access to port 22 or at least only allow it to be accessed from a limited set of IP addresses.

Ok, so how do I do that?

               Thanks, zoey

---

### Post by hovzio on 2009-04-08
Are you running an ssh server, 22 is its default port?
Are you behind a router/firewall?

EDIT: If your pc is behind a router with firewall you will have to check it too for open ports, in this case firestarter has nothing to do with your open port. Check your gateway. (do you know how this is done?)

---

### Post by ibuclaw on 2009-04-08
To block ICMP echo requests, you may be forced to use iptables directly:
```
sudo iptables -A INPUT -p icmp -j DROP
```
Bare in mind that will only last as long as your computer is turned on though.

But if you are behind a router, you shouldn't need this as the routers job is to **always drop packets**. (unless you want protection from other computers inside your LAN ???)

Also, if you ever port scan your computer, always always always do it from outside your network. You get a valid result that way.

Regards
Iain

---

### Post by Nostalos on 2009-04-08
I personally am not familiar with firestarter so can't give you a step by step.  However,  there should be a configuration in firestarter that allows all to ssh which could be replaced with individual ip addresses or networks.

Or

edit modify your hosts.allow and hosts.deny to allow only specific addresses

> 
#/etc/hosts.deny
ALL:ALL


> 
#/etc/hosts.allow
ALL:localhost
sshd:ipaddr1
sshd:ipaddr2


this will deny all hosts via tcpwrappers (on apps compiled with tcpwrap support) other than what is explicitly specified.   In this case localhost can use any application.  ippaddr1 and ipaddr2 are the only things allowed besides localhost to ssh.


Do note that this will STILL show up in a port scan.   But anything besides the ip's listed will be immediatly disconnected.

---

### Post by zoey_s on 2009-04-08
Thanks, everyone.  I should probably tell you that you are posting to a 71 year old lady who discovered computers about 6 years ago and Linux about a year after that, so not only do I not always understand the answers that I get to my inquiries, I don't even understand the questions sometimes, but I am having a lot of fun just the same.  I would never make it without all of the very helpful people on forums and the linux articles on the net.

As to the router, we have one that also runs wireless and I don't know about the firewall, nor do I know how to check that.

I am running ssh using port 22, which is the only one that answers Shield's Up pings.

Thanks Again, zoey

---

### Post by hovzio on 2009-04-08
> **zoey_s said:**
> Thanks, everyone.  I should probably tell you that you are posting to a 71 year old lady who discovered computers about 6 years ago and Linux about a year after that, so not only do I not always understand the answers that I get to my inquiries, I don't even understand the questions sometimes, but I am having a lot of fun just the same.  I would never make it without all of the very helpful people on forums and the linux articles on the net.

As to the router, we have one that also runs wireless and I don't know about the firewall, nor do I know how to check that.

I am running ssh using port 22, which is the only one that answers Shield's Up pings.

Thanks Again, zoey

If you are running a server on port 22, then its open, nothing you can really do. Google port knocking, I've heard this can ghelp tidy things up. Like I said if you want to have the ssh server available, it has to be listening.. somewhere. In your case port 22.

---

### Post by Nostalos on 2009-04-08
> **zoey_s said:**
> Thanks, everyone.  I should probably tell you that you are posting to a 71 year old lady who discovered computers about 6 years ago and Linux about a year after that, so not only do I not always understand the answers that I get to my inquiries, I don't even understand the questions sometimes, but I am having a lot of fun just the same.  I would never make it without all of the very helpful people on forums and the linux articles on the net.

As to the router, we have one that also runs wireless and I don't know about the firewall, nor do I know how to check that.

I am running ssh using port 22, which is the only one that answers Shield's Up pings.

Thanks Again, zoey

/salute

Nothing but respect for you for learning.    If you have a router, more than likely you are picking up the router on shields up and not your ubuntu machine.  Especially if you didnt install openssh-server as it doesnt install by default on desktop.  (educated guess there as I have no real clue to your setup)

In which case, if you don't need it then turn it off.  If you do need it, just make sure your password is for lack of a better term secure.  i.e.  your username and password are not the same etc.

Security is a tradeoff between risk and usability.  And other than human error on things such as passwords SSH is pretty low risk.

---

### Post by Soul-Sing on 2009-11-08
[COLOR="Red"]using gufw, not firestarter....[/COLOR]:
$```
 sudo nano /etc/ufw/before.rules
```
Replace:
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
by:
#-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
Save file and exit.

Restart (g)ufw with:
```
sudo /etc/init.d/ufw restart
```

---

