---
title: "Trouble changing from Windows Network to a Linux-configured network."
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by Drew_[SCED] on 2008-07-08
I'm taking all the computers in this house and converting them to Ubuntu Hardy.  Currently 2/3 of the computers run Hardy, including this one, the desktop connected to the Linksys WRT54G router.  Before, everything ran Windows XP and the old Windows Network remains.

I would like to be able to set up static IPs and transfer files through an unencrypted wireless network.  However, I'm running into problems.

[This](http://ubuntuforums.org/showthread.php?t=684495) thread isn't helping, see the included screenshots.

Any help?  I'm not sure if I need Samba, or if I want it, since all the computers will run Hardy.

Screenshots: first is the info for the current network, second is the errors I received on following the sticky.

Thanks in advance.

EDIT: In case it isn't clear, this computer is connected through ethernet and the other two are connected wirelessly.  I CAN connect to the internet but I CANNOT read other computers.

---

### Post by ikonia on 2008-07-08
your using a guide for wirless networks when you don't have a a wireless network device in this computer.

You've confirmed this in IRC to me also.

I've given you the links

As your at a basic level for linux this guide should help you get the basics down and get you learning faster
[https://help.ubuntu.com/8.04/newtoubuntu/C/index.html](https://help.ubuntu.com/8.04/newtoubuntu/C/index.html)


Gives you a guide on switching from windows - which you said is your goal
[https://help.ubuntu.com/8.04/switching/index.html](https://help.ubuntu.com/8.04/switching/index.html)

Gives your the basics of networking in ubuntu
[https://help.ubuntu.com/8.04/internet/C/basics.html](https://help.ubuntu.com/8.04/internet/C/basics.html)

---

### Post by Drew_[SCED] on 2008-07-08
> **ikonia said:**
> your using a guide for wirless networks when you don't have a a wireless network device in this computer.

You've confirmed this in IRC to me also.

I've given you the links

As your at a basic level for linux this guide should help you get the basics down and get you learning faster
[https://help.ubuntu.com/8.04/newtoubuntu/C/index.html](https://help.ubuntu.com/8.04/newtoubuntu/C/index.html)


Gives you a guide on switching from windows - which you said is your goal
[https://help.ubuntu.com/8.04/switching/index.html](https://help.ubuntu.com/8.04/switching/index.html)

Gives your the basics of networking in ubuntu
[https://help.ubuntu.com/8.04/internet/C/basics.html](https://help.ubuntu.com/8.04/internet/C/basics.html)
I'm aware I'm using the wrong guide.  I can't find a guide for my situation, so I posted.

---

### Post by ikonia on 2008-07-08
the links I've posted explain how to setup networking in ubuntu, how to get your windows network settings and how to generally use ubuntu.

they are great docs.

---

### Post by Drew_[SCED] on 2008-07-08
I tried going into System -> Administration -> Network and setting up a static IP there, but it doesn't seem to be working since, checking my ports, they're still closed.  (Connection refused)

Then I tried dhcp, that didn't work either. (t/o)

Also, that doesn't solve anything about my desire to interact with other computers on this network.

---

### Post by ikonia on 2008-07-08
read the guides I posted - it will explain 

a.) how to setup a network interface
b.) how to get your windows network settings so you know the current network
c.) how to interact your ubuntu machine with the windows network.

Pay close attention to the text in the guides, not just the commands.

---

### Post by Drew_[SCED] on 2008-07-08
Still not working.  I have read the internet section, followed the troubleshooting instructions (including turning off IPv6) and still nothing.

Furthermore, the sections that require pinging don't work with the IP address given.  I'm assuming it's supposed to be [www.ubuntu.com](www.ubuntu.com) but even putting it into my browser just gives me a t/o.  Inputting [www.ubuntu.com](www.ubuntu.com) gives me a successful ping, however.

So basically what I'm left with is a useless guide and no one helping me.

EDIT: looking at devices in network tools, my eth0, when I try to confgure it, gives me this: "That interface does not exist, check to see that it is correctly typed and is correctly supported by your system."  Is this helpful?

---

### Post by ikonia on 2008-07-08
your attitude is pretty poor, I've spent 40 minutes explaining the problems with your old guide, I've dug out useful guides for you, so "no-one helping" is pretty insulting.

As for the guides being useless, I suspect its more a case of user error (such as trying ti configure a wirless network on a machine with no wirless card) rather than the official documentation being poor.

If you want help - give specifics.

Show me the part your having problems with then it can be worked through.

I don't understand why your following the internet section as you said in your earlier post "I can connect to the internet, just not the internal lan" ?

Let me have a quick scan to see if I can find the bit your reading.

---

### Post by Drew_[SCED] on 2008-07-08
> **ikonia said:**
> your attitude is pretty poor, I've spent 40 minutes explaining the problems with your old guide, I've dug out useful guides for you, so "no-one helping" is pretty insulting.

As for the guides being useless, I suspect its more a case of user error (such as trying ti configure a wirless network on a machine with no wirless card) rather than the official documentation being poor.

If you want help - give specifics.

Show me the part your having problems with then it can be worked through.

I don't understand why your following the internet section as you said in your earlier post "I can connect to the internet, just not the internal lan" ?

Let me have a quick scan to see if I can find the bit your reading.
All you did was tell me that I was making mistakes and giving me Ubuntu 101.  You didn't tell me what the problem was.  You told me to help myself.  That's like telling an illiterate to read a book.

My problem is twofold:
[list]
[*]I can't forward any ports.
[*]I can't connect to any other computers on the network.
[/list]

I've said this umpteen times but you are still telling me the same things over and over.  I've given hardware information, I've told what I've done so far, and I've given configuration information.  The only thing left is to invite you over and have you sit at the computer.

---

### Post by ikonia on 2008-07-08
the IP address in the guide 82.211.81.158 resolves to arctowski.canonical.com, which now has an ip address of 91.189.94.158 so it looks like that IP address has changed, I'll log a request to have that updated, however common sense suggests you could test this with any ip address that is on the internet, which if you read the text of the trouble shooting, explains what it's doing, so you should be able to work that out.
 

I'll leave you to dig your own mess now as you are not being helpful in this thread in resolving your issues, your contradicting yourself in your posts which makes it pretty hard to work out whats real with your setup and what's not.

> 
EDIT: In case it isn't clear, this computer is connected through ethernet and the other two are connected wirelessly. I CAN connect to the internet but I CANNOT read other computers.


If you can connect to the internet, why are you following the connect to the internet guide ??


> I'm aware I'm using the wrong guide. I can't find a guide for my situation, so I posted. 


your not aware it's the wrong guide - or you wouldn't be blindly typing wirless commands into a machine with not wirless card in it, and then saying "I don't know why it doesn't work" and when I question you on why you where using a wirless guide you said you didn't know it was a wirless guide, try being honest and saying "I don't know" rather than "I know I know"

To me this looks like your flying blind, just typing things and not understanding what your doing.

You'll get a lot better response if you give more detailed responses to the problems, 

such as "I'm reading this section [ paste line ] and when I do this command [ paste command ] I get this response [ paste command ]

Please and thank you goes a long way too, rather than "I'm getting no help, this is all rubbish"

---

### Post by ikonia on 2008-07-08
> **'Drew_[SCED] said:**
> All you did was tell me that I was making mistakes and giving me Ubuntu 101.  You didn't tell me what the problem was.  You told me to help myself.  That's like telling an illiterate to read a book.

My problem is twofold:
[list]
[*]I can't forward any ports.
[*]I can't connect to any other computers on the network.
[/list]

I've said this umpteen times but you are still telling me the same things over and over.  I've given hardware information, I've told what I've done so far, and I've given configuration information.  The only thing left is to invite you over and have you sit at the computer.


This is just nonsense now.

1.) I gave you the basic ubuntu guides as you come across as not understanding much about what your doing - they are good guides for any beginner, and if your going to run this network, you'll need to understand the basics. 

2.) you've given me no hardware information, other than 2 PC's have wirless, and I told you that one of them doesn't (hence the wirless guide failing)

3.) no where in this question do you mention not being able to port forward or wanting to port forwarding, nor did you mention this in IRC

4.) you can't connect to any other computers on the network, then why are you trying to ping the internet ??? surly you want to check the machines on your local network (this is what I mean about not understanding the basics so READING the guides may help you get a basic grasp

