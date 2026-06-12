---
title: "[SOLVED] Control or View Remote Desktop over a Network - VNCviewer"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by cyclouno on 2008-07-31
Hello guys..

**@ Question**
View and Control remote desktop over Internet or LAN

**@ Reference**
VNC viewer
[http://www.realvnc.com/products/free/4.1/index.html](http://www.realvnc.com/products/free/4.1/index.html)

**@ Why? Scenario?**
===I got a desktop pc at home running Ubuntu Hardy, which has access to Broadband - USES STATIC IP!

===I got another pc at office running Fedora sulphur - again with broadband access - USES DHCP - NO STATIC IP!

===Simply want to control my home pc from Office. 

**@ What did I do?**
%%%On Home PC....ubuntu hardy%%%
===run $ vino-preferences
===allowed other computers to access my Home PC
===set a password
===checked "encrypt connection"
===set port no to 5900 - default
===fired-up vncserver $ vncserver
===it said I had to install vnc4server / xvnc4viewer / x11vnc / vino
===so installed all those packages, without any problem.. just like it said... via synaptic
===run $ vncserver
===gave a password & verified it
===checked if vnc is running.. so run $ pgrep vnc
===throwed 2 PID's - so finally vncserver is up & running

%%%On Office PC...fedora sulphur%%%
===Ran $ vncviewer
===entered host IP (static home PC ip)
===it says "Unable connect to socket: connection refused (111)"

**@ what might be the problem?**
===iptables (firewall)?
===tcp wrappers?? or missing some services??
===Since it said "111" - I started both NFS & Portmap service in fedora... (111 is portmap service port number).. should I do it in Ubuntu? & how?
===BTW.. how do I find open ports in Ubuntu... the $ nmap localhost doesn't exist...

:confused::confused::confused:

---

### Post by ChumleyEX on 2008-07-31
yeah my first thought is the router/firewall.. If you use ssh you can tunnel to it and leave port 5900 closed. It works really well.

---

### Post by cyclouno on 2008-07-31
@chumleyEX
turned off firewall at both ends... 
$ /etc/init.d/iptables stop
$ service iptables stop

No SSH.. still no results..

---

### Post by ChumleyEX on 2008-07-31
you don't have a router and also are you logged into the desktop on the ubuntu machine?

---

### Post by cyclouno on 2008-08-01
yap.. no router... jus modem + pc... & logged in !!

---

### Post by cyclouno on 2008-08-02
apparently.. I consider this thread solved since I found a parent thread on the same topic.. [http://ubuntuforums.org/showthread.php?t=272986](http://ubuntuforums.org/showthread.php?t=272986)

So many options now.. gotta try 1 by 1...

---

