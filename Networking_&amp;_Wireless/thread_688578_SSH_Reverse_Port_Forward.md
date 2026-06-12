---
title: "SSH Reverse Port Forward"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by im_unowen on 2008-02-05
I am a newcomer to this and will appreciate all help. 

I have a few development boxes (say DEVBOX) connected on a LAN and sitting behind our firewall that cannot be exposed to the outside world. However, I need to provide for  remote users (say RLAPTOP) to access these boxes over the internet. The firewall settings permit incoming & outgoing traffic only on ports 80 and port 443 (I am not permitted to make any changes to the firewall settings).

I am planning on enabling remote access as follows:

[LIST=1]
[*]Set up an intermediary system (say BROKER) in our DMZ
[*]Establish a reverse SSH tunnel between BROKER and DEVBOX using RSA key authentication (say port xxxx on BROKER binding to port 443 on DEVBOX)
[*]Have RLAPTOP establish an SSH connection to BROKER using RSA key authentication (on port xxxx of BROKER, thereby leading to port 443 on DEVBOX)
[/LIST]
I have the following questions:

[LIST=1]
[*]What would be the security implications of the above set up? 
[*]What steps do I need to take in order to make sure that:
[/LIST]
[INDENT][LIST]
[*]Neither DEVBOX nor RLAPTOP can access any of the persistent information on BROKER
[*]Neither DEVBOX nor RLAPTOP can execute any commands on BROKER
[*]Neither DEVBOX nor RLAPTOP can discover and/or piggyback on any preexisting SSH tunnels
[/LIST][/INDENT]
Also, is there anything that I am missing & must consider?

Thank you for your help with this.

---

### Post by kirsche on 2008-02-05
when you say port xxx on broker - this should really be 443 / 80, right? (since these are the only 2 ports accessible from teh outside world.)

How do you want to access broker? SSH? If so, you could do a normal port forward like
ssh -L 443:DEVBOX:PORT user@broker

This would allow you access from rlaptop via broker to devbox

---

### Post by im_unowen on 2008-02-05
thanks kirsche! yes, the idea is to do an ssh port forward similar to ssh -L 443:DEVBOX:PORT user@broker. however, i am not sure i understand all the security implications of doing something like this. any insights you can share will help!!

cheers.

---

### Post by kirsche on 2008-02-06
You should use strong auth mechanisms, obviously. :)
For example, use cert based authentication to get to BROKER.
You still need to authenticate to DEVBOX afterwards, which is better than having a tunnel already up and running.
You can "secure" your sshd on BROKER with blacklists / knocking, depending on your needs.
The same goes for the target machine. (Security through obscurity is not a good idea, but you could use non default ports/user names on the devboxes to setup the tunnel - this might confuse a possible intruder for approx. 2 minutes :) )
Additionally, you could introduce 2 factor auth - based on a cert + radius auth.

Or, you can go the more expensive way and invest in a ssl vpn solution to provide access.

---