5.) The only thing you've said you've done is follow a wirless guide for a non-wirless PC, do an internet connection guide when your already connected to the internet, then moan that two problems you didn't mention you wanted to do don't work.

---

### Post by Drew_[SCED] on 2008-07-08
> **ikonia said:**
> This is just nonsense now.

1.) I gave you the basic ubuntu guides as you come across as not understanding much about what your doing - they are good guides for any beginner, and if your going to run this network, you'll need to understand the basics. 

2.) you've given me no hardware information, other than 2 PC's have wirless, and I told you that one of them doesn't (hence the wirless guide failing)

3.) no where in this question do you mention not being able to port forward or wanting to port forwarding, nor did you mention this in IRC

4.) you can't connect to any other computers on the network, then why are you trying to ping the internet ??? surly you want to check the machines on your local network (this is what I mean about not understanding the basics so READING the guides may help you get a basic grasp

5.) The only thing you've said you've done is follow a wirless guide for a non-wirless PC, do an internet connection guide when your already connected to the internet, then moan that two problems you didn't mention you wanted to do don't work.
The first one I did and when it failed I came to the channel and you pointed out why it failed.

The second one I did because *you gave it to me*.

The other two machines connect to the internet just fine.  And I've followed this guide: [https://help.ubuntu.com/8.04/internet/C/networking.html](https://help.ubuntu.com/8.04/internet/C/networking.html) as well, and I'm not getting anywhere.

