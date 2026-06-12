---
title: "vnc cant connect"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by compgeek83 on 2008-05-22
I'm using the basic built-in VNC on hardy, when I open remote desktop on the box itself and connect I can connect fine

when I go to another machine, hardy or xp, any client, I cannot connect, it says connection failed

any ideas?

---

### Post by xkaliburx on 2008-05-22
1st thought w/o more info is firewall.  Are you running anything on that box, and since you mentioned hardy as another machine, jump on that box and nmap or port scan the server you want to connect and make sure it's listening and it's open to you.

---

### Post by compgeek83 on 2008-05-22
nope, no firewalls, when I run nmap or a port scanner from windows it tells me no open ports

---

### Post by compgeek83 on 2008-05-22
vnc worked last week when I did a clean install, but sometime around the weekend it no longer worked.

---

### Post by xkaliburx on 2008-05-22
I assume you mean no longer worked from other machines, not all together right?

Also, what does a port scan from itself (127.0.0.1) show as you said you could connect locally.

Also, do you see anything in the logfiles such as a connect attempt, deny, etc.  

I still find it odd that no ports show open from a remote scan, not even an OS guess, etc. which really points to some FW running, but I am looking at the vino pref's to see if they allow different debug levels.

---

### Post by jtrindle on 2008-05-22
This might sound silly, but... are you logged in locally to the machine?  VNC doesn't work in the default config unless a user is logged in.

Also, that user's preferences for Remote Desktop apply:

System->Preferences->Remote Desktop->General->Allow other users to view your desktop CHECKED

and

System->Preferences->Remote Desktop->Advanced->Allow only local connections NOT CHECKED.

---

### Post by compgeek83 on 2008-05-22
> **jtrindle said:**
> This might sound silly, but... are you logged in locally to the machine?  VNC doesn't work in the default config unless a user is logged in.

Also, that user's preferences for Remote Desktop apply:

System->Preferences->Remote Desktop->General->Allow other users to view your desktop CHECKED

and

System->Preferences->Remote Desktop->Advanced->Allow only local connections NOT CHECKED.


those settings are set the right way


I have firewalker installed because I read in another post to use it to configure my firewall, but from the opening screens of it I'm assuming that the firewall isn't on unless I use firewalker to turn it on (also this wasn't working pre-firewalker)

I'll have to try the local port scan tomorrow, cant get logged in to do it from home lol

where do I find these log files?

---

### Post by compgeek83 on 2008-05-23
results of nmap scan (from localhost)

```
Starting Nmap 4.53 ( http://insecure.org ) at 2008-05-23 14:03 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1704 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
631/tcp  open  ipp
5801/tcp open  vnc-http-1
5900/tcp open  vnc
5901/tcp open  vnc-1
5902/tcp open  vnc-2
5903/tcp open  vnc-3
6001/tcp open  X11:1
6002/tcp open  X11:2
6003/tcp open  X11:3

```

---

