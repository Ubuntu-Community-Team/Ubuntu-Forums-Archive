---
title: "Internet conneciton problems"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by okok on 2006-11-18
I recently had to change my ADSL modem. When I started using the new one without making any change to any of the machines connected to it, everything worked fine in Windows, but I could not get almost anything from the internet. Disabling IPv6 in Ubuntu solved most of the problems.

However, I am still unable to use use Gaim to connect to googletalk and to MSN, and I can't download Ubuntu suftware updates. The update application just fails to connect to (at least) one of the servers, although when I type the server's address in my browser, for instance, I CAN see its browse contents and access all files.

What may be wrong and how do I solve this?

Again, with a windows machine connected to the same modem I don't experience any problem.

---

### Post by mips on 2006-11-18
a bit more info.

What does your /etc/resolv.conf look like

---

### Post by okok on 2006-11-19
Here is the full contents of my /etc/resolv.conf :

search lan
nameserver 10.0.0.138

---

### Post by mips on 2006-11-19
Try adding your ISPs primary&secondary dns server ip's to the top of the nameserver list.

---

### Post by okok on 2006-11-19
Thanks.

But is there a way for me to know what these are except for calling customer support, which might not be willing to help because they don't support linux and because in windows there is no such problem?

And why would a change of ADSL modem make settings that had worked perfectly stop working?

---

### Post by okok on 2006-11-19
Ok, I was able to obtain these numbers and the problem was solved. Only after I restarted the machine, the new lines were lost, and the file reverted to its previous condition. What causes this and how can I prevent it from happening?

---

### Post by mips on 2006-11-19
> **okok said:**
> Ok, I was able to obtain these numbers and the problem was solved. Only after I restarted the machine, the new lines were lost, and the file reverted to its previous condition. What causes this and how can I prevent it from happening?

Don't worry there is a solution to this issue as well. I can't search for you know but will tomorrow.

If you want do an Advanced search, enter my userid in the userid field and search for keywords DNS. also do a similair search but this time for a user by the name of **handy**, you should find a solution in there somewhere where people complain their dns settings are being overwritten.

---

### Post by dbott67 on 2006-11-19
The answer may be in [this thread (post #7)]("http://www.ubuntuforums.org/showthread.php?t=291022").  It seems to be the same issue --- browser works, but no Synaptic, Gaim, etc.

-Dave

---

### Post by stream303 on 2006-11-21
> **okok said:**
> Ok, I was able to obtain these numbers and the problem was solved. Only after I restarted the machine, the new lines were lost, and the file reverted to its previous condition. What causes this and how can I prevent it from happening?

No sweat.  Now that you know your isp's dns addresses, we can keep this from happening by editing the PREPEND line in /etc/dhcp3/dhclient.conf as root.  This will force your choice of addresses to always be in your resolv.conf file.  What's happening is that dhclient-script overwrites /etc/resolv.conf (on purpose) and temporary edits don't last too long. :)

Here's the thread, although I don't use the OpenDNS option - just my original isp nameservers.  Looks scary but it's only a one-line change and a reboot.

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

---

### Post by okok on 2006-11-21
Thank you all very much for your help.

Specifying the nameservers in /etc/dhcp3/dhclient.conf
 solved the problem, plus I learned about opendns, which seems to be performing better than my ISP's DNS.

---

### Post by stream303 on 2006-11-21
Cool!  Thanks for letting us know how it went.

---

