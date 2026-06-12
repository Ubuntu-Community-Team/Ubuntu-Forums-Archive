---
title: "Firewall is confusing me, can we make this clear?"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by dubhear on 2009-05-02
So, I just read I really don't need firewall at all?

**Can this be true?**

My story is that; I about a year ago turned from windows to ubuntu.
I am just amazed how much better it is than i've been led to believe.
So as a windows user i thought i need some kind of firewall, and now **i'm so confused** about how i can get firewall that is reliable and i can monitor it with my own eyes, *and how this all works*. I downloaded few programs and found out that firestarter is least confusing. I can block ip's and ports if i want and see when my system is getting a hit from network...

Now i'm fed up with closing all ports and so on. i can't do this alone. i need some REAL support to get this all clear, how i can get best possible firewall. I want to go through this step by step now, as clearly as possible. i'm not stupid, i just want to be sure/safe as much as possible.

First question: **What happens when I remove firestarter now, after I used it?**

---

### Post by tom56 on 2009-05-02
Firestarter helps you to close ports. The reason you don't need a firewall is because no ports are open to begin with. The only reason ports might be open is if you have installed some server software like a web server of mail server. By default, all the ports are closed. You can check how vulnerable you are by using a port scanner like Shields Up ([https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)).

With regard to the question at the end of your post, if you remove Firestarter any changes you made with it will remain.

---

### Post by dubhear on 2009-05-02
thank you for your kindness, appreciate it.

**so this "firestarter in reality is opening these ports? so after i installed it... it made this "not open ports by default" rule overidden?**
now i'm going to find out, on my own, more about how this firestarter really works,

maybe i will reinstall ubuntu now, so it won't get any more confusing with this firestarter thing... this *firestarter "firewall"* feels like some1 slapped my face

---

### Post by The Cog on 2009-05-02
tom56 is right. Just to add support, here is my explanation. A firewall can prevent other people on the internet from connecting to your PC (and then maybe doing Bad Things). But with an Ubuntu default install, it is not listening for incoming connections on any ports at all. All ports are closed and it is impossible to connect to the PC because it's not listening. So you don't need a firewall. It has nothing to do.

If you insall a service like a webserver, then now your PC will be listening for incoming connections. If you only want certain IP addresses to be able to connect to that service, then you may want to install a firewall and configure it to only allow connections from the addresses you specify. But without that list of preferred addresses, there is still no point installing a firewall because you would just have to configure it to allow people to connect to that service, so there is nothing for it to do.

In short, unless you have a very specific requirement, you don't need a firewall.

The reason everybody from WindowsWorld automatically installs a firewall is that windows PCs are (by default) listening for incoming connectons on lots of different ports, and the easiedt way to prevent them from being abused is to just block them all behind a firewall, like plastering over the cracks.

---

### Post by tom56 on 2009-05-02
> **dubhear said:**
> **so this "firestarter in reality is opening these ports? so after i installed it... it made this "not open ports by default" rule overidden?**

No, but it depends on what you told it to do. I expect that it doesn't make any changes until you tell it to, but from what I recall there is a first run wizard and you may have made changes then. The best thing to do is go to the link above and run the "All Service Ports" test. If you pass then you haven't got any problems.

---

### Post by iponeverything on 2009-05-02
> **dubhear said:**
> thank you for your kindness, appreciate it.

**so this "firestarter in reality is opening these ports? so after i installed it... it made this "not open ports by default" rule overidden?**

If you open a port, but you don't have anything listening on the port, it's a bit like opening a door and finding a wall behind it.
> 
now i'm going to find out, on my own, more about how this firestarter really works,

maybe i will reinstall ubuntu now, so it won't get any more confusing with this firestarter thing... this *firestarter "firewall"* feels like some1 slapped my face

:) Firestarter is not a firewall, it is just frontend to iptables - a kernel level packet filter. If your uninstall it make sure you do "sudo apt-get remove --pruge firestarter" so that old rules you put in will get removed and won't come back to haunt you later when install a service and can't figure out it won't work.

---

### Post by dubhear on 2009-05-02
Ping Reply: RECEIVED (FAILED) &#8212; Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.

this is the result that failed, could this be because of firestarter?
and another thing.. seems like all my three number ports are configured as "stealth"

i'm green as hell, much like hulk now. ARGH

Looks like i'm geting somewhere now, every post in this thread was worth a gold to me, so many thing are now much easier to understand. but still i like to get to the bottom of this, again, as much as possible. i know it can't get much better than this but, what do we have to lose?!? really this all is something everyone like me should know. special thanks for the purge command line.

---

### Post by The Cog on 2009-05-03
Do you use a router to connect to the internet? If you do, then remember that it is your router, not your PC that has a public IP address, and it is your router that is being scanned by shields up or whatever it is you are using to perform the scan.

You can of course configure the router to pass some chosen ports on to the PC.

---

### Post by alphacrucis2 on 2009-05-03
> **iponeverything said:**
> If you open a port, but you don't have anything listening on the port, it's a bit like opening a door and finding a wall behind it.


I isn't exactly the same. If nothing is listening then the OS responds to the incoming SYN packet effectively saying connection refused. 

For example I have no SSHD running on this laptop so:

```
me@laptop:~$ ssh localhost
\ssh: connect to host localhost port 22: Connection refused
me@laptop:~$

```

