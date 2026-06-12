---
title: "LAN Share drops every 24 hours?"
date: 2014-06-22
forum: Networking &amp; Wireless
---

### Post by ewangr on 2014-06-22
Upstairs machine is U14.04 64-bit with a Powerline Ethernet adapter set to connect to my home network through my Nighthawk router and wireless access. So U correctly sees it as a wired connection and I have wireless turned off. Have set a fixed v4 IP address and have Samba setup to share an attached USB3 drive.

Downstairs machine is Win 8.1 64-bit with a wireless adapter set to connect to the Nighthawk router, uses the same home network name, and shares an attached USB3 drive. Has a fixed v4 IP address (not the same as the upstairs of course).

Both machines addresses are set +50 past the range the router is supposed to use for DHCP.

In general use I can be on either machine and see the drive attached to the other (took a fair bit of setup, but is now generally reliable). However about every 24 hours or so, the U14.04 machine stops seeing the Win machine. If I go to my laptop, I can still see the win machine, but not the U machine's drive. So it appears that the U machine is not answering the calls for some reason. Internet access from all machines continues to work, so it's not falling off the network (or if it is it is quickly reestablishing).

Rebooting the U machine restores everything, and then everything can see everything again.

I'd ideally prefer not to have to reboot daily. Thoughts on what may be happening and how to troubleshoot/fix?

---

### Post by tgalati4 on 2014-06-22
It's possible that the powerline ethernet adapter is resetting itself due to powerline conditions once per day.  Get a 100' ethernet cable and bypass the powerline adapter and run it that way for a few days to isolate the issue.  Unlike wikipedia, powerline adapters work better on paper than in real life.

---

### Post by ewangr on 2014-06-22
> **tgalati4 said:**
> It's possible that the powerline ethernet adapter is resetting itself due to powerline conditions once per day.

Willing to consider that as a possibility, but then why would it still work with everything but the LAN share? Would simply forcing a remount work in that case? I have the drive in my /etc/fstab...

---

### Post by tgalati4 on 2014-06-23
You could write a cronjob that performs a *mount -a *at some time in early hours (say 3 am) and that should fix it.  Typically when the network goes down, the shared mounts get lost.  There may be an fstab switch to automatically remount, but you will have to research it.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by ewangr on 2014-06-25
> **tgalati4 said:**
> You could write a cronjob that performs a *mount -a *at some time in early hours (say 3 am) and that should fix it. 

So a couple days went by with no problem, and then this afternoon the Windows drive disappeared. Tried the mount -a (sudo of course), and no luck. Tried a few other things, and no luck. Rebooted, and everything was hunky dory.

Consider me stumped...

---

### Post by tgalati4 on 2014-06-26
It could be a problem on the Windows end.  It's possible that the USB3-connected drive is going to sleep which causes the share to disappear with no way to wake it up--other than a reboot.  Also using a wireless connection for a shared drive leaves your network vulnerable to interference.

---

### Post by ewangr on 2014-06-26
> **tgalati4 said:**
> It could be a problem on the Windows end.  It's possible that the USB3-connected drive is going to sleep which causes the share to disappear with no way to wake it up--other than a reboot.  

But it's the Ubuntu machine, not the Windows machine, that I'm having to reboot so how would that be waking up the drive connected to the Windows machine?

---

### Post by tgalati4 on 2014-06-26
There is something called a WINS server that enumerates Windows shares on a Windows network.  Rebooting could cause the WINS server to enumerate the shares.  Check your SAMBA configuration files to make sure that WINS is supported and activated.  [http://www.samba.org/samba/docs/using_samba/ch06.html](http://www.samba.org/samba/docs/using_samba/ch06.html)

Open a terminal and use:

```
smbstatus
``` and keep and eye on your share connection.

---

### Post by ewangr on 2014-06-28
So watched the status, and the only thing I could see was that once the U machine stopped talking to the W machine the status still showed the external drive attached to the U machine which was being shared to the Windows network, but stopped showing the Windows drive.

Figured you might be on to something with samba, so I did a restart of smbd and nmbd and then did a mount -a. I then clicked on the launchbar shortcut for the Windows machine drive, and Ubuntu locked up. CPU monitor froze. Clock froze. Nothing responded to clicking anywhere. Finally had to unplug the machine. It seems like even if there is something wrong at the Windows end that Ubuntu's response is less than optimal...

---

### Post by tgalati4 on 2014-06-28
Check the log files in /var/log/syslog.  You may have a hardware issue--bad network card, bad power supply, or something else.  I would still bypass the powerline adapter with a real ethernet cord to rule out the network connection.

---

