---
title: "port"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by santdevil on 2010-01-02
hai i have installed ubuntu iand i have also opened a  network port by using command below i want  to know weather port have opened or not..? thanks

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

---

### Post by Captain_tux on 2010-01-02
Use the **netstat** command to see what your open connections are...

---

### Post by jonest1 on 2010-01-02
Using 'netstat -an | grep LISTEN' will show you if tcp port 6881 is open on the computer running the application which is using port 6881.  

To see if port 6881 is available to other computers on your lan, you can try to telnet to it.  

```
telnet ip-address 6881
```

So, if you have an application running on the port and you can connect to the port from a different computer, you should be good to go.

---

### Post by Cheesemill on 2010-01-02
By default iptables accepts all inbound connections. Unless you have configured it otherwise the should be no need to manually open ports.

---

### Post by lovinglinux on 2010-01-02
Since you are trying to open port 6881, I presume you are setting it up for BitTorrent. So see [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923) .

It includes instructions on how to check if the port is opened and troubleshoot connection issues.

Since you are new to Ubuntu, I guess you would be more comfortable with [gufw](apt:gufw) firewall manager, instead of iptables commands.

---

### Post by The Cog on 2010-01-02
People refer to ports being open to mean two completely different things. 

1:
A computers ports are closed unless an application asks the operating system to listen for incoming packets on a port. The application is said to be opening the port. Unless an application has opened a port in this way, the port is closed and will refuse incoming calls. If an application has opened the port, then the OS will accept connections to that port and will tell the application when a connection arrives.

2:
A firewall will generally prevent connections that it hasn't explicitly been configured to allow. It normally does this by simply discarding packets belonging to disallowed connections so the don't reach their destination. The act of configuring a firewall to allow connections to a particular port number is ofter referred to as openng the port. Because of the confusion with meaning 1 (see the other posts in this thread) I feel this should be called allowing or permitting the port rather than opening it.

For the first meaning, simply starting the appropriate server application (probably a bit-torrent program if you're worryng about port 6881) is all that is needed to open the port.

A default Ubuntu install doesn't block any packets (all connections are allowed) so unless you chose to install a firewall like firestarter or gufw (which will then configure a default deny in iptables) then you don't need to worry about the second meaning - all ports are already permitted.

---

### Post by lovinglinux on 2010-01-02
> **The Cog said:**
> People refer to ports being open to mean two completely different things. 

1:
A computers ports are closed unless an application asks the operating system to listen for incoming packets on a port. The application is said to be opening the port. Unless an application has opened a port in this way, the port is closed and will refuse incoming calls. If an application has opened the port, then the OS will accept connections to that port and will tell the application when a connection arrives.

2:
A firewall will generally prevent connections that it hasn't explicitly been configured to allow. It normally does this by simply discarding packets belonging to disallowed connections so the don't reach their destination. The act of configuring a firewall to allow connections to a particular port number is ofter referred to as openng the port. Because of the confusion with meaning 1 (see the other posts in this thread) I feel this should be called allowing or permitting the port rather than opening it.

For the first meaning, simply starting the appropriate server application (probably a bit-torrent program if you're worryng about port 6881) is all that is needed to open the port.

A default Ubuntu install doesn't block any packets (all connections are allowed) so unless you chose to install a firewall like firestarter or gufw (which will then configure a default deny in iptables) then you don't need to worry about the second meaning - all ports are already permitted.

+1

Not to mention that a firewall is probably unnecessary, since all ports are closed by default and when you open the port by running a BitTorrent client, you will need to allow incoming connections on that port. So the firewall will be used to block ports that are already closed and allow the only port that is opened, which makes no sense.

---

