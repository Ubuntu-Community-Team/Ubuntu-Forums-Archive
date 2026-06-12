---
title: "iptables in Ubuntu 7.04"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by PcPixel on 2007-08-18
I'm using Ubuntu 7.04 x86 and would like to set up a internet accessable file server using SSH. Now, I've done this at work for my internal Ubuntu print servers, and it works wonderfully. The problem I have is when I try to protect the system at home using Firestarter/iptables.

What I'm seeing is:
-There is no /etc/init.d/iptables which means when the system boots up, there are no firewall rules.
-If I use Firestarter, the rules only go into effect if the user who created the rules logs in & runs Firestarter.

Is there a script to put iptables into the boot sequence? Any why is it that Ubuntu's firewall behaves in this manner? I am unsure if Server behaves this way, but at present I want to have the GNOME Desktop on the machine.

(I have proven that SSH is in fact working, so that isn't part of the question.)

Thanks!

---

### Post by ruibernardo on 2007-08-18
Hi PcPixel,

when Firestarter is restarted, either by the GUI or restarting it in /etc/init.d, iptables rules are flushed and applied again by Firestarter. There is no /etc/init.d/iptables (or other rules script) that can "survive" this.

To do what you want with Firestarter you have to put those "special" rules in a file that is executed after Firestarter flushes iptables.

The most commonly used file is **/etc/firestarter/user-pre**. It is executed after flushing iptables, but **before** applying the rules. [Here]("http://www.fs-security.com/docs/vpn.php") is an example of how to use this file. NOTE: the file does not exist by default, you have to create it.

There is another file that can be executed **after** Firestarter has defined the iptables rules: /etc/firestarter/user-post.

I think there are some other examples of using /etc/firestarter/user-pre in this forum and in the Internet.

---

### Post by fusionisthefuture on 2007-08-19
this is not the same question as the OP's, and i hope im not hijacking the thread, but i have a question about my iptables setup.  currently, im using webmin to configure iptables, and this is what it looks like:  

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  localhost            localhost           
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 


Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  localhost            localhost           
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:bootpc dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:80 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:443 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:21 
ACCEPT     udp  --  anywhere             anywhere            udp spts:1024:65535 dpt:53
```

the issues lies with FTP.  (and for the record, this is just a client computer)  on this computer i need to recompile alsa to get the sound to work properly, and to do that according to the howto, i need to run 
```
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2
```
in the terminal.  when i do this i get
```
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/lib ... done.
==> PASV ... 
```
and there it stops.  if i tell webmin to allow everything, it works just dandy, and i cant figure out what ports to accept from.  can anyone help?
thanks a bunch.  
-arne
p.s.  i just reinstalled ubuntu today due to a different problem, and i was using this same setup before that, but reentered it manually into webmin, and i cant remember an actual instance of trying to dl with ftp, but im fairly certain it happened on at least one instance.

---

### Post by fusionisthefuture on 2007-08-21
well apparently, the problem is not with port 21, 

```
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/lib ... done.
==> PASV ... couldn't connect to 160.217.9.25 port 54169: Connection timed out
Retrying.
```

how do i tell the firewall to allow that port when its related to port 21.  isnt that part of the whole related, established dealy?

thanks,
-arne

---

### Post by fusionisthefuture on 2007-08-21
man do i feel stupid, although on my behalf, i never noticed where it comes right out and says this, but apparently, the order of the rules in webmin make a difference.  i moved the rule that allows port 21 to in front of the one that allows outgoing connections that are established/related, and that fixed it
-arne

---

### Post by fusionisthefuture on 2007-08-21
disregard last post, that did not fix it ><

---

