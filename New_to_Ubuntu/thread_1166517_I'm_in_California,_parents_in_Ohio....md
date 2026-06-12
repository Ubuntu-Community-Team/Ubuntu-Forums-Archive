---
title: "I'm in California, parents in Ohio..."
date: 2009-05-21
forum: New to Ubuntu
---

### Post by ricardisimo on 2009-05-21
After my folks run the basic install off of the LiveCD, is there any way for me to take over the fine-tuning remotely? Adding repositories, installing apps, downloading their photos and videos, etc.? How would this be done, if it is possible at all? Thanks in advance.

---

### Post by Zzl1xndd on 2009-05-21
Have them enable the remote desktop option, and you should be able to log in using Remote desktop viewer. I use it now to Administer my Mothers Mac its rather handy.

---

### Post by Aaardwark on 2009-05-21
It is definitely doable. I recommend you read up on ssh.

---

### Post by ricardisimo on 2009-05-21
Found it... doesn't it seem odd that Remote Desktop would be in "Preferences" rather than "System"?

What is "ssh"? Where would you recommend reading up on it? Just Google it, or some site in particular?

---

### Post by mrbiggbrain on 2009-05-21
ssh is the secure shell, it basicly allows you to use an encrypted connection to administer shells. in laymens terms, you could be across the world and use there command prompt like your right there. 

the longer answer is that SSH is technically a tunneling and authentication system. it is commonly used to tunnel other programs though, giving them point to point encryption, and is used by enterprise router, siwthches and servers. in the normal sence iv said, it tunnels there shell through.

so you can feel safe useing passwords, or even credit card info, anything you dont mind being tunneled securly over the internet.

---

### Post by Miljet on 2009-05-21
ssh stands for secure shell. It is by far the easiest, and safest, way to set up a home network.

There are many tutorial and how-tos about setting up ssh. Here is a start.

