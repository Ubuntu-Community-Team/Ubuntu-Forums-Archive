---
title: "Unable to connect to Internet (via Firefox)"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by alfonsos on 2007-03-18
I just installed Ubuntu 6.06 on my Windows xp computer (dual boot) from a live CD (Canonical). The live CD itself connected fine to the web. However, after I installed the OS onto my computer from the same CD, Ubuntu would not connect to the internet.(!) How can it connect via the CD live but not from the installed OS from the selfsame CD? How do I fix it? Reinstall?

I've been to the Absolute Beginner's forum with this question, but no resolution yet. So, I thought I'd post here also.

So far I've:

  - verified that my IP supports DHCP
  - tried enabling a network setting in Firefox (network.dns.disableipv6)
  - edited the blacklist file (blacklist ipv6)

I have not tried reinstalling - yet.

---

### Post by Floppyjoe on 2007-03-18
Is this both a wireless and a wired connection problem?

---

### Post by moshuptrail on 2007-03-18
Sounds like you've done all the obvious.  Next lets start narrowing down the problem.   You say you can't see anything with Firefox and I find that's usually a gateway or DNS problem.   Take a look at the output of ifconfig.  It should tell us if you've got an IP address from DHCP.

Post the section relevant to your connection (i.e. we don't need the output for lo, the loopback connector)

---

### Post by alfonsos on 2007-03-18
> **moshuptrail said:**
> Sounds like you've done all the obvious.  Next lets start narrowing down the problem.   You say you can't see anything with Firefox and I find that's usually a gateway or DNS problem.   Take a look at the output of ifconfig.  It should tell us if you've got an IP address from DHCP.

Post the section relevant to your connection (i.e. we don't need the output for lo, the loopback connector)

Here's the output from ifconfig:

eth0   Link encap: Ethernet HWaddr  00:08:A1:18:C9:78
         inet 6 addr: fe80::208:a1ff:fe18:c978/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
         Rx packets:1 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen: 1000
         Rx bytes:258 (258.0 b) Tx bytes:1836 (1.7 KiB)
         Interrupt:169 Base address: 0xd000

---

### Post by alfonsos on 2007-03-18
> **Floppyjoe said:**
> Is this both a wireless and a wired connection problem?

No, just a wired connection.

---

### Post by HereInOz on 2007-03-18
You will find that if you make the IP address a static IP, entering the internal IP address of your router as the gateway address, and then add the DNS addresses which will be provided to you by your ISP, you will most probably have a connection.

This is an issue with some routers, that they seem to not pass DNS information correctly under DHCP, so you need to hard code the IP address, gateway, and DNS addresses.

Hope this helps.

---

### Post by Mr. C. on 2007-03-18
Alfonsos,

Your NIC did not get configured with an IP address.

Please look at the output from "dmesg" at a Terminal window, and share relevant lines.  If you are unsure, run:

```
dmesg > dmesg.out
gzip dmesg.out

```
and attach the dmesg.out.gz file to your reply.

Also show output from

```
sudo lshw -class network
lspci
lspci -n
```

MrC

---

### Post by alfonsos on 2007-03-18
[QUOTE=Mr. C.;2318667]Alfonsos,

Your NIC did not get configured with an IP address.

Please look at the output from "dmesg" at a Terminal window, and share relevant lines.  If you are unsure, run:

```
dmesg > dmesg.out
gzip dmesg.out

```
and attach the dmesg.out.gz file to your reply.

Also show output from

```
sudo lshw -class network
lspci
lspci -n
```

MR C, I'm at a loss how to get the above info to you. 

1. I can't copy and paste (at least I don't know how to do it) between Ubuntu and Windows xp (via which I'm posting here). The output I supplied in an earlier post was manually transcribed from Terminal window to paper and then typed into Windows.

2. I don't know (yet) how to generate a file in Ubuntu, and then how to get it into Windows xp. If I could get to the internet, this barrier wouldn't be nearly as high.

Any ideas? I'm certainly willing to do the laborious transcription thing, I'd just ask you to be a little selective.

I apologize for my inability to communicate fully and smoothly, but yesterday was the 1st time I laid eyes on Ubuntu. I've managed to amass 8 beans in my career here.

Is there a direct way I can configure my NIC with an IP address?

Al

---

### Post by alfonsos on 2007-03-18
> **HereInOz said:**
> You will find that if you make the IP address a static IP, entering the internal IP address of your router as the gateway address, and then add the DNS addresses which will be provided to you by your ISP, you will most probably have a connection.

This is an issue with some routers, that they seem to not pass DNS information correctly under DHCP, so you need to hard code the IP address, gateway, and DNS addresses.

Hope this helps.

Hi ThereinOz, At someone's suggestion, I tried this or at least something like it. I just did the straightforward copying of Windows xp network info into Ubuntu under static IP (it didn't work). I looked at the network info when running the live CD and that uses DHCP; but I acknowledge there is *something* different between the live CD and the install that resides on the same CD. 

Al

---

### Post by Mr. C. on 2007-03-18
Do you have a floppy drive on both systems, and a spare floppy ?

MrC

---

### Post by HereInOz on 2007-03-18
OK, you set up a static IP in System > Administration > Network.  Did you set your gateway correctly, and did you click on the DNS tab and set up your DNS IP addresses as given you by your ISP?

Try this:

Open a terminal and type:
ping 72.14.207.99

If you get a response, then your internet connection is working on a TCP/IP level.  If not, the whole thing is not working for some reason.

If you do get a response, then type:
ping [www.google.com](www.google.com)

If this doesn't work, then the problem is assuredly DNS related.

---

### Post by Mr. C. on 2007-03-18
HereInOz - there is no IP address.  None of your suggestion can work until the interface has an IP address.

MrC

---

### Post by alfonsos on 2007-03-18
> **Mr. C. said:**
> Do you have a floppy drive on both systems, and a spare floppy ?

MrC

Even better - one computer (double boot). I had no idea linux could deal with a Windows format.

I attached 1 file: dmesg.out.gz   I'll send the rest tomorrow.

Al

---

### Post by alfonsos on 2007-03-18
> **HereInOz said:**
> OK, you set up a static IP in System > Administration > Network.  Did you set your gateway correctly, and did you click on the DNS tab and set up your DNS IP addresses as given you by your ISP?

Try this:

Open a terminal and type:
ping 72.14.207.99

If you get a response, then your internet connection is working on a TCP/IP level.  If not, the whole thing is not working for some reason.

If you do get a response, then type:
ping [www.google.com](www.google.com)

If this doesn't work, then the problem is assuredly DNS related.

ping 72.14.207.99 -- "Network unreachable" (or something similar)

Al

---

### Post by HereInOz on 2007-03-18
MrC you are right about the IP address.  Seems almost as if there is a hardware problem somewhere.  Card not installed, or not cannected or something like that.

If he can't create a connection by allocating a fixed IP, and the router will not assign one, then rather than not being able to connect with Firefox, he has no active network interface at all for some reason.

Is there a hardware problem with the card, cable, or similar?

---

### Post by Mr. C. on 2007-03-18
alfonsos,

Your NIC has been identified and loaded by the system:

Linux Tulip driver version 1.1.13 (December 15, 2004)
tulip0:  MII transceiver #0 config 3100 status 7829 advertising 01e1.
eth0: Davicom DM9102/DM9102A rev 64 at 0001d000, 00:08:A1:18:C9:78, IRQ 169.

Now we'll figure out why it has no IP assigned.

Since you've found a nice dual-boot method to transfer the files, please become root:

```
sudo -s
```
and then run these commands when you get a chance (you can just copy/paste them of them into a Terminal window):
```

cat /etc/network/interfaces >> /tmp/diags.out
cat /etc/resolv.conf >> /tmp/diags.out
lshw -class network >> /tmp/diags.out
lspci >> /tmp/diags.out
lspci -n >> /tmp/diags.out
gzip /tmp/diags.out
chmod a+r /tmp/diags.out.gz
exit

```

and transfer/upload /tmp/diags.out.gz as you did previously.

MrC

---

### Post by alfonsos on 2007-03-19
> **Mr. C. said:**
> alfonsos,

Your NIC has been identified and loaded by the system:

Linux Tulip driver version 1.1.13 (December 15, 2004)
tulip0:  MII transceiver #0 config 3100 status 7829 advertising 01e1.
eth0: Davicom DM9102/DM9102A rev 64 at 0001d000, 00:08:A1:18:C9:78, IRQ 169.

Now we'll figure out why it has no IP assigned.

Since you've found a nice dual-boot method to transfer the files, please become root:

```
sudo -s
```
and then run these commands when you get a chance (you can just copy/paste them of them into a Terminal window):
```

cat /etc/network/interfaces >> /tmp/diags.out
cat /etc/resolv.conf >> /tmp/diags.out
lshw -class network >> /tmp/diags.out
lspci >> /tmp/diags.out
lspci -n >> /tmp/diags.out
gzip /tmp/diags.out
chmod a+r /tmp/diags.out.gz
exit

```

and transfer/upload /tmp/diags.out.gz as you did previously.

MrC

Here it is (this's getting exciting!)

Al

---

### Post by alfonsos on 2007-03-19
> **Mr. C. said:**
> Alfonsos,

Your NIC did not get configured with an IP address.

MrC

MrC- a question: What about the ifconfig output..

(eth0 Link encap: Ethernet HWaddr 00:08:A1:18:C9:78
inet 6 addr: fe80::208:a1ff:fe18:c978/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
Rx packets:1 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen: 1000
Rx bytes:258 (258.0 b) Tx bytes:1836 (1.7 KiB)
Interrupt:169 Base address: 0xd000)

..told you that my NIC did not get configured with an IP address?

(I hope it's clear that I'm not 2nd-guessing you - I want to know because that insight appears to be critical to solving the problem and I see an opportunity to learn something substantial and useful)

Al

---

### Post by Mr. C. on 2007-03-19
> **alfonsos said:**
> MrC- a question: What about the ifconfig output..

(eth0 Link encap: Ethernet HWaddr 00:08:A1:18:C9:78
inet 6 addr: fe80::208:a1ff:fe18:c978/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
Rx packets:1 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen: 1000
Rx bytes:258 (258.0 b) Tx bytes:1836 (1.7 KiB)
Interrupt:169 Base address: 0xd000)

..told you that my NIC did not get configured with an IP address?

(I hope it's clear that I'm not 2nd-guessing you - I want to know because that insight appears to be critical to solving the problem and I see an opportunity to learn something substantial and useful)

Al

Yup, perfectly clear - thanks for the sensitivity.

There is no line such as:

          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0

This is the key line; without an IP/broadcast/mask, no networking will occur.

MrC

---

### Post by Mr. C. on 2007-03-19
Ok, the driver is recognized, loaded, and eth0 assigned.

From a terminal window, run :

```
sudo ifdown -a
sudo ifup -a
grep DHCP /var/log/syslog
ifconfig -a

```

Show the output if there is any.

MrC

---

### Post by alfonsos on 2007-03-19
> **Mr. C. said:**
> Ok, the driver is recognized, loaded, and eth0 assigned.

From a terminal window, run :

```
sudo ifdown -a
sudo ifup -a
grep DHCP /var/log/syslog
ifconfig -a

```

Show the output if there is any.

MrC

Here it is.

Al

---

### Post by Mr. C. on 2007-03-19
Ok, you are receiving no DHCP offers:

> Mar 19 14:17:42 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Mar 19 14:17:47 localhost dhclient: No DHCPOFFERS received
This either implies that no DHCP server is available, the cable is in an ethernet port different than what the system consider's eth0, or there is some bug with the 6.06 version of the driver not present in the live cd.

Have you tried manually setting a static IP ?
What messages do you see in /var/log/syslog when a static IP is used and brought up (ifup eth0 - assuming eth0)?
Have you tried the cable in other ethernet ports ?
Do you see a link light on the NIC port ?
What does **mii-tool  -v eth0** report ?
What exact device is your ethenet cable plugged into ?

MrC

---

### Post by alfonsos on 2007-03-20
> **Mr. C. said:**
> Ok, you are receiving no DHCP offers:


This either implies that no DHCP server is available, the cable is in an ethernet port different than what the system consider's eth0, or there is some bug with the 6.06 version of the driver not present in the live cd.

Have you tried manually setting a static IP ?
What messages do you see in /var/log/syslog when a static IP is used and brought up (ifup eth0 - assuming eth0)?
Have you tried the cable in other ethernet ports ?
Do you see a link light on the NIC port ?
What does **mii-tool  -v eth0** report ?
What exact device is your ethenet cable plugged into ?

MrC

The ethernet cable (from the NIC port) is plugged into a Linksys router.

I tried the static IP again (I'd tried it before) - no go. 

I tried moving the cable (to the NIC port) to another ethernet port on the router - same behavior.

I tried removing the router with the modem plugged directly into the NIC port - same behavior: works in Windows, doesn't work in Ubuntu. 

I'll supply the above-requested terminal outputs later (little pressed for time), but later this AM  I'm going to stop at a computer store and pick up another NIC card - cheap experiment; seems reasonable to rule out that one piece of critical hardware.

Al

---

### Post by alfonsos on 2007-03-20
MrC, I'm sending you this message from Ubuntu! Earlier I went to my favorite korean computer service/sales store and, after telling the owner my problem, he explained that Linux will work reliabaly with only 3 NIC chipsets: 3com, Intel & RealTek. He gave me 2 used ones, a RealTek and a 3Com (he didn't have an Intel in his pile of NICs) - $5. I have the RealTek in the machine right now, the 1st one I tried. My original NIC - the one that apparently caused all the trouble with Linux - had a Davicom chipset

So, I guess my problem is solved and I can stop pestering you. Out of curiosity, I'm going to try the live CD and see if it works with the RealTek NIC.

I much appreciate the attention you've given my problem, I've learned a lot.

Thanks!

Al

---

### Post by Mr. C. on 2007-03-20
I'm glad you are up and running.

Like most sales people, yours does not know what he's talking about and is simply wrong.  But you do now have a new solution, and that's all that matters.

Best of luck,
MrC

---

### Post by redeemer on 2007-03-20
Well done :)

Guys, I have a similar problem here: [http://ubuntuforums.org/showthread.php?t=389260](http://ubuntuforums.org/showthread.php?t=389260)

Can anyone help?

Thanks,
Tom

---

