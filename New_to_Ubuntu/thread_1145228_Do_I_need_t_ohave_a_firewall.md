---
title: "Do I need t ohave a firewall"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2009-05-01
I like to know do I need to have a fire wall running or do Ubuntu have a default firewall in built or do I've to install one.

---

### Post by jbrown96 on 2009-05-01
Ubuntu has a firewall called ufw. You can read more about it with ```
man ufw
``` I don't think that it's active by default, but I'm not really sure. It doesn't really matter though. Ubuntu has all ports closed by default, so a firewall is only needed if you want to manage open ports. 

If you install anything that needs an open port (apache, openssh-server, etc.), it will automatically open the required ports in Ubuntu. 


Ufw is frontend to Iptables which is a very powerful firewall. however, it's really complicated, but if you are interested in firewalls, take some time and learn it.

---

### Post by sadaruwan12 on 2009-05-01
Thank you

---

### Post by renjithforever on 2009-05-01
i got firestarter from ulitmate edition.... should i be using it... is my ubuntu secure by default?

---

### Post by mjitkop on 2009-05-01
You can check with [ShieldsUp!]("https://www.grc.com/x/ne.dll?bh0bkyd2") to see what ports are currently open on your computer with Ubuntu. I did it last night with a default installation of Ubuntu 9.04 "Jaunty Jackalope" and I was pleasantly surprised to see that ShieldsUp! reported that my computer was 100% in stealth mode. In other words, my computer with Ubuntu is completely invisible on the internet and I didn't even install a firewall. :)

---

### Post by Dragonbite on 2009-05-01
There is a site you can go to which will scan your internet connection for open ports.  

[http://www.auditmypc.com/]("http://www.auditmypc.com/")

I used that when I was trying to get my webcam working.

I believe Ubuntu has the firewall on by default, and ufw is just the gui (CLI "gui"?) for managing the firewall.```
sudo ufw status  (display the status)
sudo ufw disable (disable the firewall)
sudo ufw enable (enables the firewall)
sudo ufw app list (shows services the firewall allows, like CUPS)
sudo ufw allow 5100 (opens port 5100)
```


If you are connected right off the modem, then a firewall is highly recommended to have running.

I have my modem connected to a dedicated firewall/router/content filter so anybody would have to get past that. If they did then they would reach my wireless router's firewall. Then if they passed that they would have to get through my local one as well.

---

### Post by mjitkop on 2009-05-01
> **renjithforever said:**
> i got firestarter from ulitmate edition.... should i be using it... is my ubuntu secure by default?


Check [here]("https://help.ubuntu.com/9.04/keeping-safe/C/firewall.html"). That's where I got the link for ShieldsUp!

---

### Post by brunogirin on 2009-05-01
The [Ubuntu firewall wiki page]("https://wiki.ubuntu.com/UbuntuFirewall") is a good start.

---

### Post by binbash on 2009-05-01
you do not need any firewall unless you are using a server

---

### Post by Mortus Pryde on 2009-05-01
Pretty much what others have said. Ubuntu has all ports fully closed by defualt unless a program otherwise requests them to be open or visible. You really only need a firewall if you are running a server, peer to peer sharing, and other software that may require or allow other computers to initiate contact. Otherwise you really only need it enabled for you own peace of mind or if you are connecting to untrusted networks, say on a laptop at your local Starbucks or in a Hotel while you are traveling.

For example I will have anti-virus (Avast 4 Linux) and firewall eventually activated on my laptop for this reason. It will travel with me on vacation, and I may well want to check e-mail, use the internet or connect to SecondLife or OpenLife. While doing so I want the peace of mind that a malicious machine will not be able to allow access to mine and that I do not contract or pass along a virus.

---

### Post by stwschool on 2009-05-01
Just adding one last little thing, try adding gufw if you want a nice easy GUI for managing your ufw setup. Ubuntu's pretty damn secure but a little more can't hurt right?

---

### Post by Mortus Pryde on 2009-05-01
Hoping I am not getting to far off topic, but may be useful for the OP as well should he/she decide its worth the peace of mind to run a firewall.

gufw vs Firestarter, which would you recommend overall for managing a systems firewall relatively quickly and easily?

---

### Post by brian_p on 2009-05-01
> **sadaruwan12 said:**
> I like to know do I need to have a fire wall running or do Ubuntu have a default firewall in built or do I've to install one.

The short answer is 'no'. The longer answer would also probably be 'no' but you have provided no information on your present or future configuration so it is impossible to say.

---

### Post by brian_p on 2009-05-01
> **mjitkop said:**
> 

I was pleasantly surprised to see that ShieldsUp! reported that my computer was 100% in stealth mode. In other words, my computer with Ubuntu is completely invisible on the internet and I didn't even install a firewall. :)

ShieldsUp! reported on the state of your router, not your computer.

---

### Post by brian_p on 2009-05-01
> **Mortus Pryde said:**
> 

For example I will have anti-virus (Avast 4 Linux) and firewall eventually activated on my laptop for this reason. It will travel with me on vacation, and I may well want to check e-mail, use the internet or connect to SecondLife or OpenLife. While doing so I want the peace of mind that a malicious machine will not be able to allow access to mine and that I do not contract or pass along a virus.

My laptop travels too and listens for tcp connections on ports 22, 25, 53, 111, 113, 631 and 953. It also listens on some udp ports. My peace of mind comes from the software being up-to-date and configured correctly, not from using iptables.

---

### Post by Mortus Pryde on 2009-05-01
> **brian_p said:**
> My laptop travels too and listens for tcp connections on ports 22, 25, 53, 111, 113, 631 and 953. It also listens on some udp ports. My peace of mind comes from the software being up-to-date and configured correctly, not from using iptables.

True enough. ;) I am only committed to running anti-virus at this point, its just one of those things that I would rath have and have up to date and not need it, then find I am about to get hit by a meadior shower and need it.

---

### Post by blueridgedog on 2009-05-01
> **sadaruwan12 said:**
> I like to know do I need to have a fire wall running or do Ubuntu have a default firewall in built or do I've to install one.

My opinion is that the default install of Ubuntu is sufficiently secure that if placed behind a hardware router or NAT device, there is little additional security to be gained in installing a machine based firewall.

If you have a direct Internet connection (and not a connection behind the typical home router which has NAT and a firewall build int) then using one of the firewall options makes good sense.

If you decide to add network aware services (file sharing, ssh or a web server for example) that you want to restrict to your local network or to a specific list of systems, then a firewall would also be advisable at that time.

---

### Post by mjitkop on 2009-05-01
> **brian_p said:**
> ShieldsUp! reported on the state of your router, not your computer.

Thank you, brian_p. I stand corrected. ;) So then it makes no difference if Ubuntu itself is secure? :confused:

---

### Post by blueridgedog on 2009-05-01
> **mjitkop said:**
> Thank you, brian_p. I stand corrected. ;) So then it makes no difference if Ubuntu itself is secure? :confused:

Secure has many angles from which it can be viewed.  One definition implies a firewall protecting insecure services from being accessed.  Another implies not running unprotected services.  It may be hearsay from a modern net perspective, but my take is that Ubuntu behind a NAT router is secure, as secure as most are likely to need.  

Now, that said, if you travel a great deal and spend time accessing hot spots and other public network locations, then you may want to invest the time to setup a firewall as linked to by other posters.  I know what services my Ubuntu box is running and how they are setup and I generally don't run a firewall on top of the OS.  My take is that Ubuntu is secure as released and patched.

---

