---
title: "How to check the keylogger in my Ubuntu system"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by angelating on 2009-02-19
Hi 

I am a new Ubuntu user after my computer (on window) had been hacked three times, through the use of keyloggers by the rival websites.

Last month, they tried to do it again. But I used Ubunto. I am not sure if my computer has been hacked again or not. The Ubuntu community in Thailand said I would be safe as far as I downed load the copyrighted registry.

But I read from the forum here, it seemed to me that keylogger can still intrude by computer. Can anyone tell me how I can check and protect my computer? 

Last time, they intruded me through the remote internet and put keyloggers to remember my email passwords. They still some info.

Please kindly advise.

best
angela ting

---

### Post by loell on 2009-02-19
linux key loggers needs to have a root (super user) access before they can monitor the keyboard port.  unless they don't gain that privilege they can't run a key logger. Yes, this doesn't answer your question, the right question would be more technical, "what utility would i use to monitor who accesses my keyboard port"?  but i tried searching around, i still can't find if there's such a tool.

the good thing is, if no one knows your password, they can't run a keylogger to find out your password.

---

### Post by amauk on 2009-02-19
depends what you mean by "keylogger"

1) Rogue application loaded on **your** machine that monitors keystrokes and reports anything interesting to a 3rd party

You are pretty much safe against these

You would need to manually install such an app
it couldn't install itself automatically
also, any such program would need root privileges to operate - again requiring you to manually grant such privileges

2) 3rd party logging your username & password credentials to a website

2a) There are a few dodgy sites out there that offer some service (Eg. image hosting, or something) that require you to supply your email address when registering

They take your login credentials and try them against your email account, in the hope that you use the same password for everything

Linux will not protect you against this, as it's happening outside of your control

2b) someone monitoring your network traffic (Eg. over unsecured wireless) can see any login credentials supplied by you as they travel across the network

Again, Linux will not protect you against this, as it's happening outside of your control

however, most sensitive sites (like online banking) will provide encrypted channels meaning anyone monitoring your network can still "see" communication, but can't decipher what it is

Ensure any sensitive sites you log into, use HTTP**S** rather than plain HTTP

---

### Post by HavocXphere on 2009-02-19
It's unlikely that they managed to hack your ubuntu box....but if you really feel you need extra protection:

Intrusion detection:
[http://en.wikipedia.org/wiki/Open_Source_Tripwire](http://en.wikipedia.org/wiki/Open_Source_Tripwire)

Detecting rootkits:
[http://en.wikipedia.org/wiki/Chkrootkit](http://en.wikipedia.org/wiki/Chkrootkit)

I don't know a specific check for keyloggers on linux. Windows yes, but not linux.

---

### Post by binbash on 2009-02-19
you can use rkhunter for detecting rootkits also.

---

### Post by glotz on 2009-02-19
[QUOTE=angelating]The Ubuntu community in Thailand said I would be safe as far as I downed load the copyrighted registry.[/QUOTE]Anybody know what this means? Sounds real strange to me.

---

### Post by Sir Jasper on 2009-02-19
Hi all,

A supplementary question follows:

It seems almost impossible for infections to get into Ubuntu; but if that should somehow happen, would installing the Ubuntu firewall help
in blocking outgoing contact - if appropriately configured?

My regards

---

### Post by loell on 2009-02-19
> **glotz said:**
> Anybody know what this means? Sounds real strange to me.

there is the Thai loco team, maybe he's referring to them. not sure about "copyrighted registry" though.

---

### Post by glotz on 2009-02-19
Yeah. Just because, if I wanted to have a keylogger on somebody's machine that's new to Ubuntu, the easiest way by far would be to use social engineering to make them install my trojan.

---

### Post by angelating on 2009-03-26
It's me again.

Sorry I mis-spelled the word. What I mean "the copyrighted registry" should be "repository".

I still don't know how to check if the hackers are successful in tricking me or not. But a few weeks ago, I used the Window system and found that they are trying to scan my port. Also, they called my telephone number, the same line that is used to connect the internet. This number is confidential and I told only to 2-3 friends.

The Thai Ubuntu users seem to be trust in it a lot. Some of them do not even install firewall.

About password, I used different passwords and each of them have more than 10 characters. They also include the capital letters, numbers and special letters.

Do you think if I should re-format the system again?

---

### Post by MrWES on 2009-03-26
Are you behind a router? If so, are you forwarding any ports?

---

### Post by angelating on 2009-03-26
I did nothing with the router. I am only the user, do not know anything about technique. So I did not forward the port. But maybe it has already set from the manufacturer.

---

### Post by jakupl on 2009-03-26
> **angelating said:**
> 
The Thai Ubuntu users seem to be trust in it a lot. Some of them do not even install firewall.


You don't need a firewall on ubuntu. Ubuntu comes with iptables, but by default nothing is engaged. This is reasonable as a default Ubuntu install opens zero ports to the outside world, so a firewall is redundant.

check bodhi.zazens great post entitled  [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by perspectoff on 2009-05-02
> **jakupl said:**
> You don't need a firewall on Ubuntu. Ubuntu comes with iptables, but by default nothing is engaged. This is reasonable as a default Ubuntu install opens zero ports to the outside world, so a firewall is redundant.

check bodhi.zazens great post entitled  [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")

That's not correct. All ports are open by default on Ubuntu. Otherwise nothing would work. "Nothing is engaged" actually means all ports are open.

When you start a firewall front-end (UFW, Guarddog, Firestarter), it closes most of the ports by manipulating iptables. You can then choose which ports to open or close.

But if you don't run a firewall, all your ports will remain open.

---

### Post by tom56 on 2009-05-02
> **perspectoff said:**
> That's not correct. All ports are open by default on Ubuntu. Otherwise nothing would work. "Nothing is engaged" actually means all ports are open.

When you start a firewall front-end (UFW, Guarddog, Firestarter), it closes most of the ports by manipulating iptables. You can then choose which ports to open or close.

But if you don't run a firewall, all your ports will remain open.

But if nothing is listening on those ports it doesn't matter if they are "open" or not.

---

### Post by jakupl on 2009-05-03
You don't need a firewall front-end.
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[QUOTE="bodhi.zazen"]By default, Ubuntu includes a firewall, iptables, but by default nothing is engaged. This is reasonable as a default Ubuntu install opens zero ports to the outside world, so a firewall is redundant. However, installing "server software" will cause ports to open, so some people like to use a firewall as a catch-all layer to find mistakes in their configuration.
[/QUOTE]

---

### Post by hashi856 on 2009-05-03
> **perspectoff said:**
> That's not correct. All ports are open by default on Ubuntu. Otherwise nothing would work. "Nothing is engaged" actually means all ports are open.

When you start a firewall front-end (UFW, Guarddog, Firestarter), it closes most of the ports by manipulating iptables. You can then choose which ports to open or close.

But if you don't run a firewall, all your ports will remain open.

OK Stupid question time. I know next to nothing about computers. What exactly is a port? Sorry.

---

