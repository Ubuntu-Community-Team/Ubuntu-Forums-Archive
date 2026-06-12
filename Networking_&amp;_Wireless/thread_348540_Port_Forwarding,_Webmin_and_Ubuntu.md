---
title: "Port Forwarding, Webmin and Ubuntu"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by trisco2001 on 2007-01-28
I know this must be a really newbie question to ask. I have tried figuring this out a million different ways (or ten ways a hundred thousand different times each). I love Ubuntu, it beats the crap out of Mac OS X for basic server needs. 

But then someone goes and develops a program outside of open source that I'd really like to use, one that's got a binary for Mac OS X. I'm talking (of course) about Ventrilo. I know, they have a linux version too, or teamspeak does. But since it's closed source, they've only decided to port it over to x86 processors, and my Ubuntu box is a wiped Mac Mini (PPC). I can't use the linux version of their server on my Mini-Buntu. 

My Linksys Router crapped out on a vacation last year, and rather than replace it I set up the Mac Mini to do NAT using Webmin. Seemed pretty easy; there was a little option there to "setup the firewall for NAT from eth2". Perfect. Done. 

But IPTables is beyond me at this stage, and I'm not even sure if it's possible. I saw someone open a tunnel using SSH; something akin to: 

"ssh -l tristan -L 3784:192.168.10.246:3784 192.168.10.246 cat -"

But I don't know that this is doing what I want/need. The Ventrilo server is started; I can connect to it within the local network all I want. What I need to do is forward the port (3784) from the Mac Mini to my iMac where I can start and run the Ventrilo server. I guess the whole "cat -" thing is supposed to keep the connection open. But when I nmap my domain or localhost, the port is still closed. 

Is Webmin's built in firewall, which I am using for NAT, somehow preventing the port from being open? The server is obviously running, but the port appears to be closed (which doesn't make sense to me). Is Ubuntu itself taking steps to derail my attempts? What can I do to open the port?!

Tristan

---

### Post by trisco2001 on 2007-01-29
Okay. So I found this command: 

"sudo iptables -A INPUT -p tcp -m tcp --dport 3784 -j ACCEPT"

Which seems to set up the firewall to accept connections on this port. 

This seems to be the last problem I have. When I nmap localhost, it says the port is open. But when I nmap my domain, it says the port is closed. Why?!

tristan@Vlad:~$ nmap localhost -p 3784

Starting Nmap 4.10 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2007-01-28 22:50 PST
Interesting ports on localhost (127.0.0.1):
PORT     STATE SERVICE
**3784/tcp open  unknown**

tristan@Vlad:~$ nmap [www.theblowmedown.com](www.theblowmedown.com) -p 3784

Starting Nmap 4.10 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2007-01-28 22:50 PST
Interesting ports on c24-143-68-144.sea2.cablespeed.com (24.143.68.144):
PORT     STATE  SERVICE
**3784/tcp closed unknown**

What does it WANT from me?!

Tristan

---

### Post by kosmic on 2007-01-29
How many boxes do you have ?
Did you use this iptables command in the box that has acess to the net ?
Is your domain pointing to that box or tho another one that does Nat to the server box ?

---

### Post by trisco2001 on 2007-01-29
I have one server. The server is responsible for the internet of three other computers in the household. The IPTables command I mentioned was applied to the Server (Mac Mini)

INTERNET
      ||
Cable Modem
      ||
Mac Mini
     /|\
Other computers

The domain is pointed to the Mac Mini. Those two nmap commands are theoretically pointing to the same box, but one says the port is open and one says the port is closed. 

...

But, I mean, if I type in my domain in the browser it correctly pulls up my web site. Same with ssh and all the other protocols. This one just perpetually says it's closed.

Tristan

---

### Post by kosmic on 2007-01-29
Hum the possible answer is pretty simple, maybe your Cable provider is blocking acess to that ports, thats the reason why you can acess the port when you are inside your network, but if you want to acess that port from the outside using your Cable modem provider, they block that ports.

The only thing I can recomend is to email them to see what ports do they block

EDIT ****

Hum I've just nmap your network and you have a lot of ports open so it can't be your ISP that is blocking, can you please in a terminal type :

sudo iptables -L and post the output here ??

Also I advise that you Block Webmin port to the outside world ;)
And don't Allow Root logins with ssh :)

---

### Post by trisco2001 on 2007-01-29
As you can tell, I'm a fairly new addition to the sysadmin community. Lol. I know enough to realize that these are the rules set up for my firewall. The two ACCEPT lines you see in the input chain were my attempts at allowing this communication. I know what port this thing communicates on, but I'm not sure which protocol it uses. 

Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:3784
ACCEPT     udp  --  anywhere             anywhere            udp dpt:3784

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by kosmic on 2007-01-29
Hum what you are trying to do is Tunneling a SSH conection, this is the reason you can see a open door in your network.

Just read a bit about that here -> [http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Port_Forwarding.html](http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Port_Forwarding.html)


At first i was thinking that you want to connect to an SSH server, but i've read your post again and now I realize that you are making an SSH Tunel :(.

To know more about SSH tunneling read the page Above, it explains better than my what is SSH Tunneling :)

Any help you need just post here ;)

---

