---
title: "HOW TO: Share internet to another computer though Two NICs using Ubuntu"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by will71110 on 2007-08-29
I have seen a lot of treads asking how to share internet to another computer though two NICs.  NAT is the answer. (This lesson assumes you know a little bit about networks and how to configure NICs on Ubuntu.)

If you are running Ubuntu and this is how you want to set it up:

**Internet < RJ45 > ADSL Router < CAT5 > (NIC1) Ubuntu Computer (NIC2) < CAT5/Wireless/Other > Other PC, Xbox, Switch or anything else you want to share**. (this setup work a lot better then ICS might I add)

This guide will help.  It will also help if you want to share your VPN with your internal network if your VPN server is Ubuntu.

Before you start, make sure you **statically assign** an IP address to NIC2 and the boxes behind there especially if you are not using DHCP server on the Ubuntu box (the 2 NICs do not have to be on the same IP subnets since we will be NATing).

The **gateway **of all the boxes behind NIC2 should point to **NIC2**. (DNS still points to the ADSL Router or equivalent).  If your ADSL router hands out DHCP then you will not have to set a static IPs on NIC1. If it does not, go ahead and statically assign that too.

Now you need to list your NICs

**>ifconfig &#8211;s**

That should give you a short list of your interfaces. Your interfaces will probably be listed like ethX (where X is a number).  If you want to share a VPN connection you&#8217;ll probable see hamX or pppX.

In this lesson I&#8217;m just going to use eth0 (NIC1) and eth1 (NIC2) as examples.  Fill in where it fits your needs.

Now that I know what NICs I want to use, now I need to tell Ubuntu  that I want to port forward.  This command will do this for you. (IMPORTANT: Some advice, make a script and put these next command in it because when you reboot the computer, these commands don&#8217;t save)

**>sudo echo 1 > /proc/sys/net/ipv4/ip_forward**

This next command flushes the iptables (you do not have to do this but I like to rid of any problems that might be in the iptables before I start)


**>sudo iptables --flush**

(Next is the part to actually tell Ubuntu to NAT and what type of NAT)

[B]>sudo iptables &#8211;t nat &#8211;A POSTROUTING &#8211;o eth0 &#8211;j MASQUERADE
>sudo iptables &#8211;A FORWARD &#8211;i eth0 &#8211;o eth1 &#8211;m state --state RELATED,ESTABLISHED &#8211;j ACCEPT
>sudo iptables &#8211;A FORWARD **-i** eth1 &#8211;o eth0 &#8211;j ACCEPT[/B]
(End the script here if you wrote one. You&#8217;ll have to add in a line that points to your script in the local.rc file located under /etc if you want it to load the script every time you reboot.)

That should get you going.  If you have any question about this, let me know and I&#8217;ll try and answer the best way I can.

This was tested on Ubuntu only but it will probably work on other distros.

---

### Post by newbieal on 2007-08-31
I'm new to Ubuntu, and I've been trying to get masquerade to work for a couple of weeks. So I followed your instructions, and had two problems:

1. When I entered the command "sudo echo 1 >/proc/sys/net/ipv4/ip_forward" I got a permission denied response. How do I get around that?

2. The second "forward" command was rejected until I put a "-i" in front of eth1. Was that correct? (I was trying to make it look similar to the first command.

FYI, I tried using Firestarter to configure iptables which didn't work. I think there may have been a problem with the ports used by Samba.

Your reply would be greatly apprecieated.

Newbieal

---

### Post by elvinatom on 2007-09-01
I like the guide, easy and straight to the point - but this really made my day:
"There are only 10 type of people in the world, those who understand binary and those who don't"

---

### Post by will71110 on 2007-09-03
Made a mistake.  forgot a -i in last command.  :) edited it

---

### Post by will71110 on 2007-09-03
> **newbieal said:**
> I'm new to Ubuntu, and I've been trying to get masquerade to work for a couple of weeks. So I followed your instructions, and had two problems:

1. When I entered the command "sudo echo 1 >/proc/sys/net/ipv4/ip_forward" I got a permission denied response. How do I get around that?

2. The second "forward" command was rejected until I put a "-i" in front of eth1. Was that correct? (I was trying to make it look similar to the first command.

FYI, I tried using Firestarter to configure iptables which didn't work. I think there may have been a problem with the ports used by Samba.

Your reply would be greatly apprecieated.

Newbieal

Not sure why you got access denied.  Try a reboot, could be something had ip_forward locked. Since you said you had firestarter installed, that might be why your getting the ip_forward denied access.

For #2,  yes you were right to put a -i there.  I have now fixed that :).

---

### Post by drmynatt on 2008-03-04
Hello- I too had a problem with ip_forward permissions. Is there a way to flush that setting or override it?

This is the easiest two-NIC setup I've seen, but I still can't get it to work.

I do see lo, eth0, and eth1 using Network Tools and iptraf and now I see also for the first time that lo has hits; have not seen that before.

However, I still can't get it to work.

Any help getting my two-NIC Ubuntu box to work would be *greatly* appreciated.

Thank you,

DAve

---

### Post by drmynatt on 2008-03-04
I figured it out with a lot of help; use quotes:

sudo "echo 1 > /proc/sys/net/ipv4/ip_forward" 

That resets the ip_forward setting. Not sure can do both ipv4 and ipv6 at same time??

I think that works; it did for me.

Dave

---

### Post by drmynatt on 2008-03-04
Does this configuration mean that the Ubuntu box functions as a router only... I need the box to be a workstation too and be able to access the internet as well as the boxes behind it.

Internet>>Modem>>Ubuntu>>Hub>>Other Machines

Can this config be adapted -or does it permit- the Ubuntu to be used as a workstation too?

Dave

---

