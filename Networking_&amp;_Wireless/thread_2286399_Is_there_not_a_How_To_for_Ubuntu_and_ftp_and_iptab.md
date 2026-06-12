---
title: "Is there not a How To for Ubuntu and ftp and iptables and conntrack_ftp?"
date: 2015-07-11
forum: Networking &amp; Wireless
---

### Post by ZippyDan on 2015-07-11
I've done every possible search for every combination of the following keywords:

Ubuntu
ftp
iptables
ip_conntrack
ip_conntrack_ftp
nf_conntrack_ftp
modprobe

It is one of the most basic tasks to do, setting up an ftp server, and no one on the entire googley internets seems to have posted the, likely incredibly simple, steps to get it working.

I have a very simple firewall setup:

```
-A INPUT -i lo -j ACCEPT
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -m tcp --dport 4559 -j ACCEPT
-A INPUT -j DROP
```

OUTPUT is set to ACCEPT all.

So I'm using a nonstandard ftp port (it is actually the standard HylaFax connection port, which then proceeds to function using passive ftp connections, but that is not important right now).

From everything I have read on numerous places on the internet, since my firewall is already set to accept any RELATED or ESTABLISHED connections, the only thing missing for me to get my PASSIVE ftp ports working is to:

**1. **Load the [FONT=courier new]ip_conntrack_ftp[/FONT] module (or the [FONT=courier new]nf_conntrack_ftp[/FONT] module)
**2. **Tell the module that port 4559 is my ftp control port (and not the standard port 21)
**3. **Find a way to get it to persist through a reboot

**For 1.**

**A. **What is the difference between [FONT=courier new]ip_conntrack_ftp[/FONT] and [FONT=courier new]nf_conntrack_ftp[/FONT]?  Which should I use?
**B. **Where is the correct place to load a module in Ubuntu?  In my searches, I've seen people writing startup scripts I've tried [FONT=courier new]sudo modprobe ip_conntrack_ftp ports=4559[/FONT] and [FONT=courier new]sudo modprobe nf_conntrack_ftp ports=4559[/FONT] and it seems to make no difference.  I noticed that there is an [FONT=courier new]iptables --module[/FONT] listed in [FONT=courier new]--help[/FONT], but I can't get it to take.  I've seen mention of [FONT=courier new]/etc/modprobe.d[/FONT] and [FONT=courier new]/etc/modules[/FONT] (I'm about to try this)

**For 2.**

How do you define the ftp control port for the module?  I've seen examples where people put [FONT=courier new]ports=4559[/FONT] after the [FONT=courier new]ip_conntrack_ftp[/FONT] or [FONT=courier new]nf_conntrack_ftp[/FONT], but this doesn't take with [FONT=courier new]iptables --modules[/FONT] for instance.

**For 3.**

How to make it persist through a reboot?

---

### Post by ZippyDan on 2015-07-11
Well I answered my own questions, but I won't consider this post a waste because now hopefully someone else in my same situation who is either trying to setup an FTP server that supports PASSIVE connections, or someone using a NONSTANDARD FTP port, or someone trying to get HYLAFAX working like me can do a google and find this SUPER SIMPLE SOLUTION

ALL YOU NEED TO DO TO HAVE A SECURE FTP / HYLAFAX SOLUTION IN UBUNTU ARE THE **TWO** FOLLOWING INGREDIENTS:

**1. IPTABLES**
Note: this is not a complete iptables firewall.  I'm only showing the lines that you would need to add to an existing iptables, relevant to getting an FTP server working (see my original post above for an example of a complete firewall if there are no other services that you need).  If you need more help with this part, see Ubuntu's own fantastic How to, including how to get iptables to survive a reboot: [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
```

-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -p tcp -m tcp --dport 4559 -j ACCEPT

```

**2. sudo vi /etc/modules **(the missing puzzle piece!)

Add the following line to the end of the file and save:  
ip_conntrack_ftp ports=4559

And reboot!  THAT'S IT!  

Adding that line to /etc/modules will automatically reactive the ip_conntrack_ftp module every reboot, and fix the problem of opening ports for ftp sessions initiating on port 4559.  Obviously, if you are using a different ftp port, just replace 4559 with whatever port you are using.

I'd still like to know what is the difference between nf_conntrack_ftp and ip_conntrack_ftp, just for curiosity's sake.

---

### Post by QIII on 2015-07-11
You can start with documents like these:

[https://help.ubuntu.com/lts/serverguide/ftp-server.html](https://help.ubuntu.com/lts/serverguide/ftp-server.html)

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

Also, look at my signature for "Find what you need in the Ubuntu Community Wikis"

---

### Post by ZippyDan on 2015-07-11
I already posted the answer above, but thanks for your reply.  Note that none of your links give the incredibly simple answer that I found.

> **QIII said:**
> You can start with documents like these:

[https://help.ubuntu.com/lts/serverguide/ftp-server.html](https://help.ubuntu.com/lts/serverguide/ftp-server.html)

Makes no mention of firewalls, iptables, modprobe, or ip_conntrack_ftp

> **QIII said:**
> [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Makes no mention of modprobe or ip_conntrack_ftp

> **QIII said:**
> [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

This one finally does make mention of modprobe and ip_conntrack_ftp, but not how it relates to an FTP server, and there is no explanation of how to define a custom FTP port, or even if such a setup is possible using this script.  Anyway, my solution seems much simpler and seems to be working great.

---

### Post by bab1 on 2015-07-12
> **Daniel_Castellanos said:**
> 
This one finally does make mention of modprobe and ip_conntrack_ftp, but not how it relates to an FTP server, and there is no explanation of how to define a custom FTP port, or even if such a setup is possible using this script.  Anyway, **my solution seems much simpler and seems to be working great.**

Until you are hacked.  No one uses straight FTP any more.  It's a security risk.  Most folds these days use SSH for file transfer (SFTP),   FTP passes the login info in and data in clear text.  If you install SSH all file transfer and login info is encrypted.

---

### Post by QIII on 2015-07-12
The list was not intended to be exhaustive.  Those were examples to indicate that there certainly are plenty of resources -- you might have to look at several.  If one wants something fully comprehensive, a book store is often the best place to go.

And I'm glad you found a way to get what you needed.

---

### Post by ZippyDan on 2015-07-30
> **bab1 said:**
> Until you are hacked.  No one uses straight FTP any more.  It's a security risk.  Most folds these days use SSH for file transfer (SFTP),   FTP passes the login info in and data in clear text.  If you install SSH all file transfer and login info is encrypted.

Well, in my case I'm using HylaFax server, which is still widely used, and makes use of FTP protocol for communication with clients.

My server happens to not be accessible to the outside world.  It only has a LAN IP and no one can hit those ports from an outside connection.  But if someone wanted to be extra secure they could certainly just add an ```
-s 192.168.1.0/24
``` to their IPtable rule.

[quote=[COLOR=#000000]QIII[/COLOR]][COLOR=#000000]The list was not intended to be exhaustive. Those were examples to indicate that there certainly are plenty of resources -- you might have to look at several. If one wants something fully comprehensive, a book store is often the best place to go.[/quote]

Yes well none of your links provided an answer to the question.  And I googled for hours reading forums across the web looking for an answer.  The closest answer I got (which finally led me to the solution), was from Stack Exchange.  I was simply surprised that such a seemingly simple task is not better documented.[/COLOR]

---