You've given me, AGAIN, basic guides that aren't helping.  Because I made one mistake in the beginning, you're assuming that I can't do anything right.  I've followed those guides perfectly however.  I understand the basics, else I wouldn't be connected to the internet *at all*.  I followed the (obviously useless) guides because you told me to, though I knew they wouldn't work (which is why I said, at the beginning, that you were giving me useless information).

By the way: I mentioned in the IRC that I wanted help with forwarding.  I know I did.  Anyone can check the logs.

So for the love of God, please understand my problem and offer advice on it.  Don't lecture me on how I asked or anything else.  Just help.

---

### Post by ikonia on 2008-07-08
Ok - heres the summary of what you need to do.


1.) What is your device your port forwarding with - I assume it's your internet router, your ubuntu machine needs to be on the same network as your router to be able to use it. To do this most routers give out a dhcp address, that will assign an IP address, netmask, gateway and dns servers, make sure the gateway is the INTERNAL ip address of the router. (assumption due to lack of info)

2.) make sure your on the same network and subnet as your network router, ping it to see if it responds

3.) ping the IP addresses of the windows PC's to confirm your on the same network as them - they should have iP addresses on the same network as the router too (I'm again making the assumption that your router is your internet gateway).

4.) if your assigning static IP addresses, make sure they don't conflict with the DHCP range of the router, make sure they are on the same network as the router and other PC's on the network, make sure the network mask is right and the DNS servers are reachable, and most importantly make sure the default route is your internet gateway/router.

That is the networking side of things, once you've got that working and setup correctly we can talk about accessing files.

Let me know when your done and working.

---

### Post by Drew_[SCED] on 2008-07-09
> **ikonia said:**
> Ok - heres the summary of what you need to do.


1.) What is your device your port forwarding with - I assume it's your internet router, your ubuntu machine needs to be on the same network as your router to be able to use it. To do this most routers give out a dhcp address, that will assign an IP address, netmask, gateway and dns servers, make sure the gateway is the INTERNAL ip address of the router. (assumption due to lack of info)

2.) make sure your on the same network and subnet as your network router, ping it to see if it responds

3.) ping the IP addresses of the windows PC's to confirm your on the same network as them - they should have iP addresses on the same network as the router too (I'm again making the assumption that your router is your internet gateway).

4.) if your assigning static IP addresses, make sure they don't conflict with the DHCP range of the router, make sure they are on the same network as the router and other PC's on the network, make sure the network mask is right and the DNS servers are reachable, and most importantly make sure the default route is your internet gateway/router.

That is the networking side of things, once you've got that working and setup correctly we can talk about accessing files.

Let me know when your done and working.
I've done that all except for pinging the Windows PCs because there are no Windows PCs.  If you'd like me to ping one or both of the other Ubuntu PCs, I will.

Oh, by the way, I'm only assigning a static IP to the desktop.  The laptops are on roaming mode.

---

### Post by ikonia on 2008-07-11
ok, so if you can see the other PC's on the network, you need to decide how you want to share resources on them, and how you want to access them.

NFS/Samba/SSH/ftp/http/rsync

All ways at sharing/accessing files, have a think about which one would suit you best.

---

