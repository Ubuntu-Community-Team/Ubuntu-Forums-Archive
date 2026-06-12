---
title: "Firestarter service is NOT started when booting! I'm exposed!"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by Biffy on 2007-03-27
I just installed Ubuntu on this old machine. It's a p2 400mhz with 132 mb of RAM. The system is starting way too fast to be true. Normally you see all kinds of services starting when booting. But here's none. First it says "starting up" and then it prompts something about fschk, then it's done and GDM starts. Something wrong here..

Ok, so i installed firestarter. I see in /etc/init.d/ that the script/service is there. Its green, so it should start at startup but it does not. When the system is up and running, i type /etc/init.d/firestarter status and it says that firestarter is stopped. Then i try the "Shields up!" test and it says that my ports are closed. Not good!

I then start the service, and Shields up says that my ports are stealthed. Summary: My firewall is not started at bootup! Why isnt any services being started when booting? How can i fix this? I did install firestarter from the repos.

---

### Post by Biffy on 2007-03-27
I should add that when i installed Ubuntu, the installation crashed when trying to install packages. Yes, it installed the base packages but nothing more. I did install GDM, gnome, fonts and so on manually from the command line.

---

### Post by wthanna on 2007-03-27
Firestarter is just a graphical interface for IPTables...   If your ports are closed, nothing can get in... you are not "Exposed"

Closed ports = good

---

### Post by r4ik on 2007-03-27
Try,

[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

Good luck !

---

### Post by Biffy on 2007-03-27
> **wthanna said:**
> Firestarter is just a graphical interface for IPTables...   If your ports are closed, nothing can get in... you are not "Exposed"

Closed ports = good

How can i see if iptables are started? Something is wrong, no services are started at startup.

When starting the firestarter service, it says "stealthed" instead of "closed". And thats the way i want it.

r4ik: The service should be started automatically when the system is booting. I did not compile it from source.

And oh, shouldn't there be a fancy Ubuntu logo when booting? There is none, just plain white text.

---

### Post by patrickfromspain on 2007-03-27
Could it have something to do with the machine? Ubuntu may be a bit too much..

---

### Post by r4ik on 2007-03-27
Try,

[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

or,

[http://www.ubuntuforums.org/showthread.php?t=159661&highlight=iptables](http://www.ubuntuforums.org/showthread.php?t=159661&highlight=iptables)

Does not come easy sorry.

Good luck !

---

### Post by Biffy on 2007-03-28
Think i solved it by installing the latest kernel. So services are starting when booting the kernel, but it is not printed on the screen. How can i edit grub so that it prints exactly what it is doing on startup? My dapper machine does that.

---

### Post by Biffy on 2007-03-28
Another question: Why wont the firestarter service start if the network cable is unplugged?

---

### Post by psusi on 2007-03-28
Do you understand what "stealthed" means?  It is a useless violation of the TCP protocol that doesn't do you one bit of good.  Don't worry about it; you aren't vulnerable to anything.  The personal firewall is senseless windows idiocy and isn't needed in Linux.

---

### Post by clickwir on 2007-03-29
> **psusi said:**
> Do you understand what "stealthed" means?  It is a useless violation of the TCP protocol that doesn't do you one bit of good.  Don't worry about it; you aren't vulnerable to anything.  The personal firewall is senseless windows idiocy and isn't needed in Linux.

I'm going to have to agree.

Closed or stealth, you are still "protected". The only status of a port that you need to take note of is "OPEN".

---

### Post by Biffy on 2007-03-30
> **psusi said:**
> Do you understand what "stealthed" means?  It is a useless violation of the TCP protocol that doesn't do you one bit of good.  Don't worry about it; you aren't vulnerable to anything.  The personal firewall is senseless windows idiocy and isn't needed in Linux.

Ok. So, why do i need a firewall in Windows and not in Linux? Is it more of a risk to have closed ports in Windows? Cause i've had some bad experiences when i did a fresh Windows install and plugged the TP cable in without a firewall. No ports where open, still it took 5 seconds to get a known virus inside.

---

### Post by Floppyjoe on 2007-03-30
I agree with Biffy here. If you are not running any Web servers or service like that on your computer you would like the computer to show up as stealthed when it is scanned by port scanners. This effectively hides your computers or routers presence from unwanted attention by others. If it only shows as closed or other then if someone malicious sees that he knows there is something there and might try to comprimise the system. 

Windows XP comes with the computer wide open to attack when you install it. You have to know how to secure it otherwise you could get victimized. 

Linux on the other hand does not get installed wide open like that and is much more secure that way.

---

### Post by nick1 on 2007-05-04
Greetings,

I believe Firestarter is not enabling my firewall rules on system bootup.

First, some information:

I am using Ubuntu Feisty Fawn 7.04 desktop edition
I have Firestarter version 1.0.3 installed
I have a fairly strict policy setup:
inbound traffic policy:  default (meaning all inbound traffic is blocked)
outbound traffic policy:  restrictive by default, whitelist traffic (only allowing HTTP/S and Samba(SMB) out)

The reason I believe Firestarter is not enabling my firewall rules on system bootup is because when I issue the following command...

```
sudo iptables -L
```

...I do not see any of my firewall rules listed.  This command is used to list the entire set of firewall rules.  It's as if Firestarter did not implement my firewall policy.

Only when I manually startup Firestarter (System > Administration > Firestarter) is my firewall enabled.  Reissuing the previous command displays my firewall rules.

Is this a bug? What is the resolution to this problem?

Thanks,

*Nick*

---

