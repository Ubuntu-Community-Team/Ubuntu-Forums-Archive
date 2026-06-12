---
title: "Need free NX Help please"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by ashc on 2008-11-12
hello, i am new to nxclient and I am trying to connect to my ubuntu server but I am having issues with FreeNX any help would be much apreciated...


Here is what the details say on NXClient

it sais authentication complete, then sais connection error?


NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 700 Session id: r16252.ovh.net-1000-54925100B44AAC086A5CE1859BE1BADA
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: bd322a48d61e520202a6cc8fb502b983
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: bd322a48d61e520202a6cc8fb502b983
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/admin/.nx/F-C-r16252.ovh.net-1000-54925100B44AAC086A5CE1859BE1BADA/session". You might also want to try: ssh -X myserver; /usr/bin/nxnode --agent to test the basic functionality. Session log follows:
/usr/bin/nxserver: line 1368: 23542 Terminated              sleep $AGENT_STARTUP_TIMEOUT
Can't open /var/lib/nxserver/db/running/sessionId{54925100B44AAC086A5CE1859BE1BADA}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{54925100B44AAC086A5CE1859BE1BADA}': No such file or directory
NX> 1006 Session status: closed
NX> 1009 Session status: starting
NX> 1009 Session status: starting
NX> 1001 Bye.
NX> 280 Exiting on signal: 15

any ideas, would be much apreciated

---

### Post by Hibbelharry on 2008-11-12
You posted the same question in 3 different subforums. Thats bad behaviour. Stop doing this in future or don't expext too get much help from people !

---

### Post by ashc on 2008-11-13
ok im sorry its just i didnt know what area of the forum to post it in, i wont do this again

---

### Post by Peter09 on 2008-11-13
As a first check can you login from you  client to your target server using ssh?

---

### Post by ashc on 2008-11-13
hello. im not to familiar with what you have suggested as im quite new to theserver its self, please could you explain how to do this maybe?,
thnx....

---

### Post by Peter09 on 2008-11-13
Can you try the following command in a terminal on your client (where there are angled brackets you need to put your data.)

```
ssh -X <your server user id>@<your server name> xterm
```

this should give you a terminal on your server.

---

### Post by ashc on 2008-11-13
im so sorry but i am not sure where you mean to type this information, i am an extreme newbie to this client, im gratefull for any help you can give me....

---

### Post by Peter09 on 2008-11-13
Open a terminal, use the menu sequence below.

 Applications->Accessories->Terminal

At the prompt in the terminal type the command line that I gave you followed by the enter key. Note that Case matters.


user name = your login name at the server
server name = the name of the server as it appears on the network.

example 

ssh -X fred@myserver xterm

---

### Post by ashc on 2008-11-13
my nx client, doesnt have any of these in the settings, should i be looking somewhere else?

---

### Post by ashc on 2008-11-13
i am actually using windows but am trying to connect to my server which is ubuntu, if that helps

---

### Post by Peter09 on 2008-11-13
You need to open a terminal. This is nothing to do with NX, but NX needs ssh to work. I am trying to check if ssh is installed correctly on your client and server.

the Applications menue is on the top panel.

---

### Post by ashc on 2008-11-13
> **ashc said:**
> my nx client, doesnt have any of these in the settings, should i be looking somewhere else?

> **ashc said:**
> i am actually using windows but am trying to connect to my server which is ubuntu, if that helps

the funny thing is , i was connecting succesfully and then out of the blue it just disconnected me from the derver and wont let me log back on since?,

---

### Post by ashc on 2008-11-13
yes it is on ubuntu, but im using windows, i can only acess ubuntu when im connected to my server, which it is not letting me do, thnx for your help, im completly baffled...

---

### Post by Peter09 on 2008-11-13
Ahh ... totally different game. 

If you have been connected and it won't connect again then check you can still see the server on your network.

---

### Post by ashc on 2008-11-13
im sorry but where would i look to find this out? , lol im not very clued up when it come to this type of thing!!...

---

### Post by Peter09 on 2008-11-13
I think you need to go and talk to who ever set up your system. You are trying to do a reasonably complex fix without enough knowledge.:)

---

### Post by ashc on 2008-11-13
NX> 706 Agent cookie: 9f76871a9c02804a239d560dbcb014c6
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/admin/.nx/F-C-r16252.ovh.net-1000-BF201C3F7159B5BDCFCEB70CAAC2667C/session". You might also want to try: ssh -X myserver; /usr/bin/nxnode --agent to test the basic functionality. Session log follows:
/usr/bin/nxserver: line 1368: 24788 Terminated              sleep $AGENT_STARTUP_TIMEOUT
Can't open /var/lib/nxserver/db/running/sessionId{BF201C3F7159B5BDCFCEB70CAAC2667C}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{BF201C3F7159B5BDCFCEB70CAAC2667C}': No such file or directory
NX> 1006 Session status: closed
NX> 1009 Session status: starting
NX> 1009 Session status: starting
NX> 1001 Bye.
NX> 280 Exiting on signal: 15


this is what its telling me in my log of nx client, if this makes any sense, i know it doesnt to me...

---

### Post by ashc on 2008-11-13
> **Peter09 said:**
> I think you need to go and talk to who ever set up your system. You are trying to do a reasonably complex fix without enough knowledge.:)

i have an nx client, which connects to a sever through a username and password, and my server is a company, they cannot help ,e as all they provide is the server, do you know of any other programs to do the same as nx client?

---

### Post by Peter09 on 2008-11-13
Have you tried rebooting your system.

---

### Post by ashc on 2008-11-13
yes, i have, didnt seem to work, really weird how one minuite it  was woking and now it isnt, and i havnt changed any settings in nxclient...

---

### Post by Peter09 on 2008-11-13
As the company to check at their end.

---

### Post by ashc on 2008-11-13
ok i will do, thnx for your help, iv got to go to work now but il bw back later il let you know what the outcome was,  cheers....

---

### Post by ashc on 2008-11-13
> **ashc said:**
> ok i will do, thnx for your help, iv got to go to work now but il bw back later il let you know what the outcome was,  cheers....

im also getting a session start up error every  now and again if that helps,


NX> 148 Server capacity: not reached for user: admin
NX> 105 startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="ashley" --type="unix-gnome" --geometry="1110x864" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1110x864x32+render" 

NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 700 Session id: r16252.ovh.net-1000-833BF659FA218152A229ACF63A5FC36E
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: f7bab4e4ee992a12dba79ddfde1bee60
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: f7bab4e4ee992a12dba79ddfde1bee60
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 /usr/bin/nxserver: line 1368: 28150 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/admin/.nx/F-C-r16252.ovh.net-1000-833BF659FA218152A229ACF63A5FC36E/session". You might also want to try: ssh -X myserver; /usr/bin/nxnode --agent to test the basic functionality. Session log follows:
NX> 1006 Session status: closed
NX> 1009 Session status: starting
Can't open /var/lib/nxserver/db/running/sessionId{833BF659FA218152A229ACF63A5FC36E}: No such file or directory.
mv: cannot stat `/var/lib/nxserver/db/running/sessionId{833BF659FA218152A229ACF63A5FC36E}': No such file or directory
NX> 1009 Session status: starting
NX> 1001 Bye.
NX> 280 Exiting on signal: 15

---

