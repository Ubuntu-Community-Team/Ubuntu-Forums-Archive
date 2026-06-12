---
title: "hosts file"
date: 2004-11-05
forum: Networking &amp; Wireless
---

### Post by TRex on 2004-11-05
I can get to the /etc/hosts file, but cannot figure how to edit it. I'm a newbie at Linux, so please don't assume I know anything about it. I know networking in the Windows environment and use a special hosts file on my Windoze PCs that blocks most advertising. I'd like to do the same with this box. TIA.

---

### Post by FLeiXiuS on 2004-11-05
Here is a quick how to, to edit your /etc/hosts file.
The $ represents a line of code you may enter in a terminal.

Open /etc/hosts with your favorite text editor.  Remember to use sudo.

```

**Format:**
<IP> <HOSTNAME>.<DOMAIN> <ALIAS>

**Example:**
127.0.0.1 localhost.localdomain localhost

```

_IP_
Replace the <IP> with the IP of your system. If your running DHCP do not worry about editing this file.  To detect your IP address run ```
$ lsconfig
``` Then browse for the connected interface (eth0, wlan0, etc)

_Hostname_
Replace the <HOSTNAME> to your systems hostname.
```

**To view current hostname:**
$ hostname

**To change hostname:**
$ sudo hostname 'enterhostname'
(without quotes)

```

_Domain Name_
The domain name can be anything you like unless it must be resolv, which then you must use /etc/resolv.conf.  But thats another issue i'll cover later! :o 

_Alias_
Alias are simply another way to combine a set of arguments.  When you create a hosts file, its simply creating a list of hosts on the network, or locally.  Its much easier to understand if you kept the alias the same as the hostname.  It saves a lot of trouble with debugging and troubleshooting.  But you are free to use whatever you like.


That should help you out.

---

### Post by TRex on 2004-11-05
Mucho thanks, FLeiXiuS.

I opened a root terminal session (which required my password), entered 'gedit' which opened the editor, opened the hosts file and it opened with permissions. :-) Then it was a simple matter of copying from a hosts file from my PCs to the etc/hosts file -- too many to type, I have nearly 700 entries!

Thanks again. Your directions made it easy.

---

### Post by rtimai on 2007-07-13
I also want to use the MVP Hosts file in Ubuntu 7.04 Feisty to block malicious and nuisance IPs. 

See [http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)

I opened Root Terminal, entered gedit, which prompted me for my password, but as GEdit opened, the following message appeared in the Root Terminal console.

(gedit:10570): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I was able to open the ect/hosts file and add the MVP entries, but found that it was read-only. What am I doing wrong?

---

### Post by rtimai on 2007-07-13
I just noticed that TRex who says he's a newbie joined this forum Nov 2004. How much do you have to know to not be a newbie anymore?

I installed Feisty Fawn for the first time last week after deciding to delete my Windows XP partition and run solely on Linux. The hosts file is probably not a really big deal, considering hardly any malware runs on Linux. Now that I think about it, ff someone would direct me to a Linux-for-Windows-Users resource, that might be a more useful request. You are welcome to email me.

Roger

---

### Post by Mr. C. on 2007-07-13
As an advisory note, creating a large hosts file will slow down hostname -> IP lookups.  The hosts file is a flat file and an exhaustive search must be performed before subsequent DNS lookups will occur for for all entries not in the hosts file.  This is a very clumsy way to perform blacklisting.  There are better approaches.

MrC

---

### Post by rtimai on 2007-07-14
Mr. C:

Thanks for your response. I remember that a large hosts file affected performance in Windows XP too, and there was a setting used to workaround it, changing the startup mode of one of the system services from Auto to Manual, don't remember exactly which, but it had "DNS" in the service name.

I'll take your suggestion and reconsider modifying the hosts file only if I come across more information. That not many Linux users seem concerned with a local hosts file suggests that other tools such as the NoScript and AdBlock Plus extensions for Firefox might be adequate? I just installed both those add-ins. 

The reason I asked in the first place about this is that at [www.linux.com](www.linux.com) (not the -.org site,) an annoying banner displays over the title of the main aritlcle on the page, and there is no way to move it or cover it. I had to hit Ctrl-+ repeatedly to enlarge the font size until the Printer-friendly text link became visible, then I could view the article unobstructed in the printer-friendly page. 

Later on I installed AdBlock Plus, and that killed the obstructing banner. Firefox's built-in pop-up blocker, btw, didn't stop that banner from appearing.

---

### Post by Mr. C. on 2007-07-14
AdBlock is the right tool for the job.

MrC

---

### Post by putz3000 on 2008-03-23
remember that if you are editing a file and find out it is read only that probably means you did not type sudo in front of the command launching your editor (example: sudo gedit hosts).  At least as a newbie, that is what I find is usually causing me the "read only problem".

---

