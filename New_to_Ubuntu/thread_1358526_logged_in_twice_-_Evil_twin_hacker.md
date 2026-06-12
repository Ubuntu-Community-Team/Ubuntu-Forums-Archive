---
title: "logged in twice - Evil twin hacker?"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Baffled Lemming on 2009-12-18
Hi Pals,
 
 I have a problem you may be able to help me with.  After noticing hacker activity--telnet attempts, funny IPs and unusual ports bouncing off Firestarter-I looked into securing my system and noticed something very worrying.  
 
 I am logged in twice.  When I put in users at the command line I get "brad brad".
 
 So I cat-ed /etc/passwd and found this line in there:
 
 brad:1000:1000:Brad,,,:/home/brad:/bin/bash
 
 As I understand it this is the users and group setting and 1000 is the default number assigned to users.  But you'll note that the first brad is lower case and the second one is upper case.  Could this be a shadow user?  
 
OS is 9.04.  

 How do I edit this ghost user out without wiping out my system? 
 
 Thanks to you experts in advance for your advice.
 
 Baffled Lemming

:)

---

### Post by jimmy the saint on 2009-12-18
[http://lmgtfy.com/?q=ubuntu+logged+in+twice](http://lmgtfy.com/?q=ubuntu+logged+in+twice)

There you go

---

### Post by CharlesA on 2009-12-18
/etc/passwd is fine. the "Brad,,," is the name of the user.

---

### Post by t0p on 2009-12-18
You don't have a problem with your /etc/passwd.  It says "brad"   because that's your username.  It says "Brad" because you told it that's your name when you created the user account (probably during installation).

You thought you might be suffering an "evil twin" attack.  An evil twin attack is when a would-be attacker sets up a rogue wireless AP to impersonate your usual AP, in the hope that you'll use the rogue AP to connect to the internet and the attacker can grab passwords, personal info etc..  That is not what you have described at all. But in any case, I can't see anything to worry about in what you've shown us.

You mentioned seeing telnet sessions that you didn't start.  Where did you see this?  Was it a telnet client on your computer accessing a remote machine, or was it a remote telnet client trying to access your computer?  Do you have a telnet server installed?  What IP address was the telnet traffic coming from/going to?  Please post the log of the session, or whatever you've got on it.

---

### Post by atomizer on 2009-12-18
> **jimmy the saint said:**
> [http://lmgtfy.com/?q=ubuntu+logged+in+twice](http://lmgtfy.com/?q=ubuntu+logged+in+twice)

There you go


OMG I thought it was a real anwser and clicked on the link.......

---

### Post by fromthehill on 2009-12-18
> **atomizer said:**
> OMG I thought it was a real anwser and clicked on the link.......
actually, the first result IS the answer :)

the chance a hacker tries to break into your pc is close to zero

---

### Post by Baffled Lemming on 2009-12-18
Thanks for all your input.   But to clarify, when I type &quot;users&quot; into a command line interface, I get this:    brad@Dellhome:~/school$users  brad brad    Is that what you get?     In terms of the intruder alert, it started with this li'l number:     Time:Dec 11 22:19:51 Direction: Unknown In: Out:ppp0 Port:44444 Source:10.101.63.212 Destination:24.XXX.XXX.XXX Length:65535     Time:Dec 11 22:21:48 Direction: Unknown In: Out:ppp0 Port:80 Source:10.101.63.212 Destination:24.XXX.XXX.XXX Length:44 TOS:0x00     I removed the ip address so as not to invite retaliation only later to discover it was Tiger Wood's wife, keeping her options open and checking on me to see if I'm still single.     This is where we are now, from an nmap scan a minute ago.     Initiating SYN Stealth Scan at 15:54 Scanning localhost (127.0.0.1) [1000 ports]  Discovered open port 25/tcp on 127.0.0.1  Discovered open port 631/tcp on 127.0.0.1  Discovered open port 9103/tcp on 127.0.0.1  Completed SYN Stealth Scan at 15:54, 0.36s elapsed (1000 total ports)     Presumably port 25 is smtp, I've disabled port 23--the telnet port-- and these other guys, I don't know what they are.  I didn't save that session that regsitered telnet outgoing as I was too busy pulling the cat 5 cable out of the computer.    It's quite possible that me seeing telnet coming up on firestarter was me banging my head against the inside of the firewall during an NMAP scan--dont' know if Nmap scans telnet or not.      All help and suggestions much appreciated.

---

### Post by Baffled Lemming on 2009-12-18
Apologies for the formatting mess.

---

### Post by fromthehill on 2009-12-18
port 25=SMTP
port 631=Internet Printing Protocol.
port 9103= bacula-sd, Bacula Storage Daemon, Silverfall, Spliter Cell Chaos Theory, Supreme Commander, HP JetDirect card
port 44444:not a lot information. used by the backdoor trojan 'prosiak'. but it doesn't work under linux. also found this:
"This port range can be configured on Linux by using the "sysctl" command and the "net.ipv4.ip_local_port_range" variable."

---

### Post by Mornedhel on 2009-12-18
"users" returns as many entries as there are currently users logged in. You are logged in twice. Once for your graphical session, once for the terminal you're typing users in. Try and open more terminals, then run users again. There should be one brad per open terminal, plus the one for the graphical session.

---

### Post by Extract_Here on 2009-12-18
> **Mornedhel said:**
> "users" returns as many entries as there are currently users logged in. You are logged in twice. Once for your graphical session, once for the terminal you're typing users in. Try and open more terminals, then run users again. There should be one brad per open terminal, plus the one for the graphical session.
sound like this one is covered

---

### Post by Baffled Lemming on 2009-12-19
Thanks to everyone for the helpful.  Input this one is solved!

---

### Post by Baffled Lemming on 2009-12-19
Um Sorry to be stupid here, but how do I change the topic from Ubuntu to solved?  Also, am going to be out for the WE so if one of you guys can just do it I would be most appreciative.

---

### Post by lotharmat on 2009-12-19
Thread tools (at the top of the page)

---

