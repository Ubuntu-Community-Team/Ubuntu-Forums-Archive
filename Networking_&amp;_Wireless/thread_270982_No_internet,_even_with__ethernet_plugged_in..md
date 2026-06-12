---
title: "No internet, even with  ethernet plugged in."
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by mztriz on 2006-10-04
Okay today I installed ubuntu 6.06 on my friends gateway w730-k8x laptop, but the 'net isn't working. I'm not sure why, even if I plug it in it doesn't detect it. Any ideas? I feel kind of bad for leaving her internet-less...](*,) 

Thanks everyone, 
Ava.

---

### Post by malnacido on 2006-10-04
I have a slightly different, but similar problem. I also own a gateway laptop that has a Marvell Yukon Ethernet controller. I get internet for some of the time and then when I begin downloading a big file, say from the repository, internet access cuts out and i have to deactivate the ethernet adapter and reactivate it in order for internet to come back. And it is a continual problem. Any fixes??](*,)

---

### Post by mztriz on 2006-10-04
Ahh, someone pleaseee help me. This is her only way of acessing the intnernet and she needs it; we're both in college and it's the only way she can do certian assignments. I don't live on campus.

---

### Post by Iowan on 2006-10-04
Dual-boot might be a good option - but probably kinda late now...
Probably gonna need more information.  
1. Is the NIC recognized? 
2. Is it activated?
3. Is machine set up with static or DHCP address?
4. Is the machine getting an IP address?
5. Can you ping another computer?
6. Can you ping a website?

Naturally, the answer to one question may affect (or nullify) another question.

---

### Post by dannyboy79 on 2006-10-04
Iowan, when you ask people stuff like this you probably should assume that since they are here asking the question they don't know how to give you that info to begin with.

mztriz, if you know how to get this info than i apologize for assuming you were a newbie. if you are a newbie, give us the results of the following. go to a terminal and type in (note: for the dmesg one, only look for things that relate to your nic card or aything that says eth0 or anything that looks like it's relavent.)

lspci -v

dmesg

you could also go to system, admin, networking, does a ethernet connection show up there? if so, try to do what iowan says, deactivate it, and then activate it waiting a minute between clicks. if eth0 is there, click on properties, what does it say as far as dhcp or static? give us this info and we can help from here.

---

### Post by Iowan on 2006-10-04
> **dannyboy79 said:**
> Iowan, when you ask people stuff like this you probably should assume that since they are here asking the question they don't know how to give you that info to begin with. Because this isn't the **Absolute Beginner** section, I presume a bit more experience.  If someone needs more help getting that information, I'll be happy to try (as I'm sure you will).

---

### Post by doobit on 2006-10-04
dmesg by itself will give you a whole lot of information to sort through. Before you do anything else, plug in the internet cable and type in a terminal ```
ifconfig
``` Tell us what it says.
Most all NICs work with the latest Linux Kernels.

---

### Post by Iowan on 2006-10-04
I neglected to mention ipv6 as a potential problem source, but let's start with the basics...

---

### Post by dannyboy79 on 2006-10-04
> **Iowan said:**
> Ever seen the breakdown of as*_u_me? ;)  
Were this the **Absolute Beginner** section, I'd agree cuz I wouldn't necessarily expect a beginner to know how to find the information. Because it isn't, I **presume ** that they either know how or will ask if they need help finding the info.

What, are you 5? 

I am here to help people, you're obviously here to waste peoples time by posting answers that are incomplete. You also the reason why threads get to be so long!

---

### Post by handy on 2006-10-04
Have a look at **post 8** [here]("http://ubuntuforums.org/showthread.php?t=269808"), it is quick & easy & may be all you need.

---

### Post by matthew on 2006-10-05
> **dannyboy79 said:**
> [QUOTE=Iowan]Ever seen the breakdown of as*_u_me? :wink:  
Were this the **Absolute Beginner** section, I'd agree cuz I wouldn't necessarily expect a beginner to know how to find the information. Because it isn't, I **presume ** that they either know how or will ask if they need help finding the info.What, are you 5? 

I am here to help people, you're obviously here to waste peoples time by posting answers that are incomplete. You also the reason why threads get to be so long![/quote]Umm...I suggest we all take a deep breath and get back to helping the OP with the problem instead of this silliness that each of you are displaying. I think both of you started out with good intentions and each of you have misunderstood the other. Let's just move on. Thank you.

---

### Post by mips on 2006-10-05
There are some known issues with Marvel chipsets, do a search here but carry on below so long.

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.
[I]
If you are dual-booting install the **ext2ifs** driver in windows and access your ext2/3 partions in linux from windows if you want to transfer data across in order to paste here. Alternatively use a usb memory stick or stiffy disk.[/I]

---

### Post by dannyboy79 on 2006-10-05
i find it funny that we have posted so many responses to help this person and they haven't posted what we asked for. How can we help people if they aren't going to help us help them???

---

### Post by mztriz on 2006-10-08
I did a dhclient and it detected the network, then I installed the drivers for the wireless card. Her internet is from our university so it's a bit confusing. The only problem is everytime we go to a new location on campus we have to do dhclient. I added auto eth0 and eth1 lines in the config, but it just doesn't work ?

I don't have her laptop with me right now, but I will have it tomorrow or tuesday so I can do a ipconfig -a and all of that. 

Thanks for your help everyone :D

---

### Post by Number6 on 2006-10-08
Yea I've had the same problem! Everything was fine after the LiveCD install, but once the update completed and the machine rebooted, suddenly no internet, and no ipv4 address assigned via DHCP.
When I run dhclient eth0 the ipv4 address is assigned and of course all is well, but I want this to happen at bootup, any ideas what to do here?

---

