---
title: "proxy chain using linun-linux-windows without ssh server on windows"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by vcguy on 2008-04-12
I have a home computer running ubuntu (lets call it A), a remote computer running some version of linux (B), and a 2nd remote computer running windows (C).  I can connect from A to B using putty, and I can connect fom C to B using putty.  Is it possible to route from A through B to C and then out to browse the internet, such that the I.P. address showing when browsing will be that of C?  How to do this?

The remote computer C is part of a network and is behind firewall, so I can not successfully set up an ssh server such as freeSSHd on it.

---

### Post by sammy_pal on 2008-04-13
I am absolutely sure that the following would work if 'Machine C' was running linux. I have very little hope that the similar thing will work in windows.
First install a proxy server like privoxy in 'Machine C'. Now using ssh remote port forwarding forward the port on which privoxy is listening to some port of Machine B. The syntax will be as follows -
ssh -R *:4321:localhost:8118 "ipaddr of B"
Replace "ipaddr of B" with the IP address of B
(You may use any other free port instead of 4321 as long as it is not being used by any application, remember to replace 4321 with the same port number in the next command)
This will do the following-
The port 8118 of C (port on which privoxy is listening) will get forwarded to machine B. Any connection made to B on 4321 will be tunneled through ssh and will reach port 8118 of C

Next use ssh local port forwarding to forward one of your port to B
ssh -L *:3456:"IPADDR of B":4321 "IPADDR of B"
Replace "ipaddr of B" with the IP address of B

The result of this is :
Any connection made to port 3456 of A is tunneled through ssh and reaches port 4321 of B

The net effect being - connection to 3456 of A is sent to 4321 of B which gets sent to port 8118 of C
Now just configure your browser in A to use localhost and port 3456 as an http and https proxy.
:) the job is done. Your browser will be able to use the proxy server of C

Only trouble is that this thing will almost certainly not work with *Windoze* on C.

---

### Post by kevdog on 2008-04-14
Good piece of advice however just a few clarifications.  You can do this with windows if you have cygwin installed.  This basically installs "red-hat" like libraries on the windows machine.  Granted once they are installed you need to install the ssh daemon just like in linux to get it to run on startup.

Second, I dont think privoxy is needed.  If all you want to do is tunnel an internet connection, you can take advantage of the builtin SOCKS5 capabilities of ssh, without an additional program.  Here is a guide that shows you how to use this feature between two computers.  Using the instructions above with combining it with the info in the referenced thread, you should be able to do a 3-part tunnel as well.
[http://ubuntuforums.org/showthread.php?t=723025&highlight=socks](http://ubuntuforums.org/showthread.php?t=723025&highlight=socks)

---

### Post by sammy_pal on 2008-04-14
Thanks for the clarification.
Actually I don't have a windows machine of my own(Thank God, I don't have :)) so never tried cygwin. I don't have much idea about cygwin, just one question does cygwin provide access to the DOS shell or creates some kind of virtual shell of itself.

---

### Post by vcguy on 2008-04-18
The suggested method isn't working for me.  

Putty allows for port forwarding, and runs on both Windows and Linux.  I tried setting up the port forwarding as mentioned but it ddn't work.

Can someone please test this using putty?  Just connect to a shell on a remote machine, over putty, and use port forwarding forwards and back, and route your browser through that as decribed above.  You should then see your own IP address when you browse the net.

This is what I tried for for my tunnels in Putty

L:3456 localhost:4321
R:4321 localhost:4321 

Then I connected Putty to a remote server shell.

I expected that setting my browser to connect to localhost:3456 would route traffic to the remote server, and then back to my machine and out to the internet.  No go.

I also tried using putty to connect to my local Ubuntu machine localhost on port 22, then in my shell ran the command ssh -D 9995, and in putty made a tunnel listening on L::9995.  I then tested setting my browser settings to point to the socks server localhost:9995 and this connect out to the internet.

I then tried setting the tunnels in putty to:
L:3456 localhost:4321 (to connect out from A to B)
R:9995 localhost:4321 (to listen from B back to A, and forward connections to 9995)

but that didn't work either.  I'm wondering if I need to instruct computer B to be doing some port forwarding?

---

### Post by kevdog on 2008-04-18
Cygwin provides a virtual bash shell similar to the DOS box in windows.


Can you describe your setup as you currently have it?  What is installed on each machine now?

---

### Post by vcguy on 2008-04-20
To begin with I'm trying to go out from A to B and back to A and then out to internet.  A and B are both running linux.

---