A firewall can be configured to treat the incoming packet quite differently, for example the incoming SYN packet can simply be dropped. This leaves the sender not knowing if it succeeded in reaching the destination address. A subtle difference,

---

### Post by alphacrucis2 on 2009-05-03
> **The Cog said:**
> Do you use a router to connect to the internet? If you do, then remember that it is your router, not your PC that has a public IP address, and it is your router that is being scanned by shields up or whatever it is you are using to perform the scan.

You can of course configure the router to pass some chosen ports on to the PC.

That's correct if the PC has a private RFC address and the router is applying NAT. It is still possible to have a router and a public address on your PC such that both have a public address and no NAT occurs. This isn't common for a home internet setup though.

---

### Post by presence1960 on 2009-05-03
> **dubhear said:**
> So, I just read I really don't need firewall at all?

**Can this be true?**

My story is that; I about a year ago turned from windows to ubuntu.
I am just amazed how much better it is than i've been led to believe.
So as a windows user i thought i need some kind of firewall, and now **i'm so confused** about how i can get firewall that is reliable and i can monitor it with my own eyes, *and how this all works*. I downloaded few programs and found out that firestarter is least confusing. I can block ip's and ports if i want and see when my system is getting a hit from network...

Now i'm fed up with closing all ports and so on. i can't do this alone. i need some REAL support to get this all clear, how i can get best possible firewall. I want to go through this step by step now, as clearly as possible. i'm not stupid, i just want to be sure/safe as much as possible.

First question: **What happens when I remove firestarter now, after I used it?**

read this please, very informative & eye opening: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by tacomodo on 2009-05-03
> **alphacrucis2 said:**
> I isn't exactly the same. If nothing is listening then the OS responds to the incoming SYN packet effectively saying connection refused. 

For example I have no SSHD running on this laptop so:

```
me@laptop:~$ ssh localhost
\ssh: connect to host localhost port 22: Connection refused
me@laptop:~$

```

A firewall can be configured to treat the incoming packet quite differently, for example the incoming SYN packet can simply be dropped. This leaves the sender not knowing if it succeeded in reaching the destination address. A subtle difference,
I am wondering, if enough hosts were to probe my ports, say it was 10 million people doing it at once or something, wouldn't that sort of leave my computer totally bogged down if I were to respond "Connection refused" to each one?
Perhaps in theory a firewall would be a good idea so all these requests were just dropped?

Or am I just being silly? :p

---

### Post by The Cog on 2009-05-04
I don't think the CPU power involved in sending a connection refused message is significantly greater than just dropping the packet. It still has to be received and examined to an extend. And if you drop the packet, the sender will probably send a retransmission a few times before giving up.

Under DDOS conditions and with an ADSL line where your upload speed is significantly less than your download speed, all the connection refused messages could flood your link earlier than all the connect requests would if they were ignored. But I don't think that slim possibility alone is enough to change the way you set up your computer. Unless you are involved in something that makes a DDOS attack rather more likely than usual.

---

### Post by dubhear on 2009-05-05
one last question!

there is no right answer to this one: but would like to know **your opinion which is the best program/command to observe these ports** that are(or are not) connected to my ISP (internet service provider)?

firestarter observes these ports, I still have it and still use it. but i don't like to mess with the settings, just yet.

Can you please tell me your opinion? I really want the best to configure my ports to my program needs.

---

### Post by Tews on 2009-05-05
I simply enable UFW to default deny and dont worry about it.  

```

sudo ufw enable
sudo ufw default deny
```

also, if you are behind a router its like having a hardware firewall....

---

### Post by dubhear on 2009-05-06
> *-desktop:~$ ufw --help

Usage: ufw COMMAND

Commands:
  enable			Enables the firewall
  disable			Disables the firewall
  default ARG			set default policy to ALLOW or DENY
  logging ARG			set logging to ON or OFF
  allow|deny RULE		allow or deny RULE
  delete allow|deny RULE	delete the allow/deny RULE
  status			show firewall status
  version			display version information

*-desktop:~$ sudo ufw enable
[sudo] password for *: 
Firewall started and enabled on system startup
*-desktop:~$ sudo ufw default deny
Default policy changed to 'deny'
(be sure to update your rules accordingly)

* **is my user name**

no change in [https://www.grc.com/](https://www.grc.com/) port scan still green(=stealth)

---

### Post by Mortus Pryde on 2009-05-06
> **dubhear said:**
> * **is my user name**

no change in [https://www.grc.com/](https://www.grc.com/) port scan still green(=stealth)

This is as it should be. By running the scanner you have told grc you are indeed there, it then probes the ports on your computer and after recieving no response declares the port stealthed. To a roaming port scanner it would effectively look like no computer at all is connected at that IP address and move on.

Basic Port States: 

Open - The computer responds that its there and awaiting a connection.
Closed - The computer responds that its there and not excepting connections.
Stealthed - The computer does not respond at all.

Obviously there was a time when I was very paraniod about my computers security running Windows. Though after a time I found sense, a good router and antivirus is for the most part all you need for good security, have not had a major problem since the Blaster Worm was big.

---

### Post by Dex73 on 2009-05-07
I'm a little paranoid so I like having a little protection. Probably not necessary.

---

