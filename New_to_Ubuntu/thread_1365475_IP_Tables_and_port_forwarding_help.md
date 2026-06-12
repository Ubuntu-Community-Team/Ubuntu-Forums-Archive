---
title: "IP Tables and port forwarding help"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Baffled Lemming on 2009-12-27
Hi All--

I'm a Windows refugee getting up-to-speed in Ubuntu/Linux.  Have a few security questions to which I am sure you experts will have the answer. 

1.  I was initially using firestarter as an interface to IPtables.  Was somehow successfully hacked with a couple interesting features.  In the exceptions section, telnet port was excepted from event logging as was port 44444.  Now I know this is subseven which is only supposed to work on Windows, but it looks like they took a chunk out of me. 

2.  So, dumping firestarter and wading through the daunting task of learning iptables.  There are plenty of rules and tables in there though, some of which are probably giving comfort to the hacker causing me grief.  I'd like to save the current settings for forensice purposes, clear the decks, and then startout with some ideal settings.

So my three questions are:

1.  While I am but a grasshopper, and not a Zen master, what are the ideal settings I can pump in to acheive the following while I'm learning:
A.  Send and receive secure email via Evolution.
B.  Access a restricted list of websites, such as this one for learning purposes, and to get updates, etc.
C.  Use a relatively insecure P2P program for communications: Skype.

2.  How can I reassign ports?  Obviously I reassign ports 21 and 22. 

3.  Where are the firestarter logs, so I can see how that bad boy got in there? 

Thanks in advance!

---

### Post by JKyleOKC on 2009-12-27
In the Terminal, type "man ufw" and study the examples there. The "ufw" program is "uncomplicated fire wall" and it's a much simpler interface to iptables, that starts out with everything disabled. You then enable only the items you want.

To save the existing rule set, use "sudo iptables-save >~/oldiptables" which will write the rule set to a file named oldiptables in your home directory. It's a good idea to do this (only to a different unique filename) before each change you make to the firewall. You can then roll back to the previous rules via "sudo iptables-restore <~/savedfile" if the change isn't to your liking.

These two (save and restore) utilities make it very easy to edit your rules by hand once you feel comfortable doing so. Just save the rules to a file, edit that file via "gksudo gedit thefilename" and save it, then restore the edited file. You'll need to use gksudo or the KDE equivalent for the editing (and possibly a different editor; I use mousepad), because the save and restore operations make the file owned by root. You can read it, but not write to it, as your normal user.

Another way to work with iptables is to install the "webmin" package from the repositories. That's what I used to set up my starting point when I switched from an ancient Mandrake 8.1 distribution to Xubuntu 8.04; I then edited its rule package, stored in /etc, to tweak the rules to match what I had used previously (however my setup involves running a private FTP server, which you probably won't need). You access "webmin" through your web browser (in my case Firefox) and it handles all sorts of configuration issues for you, not just iptables.

---

### Post by Baffled Lemming on 2009-12-27
Hi Jim:

Thanks very much--excellent information.  One further question.

I was trying to manipulate iptables, both directly and through Gufw, when it became clear that ports 5900 through 5910 are open and there is some kind of VNC server running.  

I also found I can't delete this allow in iptables or GUFW.  

Are these ports necessary and iptables is somehow stopping me from shooting myself?  Or are they malicious and hard wired somewhere in the computer innards, and if so, how do I go change it?  Also if it is malicious is there a way to see what the recipient IP address is so I can track it?  You'll note that I blocked port 5900 and thought better of blocking the rest of them. 

 ufw status
Status: active

To                         Action  From
--                         ------  ----
5900:5910/tcp              LIMIT   Anywhere
110                        ALLOW   Anywhere
25/tcp                     ALLOW   Anywhere
22                         ALLOW   Anywhere
5900/tcp                   DENY    Anywhere


Thanks!

Lem

---

### Post by bodhi.zazen on 2009-12-27
IMO you should not mix and match, either stay with ufw or iptables, but not both.

ufw configures iptables so it will conflict or remove any rules you write manually, unless of course you add them to the before or after rules.

See:

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by JKyleOKC on 2009-12-27
> **Baffled Lemming said:**
> Are these ports necessary and iptables is somehow stopping me from shooting myself?  Or are they malicious and hard wired somewhere in the computer innards, and if so, how do I go change it?  Also if it is malicious is there a way to see what the recipient IP address is so I can track it?  You'll note that I blocked port 5900 and thought better of blocking the rest of them. 

 ufw status
Status: active

To                         Action  From
--                         ------  ----
5900:5910/tcp              LIMIT   Anywhere
110                        ALLOW   Anywhere
25/tcp                     ALLOW   Anywhere
22                         ALLOW   Anywhere
5900/tcp                   DENY    Anywhere
It appears that you've got a VNC server, sometimes referred to as "remote desktop," running. It would be listening on that 5900-5910 port range. However it's not hard-wired in as part of your system, so it would be safe to block the whole range.

I agree fully with bodi.zazen that you should not "mix and match" firewall management tools, even though they all wind up at the same place. That place is a part of the kernel called "netfilter" and the iptables rules tell netfilter what to do and when to do it. When you do mix and match, the tool that runs last during the boot process is quite likely to modify what earlier actions have done to the rules, with the result that you don't get what you expected.

I did experiment with ufw and found it quite easy to use, but disabled it before switching over to webmin for my initial configuration of iptables. Then once I was ready to begin tweaking, I stopped using any of the other tools and now rely entirely on manual editing -- but the rule set that I edit is the one that was created by webmin in the /etc directory, since webmin added a boot-time option to restore from that file.

To see what is listening on ports 5900-5910, check what services you are running at startup. Viewing the "dmesg" file in /var/log may help; it's a report of boot time actions but does not go all the way to the final login steps. In Xubuntu, there's a "services" item in the "system" portion of the applications menu that shows all (or at least most) running services; I'm sure that Ubuntu has something similar but someone else will have to tell you how to access it.

You can also, from the terminal, use "sudo netstat -p" to get a list of all active ports and sockets, or use "sudo netstat -p | grep 5900" to trim the list down to just those lines that contain "5900" anywhere in the line. You can "man netstat" to find more than you want to know about this useful diagnostic tool...

---

### Post by Baffled Lemming on 2009-12-27
Thanks to both of you for your responses.  I will try everything you mention Jim and and report back to you with an update.

Lem

---

### Post by Baffled Lemming on 2009-12-27
Still working on the parry and defense, but getting there.  

Here are the contents of the dmesg file.   Let me know if there is anything that looks not right there.  


tango@Alpha:/var/log$ tail dmesg
[   37.984296] type=1505 audit(1261895686.286:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1831
[   38.135832] type=1505 audit(1261895686.434:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1835
[   38.567926] ip_tables: (C) 2000-2006 Netfilter Core Team
[   38.708475] nf_conntrack version 0.5.0 (4095 buckets, 16380 max)
[   38.709324] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   38.709338] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   38.709349] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   38.941284] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   56.701498] eth0:  setting half-duplex.
[   56.701732] ADDRCONF(NETDEV_UP): eth0: link is not ready

Thanks again for the helpful advice.

Lem

---

