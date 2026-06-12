---
title: "Cconnection to router fails after working for some days"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by Alp82 on 2007-09-18
I am running kubuntu for about a week with no problems refering to my network connection. I have an nvidia onboard network card. ifconfig says that eth0 is ok (as far as i can see).

If i click on the symbol of the KDE Network Manager it says that i've a valid connection, but ping 192.168.0.1 (my router) doesnt respond. In Windows (i'm running a dual-boot system) internet runs like a charm. I'm not sure what i did. I guess it could be winecfg... because this was the last command i typed in the terminal. It crashes everytime i try wine (no idea where the problem *here* is), but this time i got some different errors, maybe relating to some network issues, dont remember clearly.

I hope you can help me... i am beginning to learn linux systems, so i'm not very experienced.

---

### Post by noob12 on 2007-09-18
Can you post the output of **lspci -nn** and **sudo lshw -C network** so we can see the hardware and driver you are using?

---

### Post by Alp82 on 2007-09-18
Here is the output
[http://pastie.caboo.se/98350](http://pastie.caboo.se/98350)

---

### Post by Alp82 on 2007-09-18
I'm still struggling. Any help?

---

### Post by noob12 on 2007-09-19
00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev a3)

Here's your ethernet controller, but I don't understand why it isn't showing up at all in the **lshw -C network**.  Only your TV card is.   Did you or that pastie site chop off the output by mistake?

---

### Post by Alp82 on 2007-09-19
No, it really didn't show up. I was wondering too. Here ist some more output.

**dmesg**:
[http://pastie.caboo.se/98616](http://pastie.caboo.se/98616)

I think this could help. But i still don't have an idea.

---

### Post by noob12 on 2007-09-19
You know that you can paste text right here, right?  Just enclose using the code block marks (use the # sign tool in the web-posting editor).

The boot you just posted used this command line
```

Kernel command line: root=UUID=ebfa57b3-1035-4c21-8d96-4dbbb073aa29 ro quiet splash

```

Here is your ethernet driver starting:

```

[ 33.597577] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
...
[ 38.036026] forcedeth: using HIGHDMA
...
[ 38.557973] eth0: forcedeth.c: subsystem: 01043:8141 bound to 0000:00:0a.0

```

Then you have a firewall come up and the ports suggest it is blocking your DHCP interaction...
```

[ 63.168717] DROPPED IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:11:6b:25:79:94:08:00 SRC=192.168.0.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=21528 PROTO=UDP SPT=67 DPT=68 LEN=308

```
as well as a lot of SMB/NMB filesharing activity.

Your firewall rules are way too broad.  If you turn off your firewall, things should improve immensely.  You are probably using either firestarter or your own iptables script.

---

### Post by Alp82 on 2007-09-19
That was it! It was "guarddog", and i deactivated it. Everything works now. Thanks for your help.

---

### Post by natureday on 2007-09-19
I had this same problem. The rats outside chewed the cabel so much that it stopped working. I thought it was my ehternet, but it was the lame rats.
Anna:)

---

