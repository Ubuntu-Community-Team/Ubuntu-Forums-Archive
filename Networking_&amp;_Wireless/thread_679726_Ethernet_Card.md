---
title: "Ethernet Card"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by Simpleton on 2008-01-27
What ethernet card should I use for compatibility with Gutsy? I've got a Realtek 8169, which is causing me havoc due to additional ATI issues. I want a card that will just plug in and work.

Suggestions?

---

### Post by margori on 2008-01-27
Hre you have some info:
- [www.ubuntuhcl.org]("http://www.ubuntuhcl.org/pub/manufacturers.php?category_id=14")
- [Support Wired Network Cards]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards")

---

### Post by Simpleton on 2008-02-02
This is really annoying... I bought a D-Link 530TX Plus, becaus the second link said it worked straight out of the box... however... it didn't make any difference.

I booted into recovery mode, tried to install fglrx, and the fetching failed due to the network card. Help!

---

### Post by Whiffle on 2008-02-02
I have a realtek 8169 that works flawlessly

What issues are you having?

---

### Post by netztier on 2008-02-02
> **Simpleton said:**
> Suggestions?

In my experience, [Intel's PRO/1000 GT (PCI) and PRO/1000 PT (PCI-E) Desktop Adapters]("http://www.intel.com/network/connectivity/products/desktop_adapters.htm") are fast and hassle-free, supported by the e1000 module that comes with the normal version of Ubuntu's Linux kernel. They even work on non-x86 hardware such as SPARC - the Sun Ultra 60 used as local mirror server at [SwissTeam]("https://wiki.ubuntu.com/SwissTeam/")'s Gutsy Gibbon release party liked the NIC and happily served packages to the party LAN.

The PCI version was around CHF 45.- (which is about USD 40.- at present) for me - not really cheap, but worth the money, IMHO.

regards

Marc

---

### Post by Didad on 2008-02-02
This is what I have and I cannot connect.

william@delta:~$ sudo lspci | grep -i ethernet
[sudo] password for william:
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
william@delta:~$ ping 192.168.1.1
connect: Network is unreachable

---

### Post by Didad on 2008-02-04
Nobody seems interested in solving this so I think I'll go back to XP - pity!

---

### Post by netztier on 2008-02-04
> **Didad said:**
> Nobody seems interested in solving this so I think I'll go back to XP - pity!

First:

[SIZE="2"]**<IRONY>**[/SIZE]
[INDENT]Yeah. Do so.

The forum is reeking with  Realtek related posts - until you'll find the search function in ubuntuforums.org (now imagine that! It even has one!) or figure out how to use Google with "Site:ubuntuforums.org" as prefix to the search terms you'd like to find, I fear you're far better off with using XP.[/INDENT]
[SIZE="2"]**</IRONY>**[/SIZE]

Second:

[SIZE="2"]**<SARCASM/PERSONAL RANT>**[/SIZE]
[INDENT]Ditch anything on which it says "Realtek". A lot of these cards may work, and many of them actually do. But a lot of them don't, or if they do, the underperform greatly. Running Realteks is just asking for trouble. In my personal opinion.[/INDENT]
[SIZE="2"]**</SARCASM/PERSONAL RANT>**[/SIZE]


Third:
[INDENT]If you want to report a problem, don't attach your post to some seemingly related thread. Start a new one where you describe your problem as precisely as possible, including outputs (using QUOTE-Tags;  the has sign in the button bar) of **lspci**, **ifconfig -a** and maybe **sudo ethtool eth0** (where eth0 is the name of your NIC) along with **sudo mii-diag -v**. 

You need to give *input* to get some *output*. Forums are not answer-my-question-machines; every network problem has some unique twist to it, and people posting here don't have any magic crystal ball to glance into and get answers just like that.[/INDENT]


regards

Marc, in a monday morning mood.

---

