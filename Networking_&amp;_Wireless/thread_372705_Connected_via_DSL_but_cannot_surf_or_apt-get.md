---
title: "Connected via DSL but cannot surf or apt-get"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by samadams on 2007-02-28
Okay here's the skinny:  After much (VERY MUCH) trouble and a great big help from Alcatel, I've managed to get my Speedtouch USB (green stingray) modem dialed in via VPN.  Unfortunately I have to issue commands manually each session to do so, so a little help in how I should include them in my logon script would be appreciated.

But here's the real problem.  After successfully connecting to my ISP, I can't do ANYTHING online.  NOTHING.  No ping, no apt-get, no Firefox, no Evolution, NOTHING.  Why?  How do I fix this?

In case you were wondering, I'm connected via wired USB on an Alcatel revision 0 DSL modem.  I do not have a router.  I do not, nor will I pay for a static IP address. (so please don't suggest that if it comes down to it - I will trash Ubuntu before I go through that expense)  If you need output from any commands or log files to get a grip on what's happening - let me know.  AND MOST IMPORTANTLY, while I fancy myself somewhat as computer savvy - I am a 'just fell of the turnip truck' NEWBEE when it comes to  Linux and Ubuntu.  I know what a terminal window is and where the log files are.  I can make myself 'root' and can navigate a directory, but I am not familiar with all of the Linux terminology, so please be VERY specific and hold the jargon and slang.  Thanks.  (really, complete sentences help here the most, trying to read other topics I can see that most people here, don't know what a sentence is.)

I HAVE searched and searched and hunted for a solution in other topics to this, all to no avail.  If you know or have the link to a thread that fixes this problem - just give me the link and I'll go away like a happy little camper.

Thanks in advance and I appreciate any assistance anyone can give.

---

### Post by Floppyjoe on 2007-02-28
Could you explain what steps you took to get connected. How do you know you are connected?
When you tried to ping did you just try to ping domain names like [www.ubuntuforums.org](www.ubuntuforums.org) or did you try to ping IP addresses such as 82.211.81.186 as well?

---

### Post by samadams on 2007-03-02
I followed the steps in the howto on connecting an alcatel USB modem.  This thread here will explain everything done so far except the last part.  [http://ubuntuforums.org/showthread.php?t=299327](http://ubuntuforums.org/showthread.php?t=299327)
 
To finally get dialed in I sought help from the Alcatel Mailing List.  After much reporting of various values back and forth, I was successfully instructed to enter the follwing commands and replug my modem in.
 
rmmod speedtch
modprobe speedtch dl_512_first=1
 
(It's this last command I'd like to automate into my login script if possible)
 
This worked, the modem lights blinked appropriately and my networking tools tell me I am connected and transmitting and receiving to my isp.  But I can't do anything.
 
As for Ping, I've only tried namespaces.  I'll try that particular IP address you referenced.  If you have others for me to try I'll be glad to do so.  I also tried to use the tool to give info on a namespace (Ip address, registered to, etc. - kinda like Whois but a little different)  It doesn't work either.  Whenever I try either tool, I get an immediate response that the domain could not be located.  There is NO time delay while the modem attempts to ping.
 
Also, the network adapter is set to loopback and it won't let me change it.  Could this be part of the problem?
 
Thanks

---

### Post by Bert the Button on 2007-03-04
Hello there!  I've just managed to connect for the first time under linux after the same sort of symptoms as yourself.  My error was in the VPI and VCI settings.  These are displayed as **0.00** in the tuts for you to edit.  After reading all the lit that came with the modem mine turned out to be **0.38**, and absolutely *nothing* to do with the modem firmware version. (what a complete windows muppet I am...)

Hope this helps  :)

---

### Post by samadams on 2007-03-05
Thanks, but my VPI/VCI settings ARE correct (mine is 8.35).  But you noted that the logs will tell you your IP address and that of your ISP.  Mine don't as far as I can tell.  Is there a particular log file you are referring to?

---

### Post by Floppyjoe on 2007-03-05
> **samadams said:**
> As for Ping, I've only tried namespaces.  I'll try that particular IP address you referenced.  If you have others for me to try I'll be glad to do so.  I also tried to use the tool to give info on a namespace (Ip address, registered to, etc. - kinda like Whois but a little different)  It doesn't work either.  Whenever I try either tool, I get an immediate response that the domain could not be located.  There is NO time delay while the modem attempts to ping.
 
So did pinging an IP address work?If it does than it is probably a DNS problem.

You could probably add the following line into the /etc/modules file to automate it:
```
speedtch dl_512_first=1
```

---

### Post by samadams on 2007-03-06
Nope, pinging IP addresses did not work.  So I guess that leaves me with DNS - what now?

p.s. - thanks for the tip on etc/modules

---

### Post by samadams on 2007-03-07
Okay, first the /etc/modules method did NOT work as far as automating the "modprobe speedtch dl_512_first=1."

I also tried putting it in my dial script both inside and outside the do/while loop.  Nada.  (though I'm realizing now, possible just adding "dl_512_first=1" to the "call speedtch" command in the do/while loop might do the trick no?)

Okay - on to more pressing matters.  Still no ping.  syslog tells me the adsl line is up and synchronized (I thought the A in ADSL stood for asynchronous?)  Anyway.  It gives me an up and down stream, but no IP address or ISP address as purported in an earlier post.  Maybe in another log perhaps?

What I have discovered is that the howto on the Speedtouch at the very end has me do three things.  1)Place 'dial' in a certain folder and create a symbolic link to it (whatever that means)  2) create another symbolic link to another file. 3) create yet one last symbolic link in /etc to a file called resolv.conf located in /etc/ppp.  This last one is supposed to FIX etc/resolv.conf to properly resolve Domain Name Servers.  But upon inspecting the contents of both /ppp/resolv.conf and etc/resolv.conf (are they the same file actually?)  they come up blank.  I'm guessing there is supposed to be something in these files to resolve DNS host names.  But there's nothing there.  Also, I'm not sure if it's related but there is a folder called /etc/ppp/resolv  and it is empty.

Hope this narrows things down a bit.

Thanks again,
SamAdams

---

### Post by samadams on 2007-04-20
UPDATE:

Since I never got a response and can't seem to find out how to fix this issue, I gave up and bought an ethernet modem.  After all that, I might not have even been dialed in on the Alcatel, I don't know for sure, the modem lights flashed appropriately but I never could do diddly squat online.  No browser, E-mail, ping, nothing.  So if anyone else has this problem, good luck.  If you figure it out, let me know.  It might be nice just in case my new modem should go kaput one day.

---

