---
title: "unable to connect to network"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by hds17 on 2008-03-25
Recently installed Ubuntu server 7.10

I can ping the box.  While logged in I can ping other boxes from the new server.  I can not connect to the box remotely or to any other server from it.  All very strange.

While logged in to the new server,  I can not  FTP SSH Telnet to other servers but I can ping them.  

Nmap shows port 22 open but I can not ssh to it,  it times out.  Any help would be appreciated.  I have spent most of my day combing through the internet and the forums here.

Thanks

MM

---

### Post by Eiríkr on 2008-03-25
I'm not familiar with what's included in Ubuntu Server; I do know that SSH is not included in the regular Ubuntu install.  Are you sure sshd is up and running on the new machine?  Timing out would certainly make sense if sshd were missing from the running process list.  ;)

HTH,

Eiríkr

---

### Post by hds17 on 2008-03-25
Thanks for the quick reply.

sshd is up and running and ssh client is installed.

I have never had this much trouble with an install in the paste,  it is enough to send me drinking today though.

---

### Post by Eiríkr on 2008-03-25
> I have never had this much trouble with an install in the **_paste_**, it is enough to send me drinking today though.

Whoa, looks like you've got an early start!  ;)

On a more serious note, I'm not familiar with NMap (a remote, or local tool?), but any chance a firewall might be blocking connections somewhere?

---

### Post by hds17 on 2008-03-25
That is what I though find one, and I know I never selected one during the install.  I used nmap to see what ports where open.


Not shown: 1673 closed ports
PORT    STATE    SERVICE
22/tcp  open     ssh
80/tcp  open     http
139/tcp open     netbios-ssn
445/tcp open     microsoft-ds
623/tcp filtered unknown
664/tcp filtered unknown

Nmap finished: 1 IP address (1 host up) scanned in 9.526 seconds

---

### Post by Iowan on 2008-03-25
Any firewalls running?  I've checked my sshd_config and ssh_config files to see what I did to make them run - not seeing anything significant.

---

### Post by hds17 on 2008-03-25
Oh and Yes I wish my bad spelling was caused by excessive drinking.

---

### Post by which_chick on 2008-03-25
Nmap is a (handy/free/useful/surprisingly informative) tool for port mapping both local boxes (the one you are sitting at) and boxes that are elsewhere, on your network or on someone else's network, should you have some need to do that.

You can't FTP, telnet, or ssh to other boxes on your network... but you can ping them.  Hrm.  Well, ping doesn't really work the same as port services do on the TCP/IP stack.  You can have (as you are experiencing) ping-ability but not full connectivity.  FTP, SSH, and Telnet are 21, 22, and 23 on TCP/IP port numbers... http is port 80 -- have you tried that one?  (If it's a firewall or something, usually that doesn't block port 80 because peeps need dey facebook, yo.)   

Are you doing the pings via hostname or via IP?    (Is this a DNS problem?)

Are the local-network boxes provided with real-world IP addresses or are they 192.168.x.x boxes?  (Is your new box set up with proper and appropriate netmasks?)

How's connectivity from the new box to the outside world? (real IP addresses) Can you go places outside your network?

Have you looked at the routing table on the new box?  (netstat -rn)   Has it got default routes and stuff there?

Just some things to try.  I'm not real sure where the problem is, but these are some things to try ruling out.

---

