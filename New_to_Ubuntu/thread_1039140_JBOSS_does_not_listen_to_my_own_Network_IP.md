---
title: "JBOSS does not listen to my own Network IP"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by ashimono on 2009-01-14
Greetings,

I am currently having some problems to make my JBOSS apps. being accessed by other computers in my network.

First of all, the local configuration:

Ubuntu - 8.04
JBOSS -  4.2.2 GA
Java -  1.6_u7

I am currently under a proxy, and using fixed IP address. However, this does not seem to be the root of the problem, since I already accessed a server in other machine running in Windows XP.

I read another [topic]("http://ubuntuforums.org/showthread.php?t=678411") here in this forum which made some suggestions. I also followed this [topic]("http://www.linuxquestions.org/questions/linux-server-73/accessing-jboss-port-8080-remotely-694848/") from other forum.

I am using the -b 0.0.0.0 command along with ./run.sh with no success. I also tried using just my IP (-b 192.168.1.166) and my netstat shows that the correct IP and correct port are being listened, however when I try to connect (browser or telnet) it does not work.

Here are the results for each of the suggested commands:

telnet 192.168.1.166

> Trying 192.168.1.166...
telnet: Unable to connect to remote host: Connection refused


netstat -ntalp|grep java

> tcp6       0      0 192.168.1.166:3873      :::*                    LISTEN      7865/java       
tcp6       0      0 192.168.1.166:8009      :::*                    LISTEN      7865/java       
tcp6       0      0 :::51306                :::*                    LISTEN      7865/java       
tcp6       0      0 192.168.1.166:1098      :::*                    LISTEN      7865/java       
tcp6       0      0 192.168.1.166:1099      :::*                    LISTEN      7865/java       
tcp6       0      0 :::44141                :::*                    LISTEN      7865/java       
tcp6       0      0 192.168.1.166:8080      :::*                    LISTEN      7865/java       
tcp6       0      0 192.168.1.166:8083      :::*                    LISTEN      7865/java       
tcp6       0      0 :::33111                :::*                    LISTEN      7865/java       
tcp6       0      0 192.168.1.166:8443      :::*                    LISTEN      7865/java       
tcp6       0      0 192.168.1.166:4444      :::*                    LISTEN      7865/java       
tcp6       0      0 192.168.1.166:8093      :::*                    LISTEN      7865/java       
tcp6       0      0 192.168.1.166:4445      :::*                    LISTEN      7865/java       
tcp6       0      0 192.168.1.166:4446      :::*                    LISTEN      7865/java   

This is what confuses the most. How is it possible that the correct ip : port are displayed in netstat, and yet I can not access it? Remembering that the company's firewall, proxy, etc, already worked for a windows machine. Is it possible to have restrictions only for ubuntu?

Thanks in advance,

Alexandre.

---

### Post by ashimono on 2009-01-14
](*,) Found the solution:

my "hosts" file (located in /etc/hosts) was not properly configured. I didn't know we could bind more then one IP for each alias (yeah, really a noob thought). So, now, I just added the following line to this file:

192.168.1.166 localhost name-of-my-computer

And it works! Apparently now when JBOSS starts and looks for the "localhost" in "hosts" file, it finds the association with the external ip address.

Also, the proxy settings were not right as well...

I added my ip address with a "/" in the end, as if it was a dominium (as if it was "http://webserver/". The correct spelling is just the ip address, like "192.168.1.166".

See ya. ;)

---

