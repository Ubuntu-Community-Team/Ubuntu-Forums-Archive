---
title: "Sane on Hardy Heron scanner share"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by the_trooper47 on 2008-07-05
okay here it is, Ubuntu Hardy with USB scanner installed & able to be used locally with Xsane. 

Problem with sharing installed & working scanner on Ubuntu to pc's in a local domain that are using Xsane-32.  Unable to properly configure host & clients...  When using Xsane-32 the "No Devices Available" message appears ....

I found point 10 on this site 'http://www.xs4all.nl/~ljm/SANE-faq.html#94' to be very useful but here's where i'm getting stuck....

10.2 : 
a) works great locally on the Ubuntu pc using Xsane.
b) WinXp pc: typed in 'hostname' of the pc in the "net.conf" file.
c) WinXp pc: added hostname's IP address in "saned.conf"
d) "Be sure that the inetd starts up the correct saned. Also, be sure that the UID that runs saned is allowed to make a scan."      -> How do i know, how can I check?

10.5: link to 'http://penguin-breeder.org/sane/saned/' 

a) "/etc/services" sane-port 6566/tcp   # SANE network scanner daemon  <- looks ok! :-)
b) "/etc/inetd.conf" was empty so i pasted & saved (as root) 'sane-port  stream  tcp  nowait  saned.saned /usr/local/sbin/saned saned'
c) "/etc/xinetd.conf"  doesnt exist!  (Is something not installed properly?)

Can anybody help with this one ?  ... :-)

A step by step guide for the host server & a separate guide for configuring the win32 clients would be awesome!!

:guitar:

---

### Post by Chunk of Earth on 2008-09-21
The first thing you need to do is install xinetd:
```
sudo apt-get install xinetd
```Create a file named /etc/xinetd.d/sane-port
(I named it that to match the name of the service, don't know if that's necessary)
```
sudo nano /etc/xinetd.d/sane-port
```Add these lines and save it (Ctrl-X):
```

service sane-port
{
              socket_type = stream
              server = /usr/sbin/saned
              protocol = tcp
              user = root
              group = root
              wait = no
              disable = no
}
```(I'm on gutsy and there's a bug that prevents user=saned, group=saned from having access. This file gives root access to saned so it could be risky. You can try replacing root with saned on hardy and see if it's fixed now)

Restart xinetd:
```
sudo /etc/init.d/xinetd restart
```See if saned is listening:
```
sudo netstat -nap|grep 6566
```or```
telnet localhost 6566
```Over at the client PC (Linux) edit /etc/sane.d/net.conf and add the server's IP address to the file, save it, then check for the scanner:
```
scanimage -L
```Haven't tried it from Windows yet because of the nausea.

---

### Post by westywesty on 2008-12-08
Hello,
I hope this thread is still open, because I have some troubles with similar problems:
I'm a quite recent linux/ubuntu-user, so I'm still trying to understand it all:
I want to share a scanner epson gt-15000 on an ubuntu network: the server, where the scanner is connected is 8.04 and connected to the web, the client is 8.10 and is wireless. The network is working (we share a printer and some files), and the scanner works with XSane on the server without problems.

I followed all the steps described in previous posts:

-I typed 'localhost'in the /etc/sane.d/net.conf file on the server and saved
-I typed the IP address of the client in the /etc/sane.d/saned.conf file , and saved
-I checked the /etc/services file: it contains a line 'sane-port 6566/tcp sane saned #SANE network scanner deamon'
-I added the line 'sane-port stream tcp nowait saned.saned /usr/sbin/saned saned' and saved (the saned exec.file is located in /usr/sbin)
-I installed xinetd:
```
sudo apt-get install xinetd
```
-I created a file named /etc/xinetd.d/sane-port:
```
sudo nano /etc/xinetd.d/sane-port
```
and added these lines and saved:
```

service sane-port
{
              socket_type = stream
              server = /usr/sbin/saned
              protocol = tcp
              user = saned
              group = saned
              wait = no
              disable = no
}
```
(I checked there is a group called saned, and when I wanted to create a user saned with the users and groups tool, then I got the response there already was a user with that name)
-I restarted xinetd:
```
sudo /etc/init.d/xinetd restart
```
and got the response 
'stopping internet superserver... ok' and
'starting internet superserver... ok'
-I checked if saned was listening:
```
telnet localhost 6566
```
and got the response:
'trying', followed by an ip-address and
'connected to localhost'
-I typed 'scanimage -L' in the terminal and got the message he found the scanner (and also another scanner, inknown to me, that isn't connected...?)
-Then I went tothe client pc and added the IP address of the server in the net.conf file and that of the client in the saned.conf file

But still, my client pc does not see the scanner (typing 'scanimage -L' responds: 'no scanner found...' and also Xsane does not find a scanner)

What did I do wrong? I am struggling with this problem for quite some time now, and I don't know anymore what to do next?

Maybe the IP addresses I typed in are not the correct ones; when I type (ifconfig' in the terminal I get several IP addresses (lo, eth0, wlan, ...), and it's not very clear to me which ones to use...

Tahnks,
westy

---

### Post by Chunk of Earth on 2009-03-07
I just had the good fortune of needing to rebuild the server that hosts my network scanning service. There was nothing very unusual that I had to do to make network scanning work again. I followed the method posted [here]("https://help.ubuntu.com/community/ScanningHowTo#Manually%20Installing%20a%20Network%20Scanner"). I tried to make inetd work but it refused so I used the xinetd method again.  I still needed to use the root user and group in my /etc/xinetd.d/saned file so that bug hasn't been fixed in Intrepid.

---

