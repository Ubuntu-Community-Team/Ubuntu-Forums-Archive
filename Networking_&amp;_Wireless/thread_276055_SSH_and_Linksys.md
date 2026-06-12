---
title: "SSH and Linksys"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by thomasaaron on 2006-10-12
Hello. 
I've got an Ubuntu 6.06 machine at home and one at work. I've installed openssh on both.

If I have both machines at home, I can network them with no problems.

If I try to connect to the one at home with my machine at work via the Internet, the connection times out.

The one at home is behind a Linksys router, and judging by some of the other posts on this forum, I realize that some type of port forwarding stuff will be necessary.

1. Is that why the connection is just timing out?
2. Is anyone out there familiar enough with the linksys router to help me set it up?

Best,
Tom

---

### Post by kidders on 2006-10-12
Hi there,

Whatever router you're using, the way to sort this out is the same :-)

Basically, when a packet arrives at your network, it hits your router, which obviously wonders what to do with it. In the absence of any better suggestion, it will most likely just drop it. If you tell your router to forward such packets to a particular computer, you're in business.

[LIST=1]
[*]Open port 22 on your router's firewall, if it has one.
[*]Redirect port 22 to the SSH server you want external users to log into.
[*]Make sure the computer running the SSH server isn't firewalling port 22.
[*]Make sure your SSH server is listening on the correct network interface.
[/LIST]

If you have access to an external SSH server, you can test your setup by going around in a circle ... log into it, and from there, back into yours.

I hope that helps.

**Edit:** This setup will most likely break from time to time, if the SSH server's IP is dynamically asigned. Try to keep it as static as possible, so you don't have to keep reconfiguring your port forwarding.

---

### Post by Endwin on 2006-10-12
Good ol' linksys served me well. Yes you need to port forward port 22 to the machine in your home with the openssh server. 

[http://www.dslwebserver.com/main/sbs-linksys-port-forwarding.html]("http://www.dslwebserver.com/main/sbs-linksys-port-forwarding.html")

gives a graphic step by step guide for the linksys. Generally you want to go to advanced and then find the port forwarding tab. Place in the port or port range and the IP of the machine you want to connect to. Click apply and you should be set.

---

### Post by thomasaaron on 2006-10-12
Thanks, folks.

I'll give that a try tonight and test it again tomorrow.
I'll let you know how it works out.

Best,
Tom

---

### Post by thomasaaron on 2006-10-13
Well, that did not work.
The connection is timing out.
Let me run through what I am doing, maybe that is where the problem is.

So I am pulling up a terminal and typing:

ssh (myusername)@(the ip assigned to my computer by the linksys router)
it would look something like joescomputer@192.168.1.100

Then, after a while the connection times out.

It seems like more information should be given at the ssh command line to help it find my computer at home in the midst of the millions of other computers out there.  Is that really all I need to type?

Setting up the porting seemed pretty simple, and, as far as I can tell, there are no firewalls running. Again, from my home, I can network into the computer with no problems at all.

Best,
Tom

---

### Post by geekman on 2006-10-13
> **thomasaaron said:**
> 
So I am pulling up a terminal and typing:

ssh (myusername)@(the ip assigned to my computer by the linksys router)
it would look something like joescomputer@192.168.1.100

Then, after a while the connection times out.

It seems like more information should be given at the ssh command line to help it find my computer at home in the midst of the millions of other computers out there.  Is that really all I need to type?


So are you saying that you are typing [user]@192.168.1.100 from work? if so this will not work because that is a local IP and your computer is only accessible to you with that IP from within your LAN i.e. from behind the router. When trying to access the computer from over the internet you must use instead a public IP address, more specifically YOUR one, it should listed somewhere near the "Status" Page on your linksys. First try that, if all is well then i would suggest you signup for a free service like DynDns, which enables you to have a free domain that always points to your public IP, even if it changes, and i assume that your public IP is dynamic so this is a good idea.

Hope ive helped a bit, and since im getting tired, i hope i havent said something which has already been said :D.

EDIT: also, if you didnt realise, yes you are right, more information must be given to distingush your computer from the rest, that is your pub IP. It wasnt really necessary but i just had to tell you that you were right :D. Also if you end up using the DynDns service, you will need to access the box via that domain rather than your public IP.

---

### Post by thomasaaron on 2006-10-13
Thank you. I'll give that a try and report back.

---

### Post by thomasaaron on 2006-10-16
Excellent!
Everything worked perfectly and I can now access my computer at home from my laptop at work.
Thank you very much for your help.
Tom

---

### Post by geekman on 2006-10-17
Glad you got it working and happy i could help:cool:

---

### Post by tturrisi on 2006-10-17
For added security, use a different port for ssh.  I use 3022 instead of 22 on my home servers.  This way, common port scans won't detect ssh and the kiddies may give up or ignore your lans.

---

