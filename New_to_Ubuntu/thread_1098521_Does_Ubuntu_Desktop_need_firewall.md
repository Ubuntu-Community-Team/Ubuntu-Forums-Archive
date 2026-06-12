---
title: "Does Ubuntu Desktop need firewall?"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by hyapadi on 2009-03-17
I'm migrating from Windows Vista to Ubuntu.

In Windows Vista, I was using Kaspersky Internet Security ( av + firewall ) to protect my computer.

I'm looking for comparable security on my Ubuntu desktop.

What I know about firewall in Linux, is that every linux already have built in firewall called linux iptables. What can be installed is the front end to configure it easily. Is that true?

How about the default firewall setting of Ubuntu? is it quite safe for desktop? ( I don't expect to have server-like security, as long as it is adequate for desktop. )

If it does need firewall. I'm looking for automated solution ( or at least the simplest solution ) like what Kaspersky ofters ( no need or need less interaction from me ).

Thanks

---

### Post by Dynaflow on 2009-03-17
Here's (hopefully) everything you want to know: [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

---

### Post by skymera on 2009-03-17
Ubuntu has an inbuilt firewall called iptables. As you said
it does not need any configuration UNLESS you need to allow people to connect to your box.

Firestarter is a GUI to IPtables.
UFW is a simple command line app.

---

### Post by isecore on 2009-03-17
Ubuntu generally does not need either firewall or antivirus. This depends muchly on what services you install and what you use your computer for.

In a standard installation Ubuntu has no services that listen for connections, and thus there's nowhere to "latch on" for an attacker. This of course might change if you install services that listen outwards or change configurations to start listening. But in a standard installation I would consider it mostly redundant.

If you're behind a NAT-gateway (aka "router" in common tongue) you most definitely do not need a firewall since the NAT-gateway essentially acts as one.

So, short answer: no. Long answer: depends on your setup, what you're doing and so on.

IPtables is built in, but it's fairly difficult to configure. There are nice front-ends for it though, I'd suggest firestarter if you want to use it. As for antivirus... well, while Linux-viruses are theoretically possible there are none in the wild, so it would be quite useless.

---

### Post by carml on 2009-03-17
A suggestion from one person who was in your same condition some months ago: forget the need of an antivirus on a Gnu/Linux distribution.
On Ubuntu you can install any antivirus if you wish,but they scan your PC looking for windows aimed viruses.:)

---

### Post by hyper_ch on 2009-03-17
(1) Linux has a firewall called iptables

(2) by default iptables has no rules, that means nothing gets filtered out and everything is accepted

(3) the behaviour in (2) is good as you normally don't have any services listening - unlike Windows where there are tons and tons of stuff listening

(4) firestarter is nothing but a configuration tool for iptables. The ubuntu dev think it's outdated and hence

(5) rather recommend to make use of UFW

(6) in most cases you don't need a firewall

(7) and in most cases you are behind a NAT router. Disable there UPnP and just let come in what is necessary - again in most cases there's no need to alter iptables.

---

### Post by theozzlives on 2009-03-17
All this "we're safe" and "there's no need" makes me wonder if the Linux community is setting itself up for a 9-11 disaster.

---

### Post by hyper_ch on 2009-03-17
> **theozzlives said:**
>  for a 9-11 disaster.

what's a 9-11 disaster?

---

### Post by t0p on 2009-03-17
> **theozzlives said:**
> All this "we're safe" and "there's no need" makes me wonder if the Linux community is setting itself up for a 9-11 disaster.

 I doubt anyone is going to crash airliners into your computer. And if someone does, there ain't no firewall available that's gonna help...

---

### Post by presence1960 on 2009-03-17
Read this : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

should answer your questions.

---

### Post by presence1960 on 2009-03-17
> **t0p said:**
> I doubt anyone is going to crash airliners into your computer. And if someone does, there ain't no firewall available that's gonna help...

No offense to theozzlives but that had me rofl.

---

### Post by Dynaflow on 2009-03-17
> **t0p said:**
> I doubt anyone is going to crash airliners into your computer. And if someone does, there ain't no firewall available that's gonna help...

No doubt they'll go for the Macs first, and they'll probably be flying Linux boxes.  

"Really? You can't put any version of Firefox higher than 2.0.0.20 on Panther if it's running on PowerPC?  Tally ho!"

---

### Post by hyapadi on 2009-03-17
I thank you guys for your quick and informative answers.

From what I read, I conclude that there is no need for firewall unless for active listening port/application.

My next question is, how could I know the running application that listen to certain port? :D

---

### Post by jms1989 on 2009-03-17
> **t0p said:**
> I doubt anyone is going to crash airliners into your computer. And if someone does, there ain't no firewall available that's gonna help...

Heh that's funny.

I agree with the folks above. You really don't need a firewall unless you are going to use linux as your firewall/router (somebody needs to make a guide on that). I find iptables to cause more trouble than its worth when running a webserver on my lan.

Just my two cents.

---

### Post by The Cog on 2009-03-17
> From what I read, I conclude that there is no need for firewall unless for active listening port/application.
Even then it's dubious if a firewall is of any use. Do you have a list of IP addresses you wanat to allow to connect, of a list of addresses you want to bar? If the service is to be accessible to all comers, there is still no use for a firewall.
> My next question is, how could I know the running application that listen to certain port?
```
sudo netstat -plnt
``` will tell you which TCP ports are listening ane which app opened them.

---

### Post by hyapadi on 2009-03-17
With all my common software up and running, I have these connections active ( from sudo netstat -plnt ):
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      7200/cupsd      
tcp        0      0 0.0.0.0:13468           0.0.0.0:*               LISTEN      8027/skype.real 

Is there any thing that can be secured?

I don't use printer for now and is that cupsd open for public or just for internal use? So is it safe?

Thanks :D

---

### Post by brian_p on 2009-03-17
> **hyapadi said:**
> 

I don't use printer for now and is that cupsd open for public or just for internal use? So is it safe?

The default installation of cupsd will only respond to requests from the machine you are sitting at. You can verify this by looking in its configuration file. Skilled code readers can check it does what it says it does.

If skype is listening it is presumably because you want to receive telephone calls. Because it is a closed source application you are totally reliant upon the skype developers to keep it secure.

---

### Post by hyapadi on 2009-03-17
@brian
as per your explaination, I think I already get the "secure level" that I desire.

Ubuntu rocks!

Thanks guys for the responses.

Case close :D

---