[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

You can Google for others or follow some of the links on Herman's page.

---

### Post by ricardisimo on 2010-03-15
Hello all. So, I got what I thought was all of the pertinent information on my parent's computer and connection, and had them check the appropriate tick boxes within their Remote Desktop Preferences. But nothing.

How do I get their exact host name and such? Thanks.

---

### Post by J V on 2010-03-15
Isn't vnc encrypted anyway?

Doesn't matter, give them a gconftool-2 script to setup the vnc, get their IP, and then disable VNC through itsself when you are done with it...

---

### Post by ricardisimo on 2010-03-15
VNC? I thought I was using SSH?

Where would I get such a script? Why a script? I have to assume there is an app or a file/folder on their system right now where they could get the proper info, or at least email me a copy of it and have me do the rest.

---

### Post by J V on 2010-03-15
vnc lets you see the other persons desktop, ssh is a more secure version (but the amount of work you would need to do to get it up and running from afar isn't worth it IMO)

You write a script...

Basicly, type in man gconftool-2 for a manual, and pop open the gconf-editor to find vinagre, then make a list of commands that will setup the vnc for them, send them the file, they double-click, and voila, you can get in...

---

### Post by ricardisimo on 2010-03-15
I'm finding almost nothing at all regarding VNC in gconftool-2. When I run ```
gconftool-2 -R /desktop/gnome
```in a terminal, I do get
```
  vnc_password = ***********=
  authentication_methods = [vnc]
```
... along with probably a lot of other stuff that gets run off the top of the terminal, because there is evidently too much information [separate question: How do I get terminal to return info one page at a time, for any command, instead of all at once?]

Is this what I need from them? The vnc_password? I'm not seeing anything else in gconftool-2 that seems appropriate.

---

### Post by ricardisimo on 2010-03-17
What's the easiest way for me to get the VNC information from my parents' computer? thanks.

---

### Post by anewguy on 2010-03-17
My limited understanding of vnc is that it requires quite a bit of work to get going.  I tried it once and had a heck of a time going across the net to somewhere else instead of within a local network.

In researching that, I found reference to something called terminal server client, supposedly under applications/internet (or maybe you need to add it from the package manager?).  I never tried it as I got so frustrated with vnc trying to do exactly what you are trying to do (I'm in Minnesota, my folks - 78 years old - are in Arizona).

Since others seem to have vnc working, and since it is a new experience for you, I hope someone will post back with some easy to follow step-by-step procedures to get it running for you, including what has to happen on your parents end as well.

In the mean time you may want to check tsclient - I don't know if it goes across the internet or just with a local net.

Dave ;)

---

### Post by derrick81787 on 2010-03-17
**[SIZE="4"]SSH[/SIZE]**

SSH is very easy to install, and if you are good with the command-line, it might be all you need.  It basically just opens a shell on the remote computer, and from there you can do whatever you want.  To set it up on their machine, you only need to run the command:
```
sudo apt-get install openssh-server
```
I think that the client is installed by default in Ubuntu, so you shouldn't have to do anything to your computer.  If it isn't, then
```
sudo apt-get install openssh-client
```
will install it.  Then to log in to a command prompt on their computer, you would run:
```
ssh username@parents_ip_address_or_host_name
```
You will need a user account on their computer, or you could just use theirs.  If your username on their computer is the same as the one on your computer, you can leave out the username part and just run:
```
ssh parents_ip_address_or_host_name
```
Your parents will need to make sure that port 22 is open on their router/firewall.

More information on configuring SSH can be found [here ]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")and [here]("https://help.ubuntu.com/7.04/server/C/openssh-server.html"), but the defaults work well.

**[SIZE="4"]VNC[/SIZE]**

VNC will allow you to see exactly what is on their screen and to control it just as if you were sitting there.  You will have to set up a VNC server on your parent's computer, and you will have to install a client from the repositories on your computer.  The clients are all easy to use, though.  Setting up a regular VNC server to use from a LAN is pretty easy, but there are a couple of problems when using it over the internet.  First of all, it's not encrypted, so for it to be secure, you need to use it in conjunction with SSH.  That can be done, but I've never personally done it.  Second of all, VNC is typically kind of slow, even on a LAN, and it will be even more so over the internet.  It should still work, though, as long as you don't mind it being kind of laggy.

You can find information on VNC servers [here]("https://help.ubuntu.com/community/VNC/Servers"), VNC clients [here]("https://help.ubuntu.com/community/VNC/Clients"), and just information about VNC in general [here]("https://help.ubuntu.com/community/VNC").

The general VNC page has information about how to configure VNC with SSH.  I recommend reading most or all of the page, but look specifically at the section titled **Accessing your PC over the Internet** (this is not the **Accessing your desktop over the Internet** section.  Look farther down the page).  Just remember that *your* PC is actually your parents PC.

I hope this helps, and good luck.

- Derrick

---

### Post by AlanR8 on 2010-03-17
I used to use VNC all the time to administer a business network that was based on NT4 Servers and WIN2K desktops.

When using VNC, or Remote Desktop across the Interweb, you need to know the external IP address of your parent's machine.

Fortunately, this is simple in Ubuntu. On the client machine, just right click the network icon then select "Connection Information". The IP address is there for you.

You will have to enter this address as the server to connect to in your Remote Desktop Viewer application (Found under Internet) in you main menu.

That said, and someone with more Linux experience than me may be able to help here, you may also have to open a port on the parent's router to allow the remote session access.

Let us know how you get on.

---

### Post by no2498 on 2010-03-18
i live in the south end of columbus high st an 270
i have 710,804,910 on disk if they live close i can help
just thinking if its loaded on their computer it may help you
and im as lost as you on the remote !

---

### Post by ricardisimo on 2010-03-18
> **no2498 said:**
> i live in the south end of columbus high st an 270
i have 710,804,910 on disk if they live close i can help
just thinking if its loaded on their computer it may help you
and im as lost as you on the remote !

Ha! Thanks, no need. They are up in Cleveburgh. Please don't offer to drive up there to help, cuz I'll know you're preying on old folks. ;)

---

### Post by no2498 on 2010-03-19
lol no i dont like Cleveland
but no im 56 my self and have a wife
was just thinking if they was close is all 
all the luck to ya

---

### Post by ricardisimo on 2010-04-01
I just looked at my ssh_config file to see what it looks like, and I noticed that the standard port (Port 22) is commented out. Do I need to uncomment it on mine and theirs? Just on theirs? Not at all? Which combination? Thanks.

---

### Post by ricardisimo on 2010-04-06
OK. So I've managed to talk them through to the terminal, copying and pasting:
```
sudo apt-get install openssh-server openssh-client
```
And, I also got them to open their connection information window, take a screenshot of it and send it to me by email. I think all of the basics should be in place here.

Let's suppose the account in question is mom@parents-desktop, and let's say their connection is 123.456.7.89. I'm ricardisimo@home-desktop, with the connection 987.654.3.21... Now what?

Thanks again, and sorry for the hand-holding, but I'm clearly not getting this.

---

### Post by Calash on 2010-04-06
You are going to run into a problem if they are behind a router.

ie: if their IP address begins with 192.168 it is a NAT address an will not accept a direct communication without some port forwarding.  There are other addresses as well, but most consumer level routers give you a 192.168 subnet.

Probably the best way to tell is to try and ping the address you got from them.

In a terminal type

ping XXX.XXX.XXX.XXX

xxx being the address.  See if you get a reply.  CTRL-C will stop the pinging.

---

### Post by lemuriaX on 2010-04-06
Once you get the port forwarding set up you'll probably want to change their SSH server to listen on a different port than default 22. Also make sure the password is very good, possibly take some other security precautions by reading up on SSH server.

---

### Post by ricardisimo on 2010-04-06
Uggh... so I pinged, and zilch.
```
From 192.168.1.2 icmp_seq=1 Destination Host Unreachable
171 packets transmitted, 0 received, +168 errors, 100% packet loss, time 170855ms, pipe 4
```
So, the next question - I guess - is: What is "port forwarding"?

---

### Post by Calash on 2010-04-06
That is a local IP.  You are not going to be able to directly access their computer using it.

Port forwarding requires a setting change in their router.  To simplify, you need to tell the router to send all traffic from port X to 192.168.1.2.  X being the port of whatever remote control you will be using. 

This configuration will depend on the router they are using and may take a bit to talk them through.  

Something like Logmein.com would be a good alternative, but unfortunately they do not have any linux clients.  If somebody has an alternative it would help alot.

---

### Post by Objekt on 2010-05-11
Watch this thread for my confused, frustrated posts, as I try to get remote administration working on my mom's netbook, which runs Ubuntu Netbook Remix.

For now, she is close enough to stop by so I can tinker with it.  I'd like to test remote access while the target machine is still physically present at my house, as that would make it a lot easier to fix any problems.  Is there a way to do a realistic test, without the netbook being connected outside my home network?  I need to somehow redirect its traffic so that it acts as if it were connected to a random access point elsewhere (an airport or a Starbucks, for example).

Adding to the complexity, my home network is behind a router doing NAT.

---

