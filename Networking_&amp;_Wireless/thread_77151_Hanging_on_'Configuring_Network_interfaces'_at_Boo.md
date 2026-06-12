---
title: "Hanging on 'Configuring Network interfaces' at Boot"
date: 2005-10-16
forum: Networking &amp; Wireless
---

### Post by Domhnull on 2005-10-16
Last night I finished a fresh install of Breezy.  I set things up and everything seemed to be working great except, like Hoary, it insisted on added my DSL modem's IP address to resolv.conf.  With that IP as the first DNS server there are issues connecting to websites, etc.  Under Hoary I had locked resolv.conf with:
```
sudo chattr +i /etc/resolv.conf
```
I did the same thing last night under Breezy.  This morning, however, on boot the system hangs on configuring network interfaces.  I'm assuming it is trying to change resolv.conf, can't but rather than proceeding is just sitting there doing nothing.  The same thing happens booting into recovery mode.

I'd welcome any help at how to get past this problem.  I'd rather not reinstall if I can avoid it.

---

### Post by Domhnull on 2005-10-16
I realized an easy way around this.  I booted with the LiveCD and unlocked the file.  When I rebooted the hanging problem was gone.  So far the system doesn't seem to have a problem with the modem's IP address being listed.  If that continues I won't worry about it.

---

### Post by dayal_78 on 2005-10-16
[QUOTE=Domhnull]I realized an easy way around this.  I booted with the LiveCD and unlocked the file.  When I rebooted the hanging problem was gone.  So far the system doesn't seem to have a problem with the modem's IP address being listed.  If that continues I won't worry about it.[/QUOTE]
Hi,
I installed Ubuntu 5.10 on my Dell Inspiron 6000 and I am also having the same problem (boot process is hanging for a long time on configuring network interfaces and then continues to boot.). Can you let me know how I can solve this problem??

Thanks
Dayal

---

### Post by Domhnull on 2005-10-16
In my case I booted with the LiveCD, mounted my hard drive, and then unlocked the resolv.conf file with:

```
sudo chattr -i /mnt/hda1/etc/resolv.conf
```

I didn't have the problem until I locked resolv.conf and it wouldn't continue past configuring the network interface at boot until I unlocked it.  It may be that your problem is different, although it could be related.  I'm afraid I don't really have any suggestions.

---

### Post by mlomker on 2005-10-16
> Can you let me know how I can solve this problem??


You could try pressing Ctrl-C to skip past it.

---

### Post by mlomker on 2005-10-16
> So far the system doesn't seem to have a problem with the modem's IP address being listed.  If that continues I won't worry about it.

It sounds like your problem is solved, but if you continue to have problems then install the **resolvconf** package rather than locking your file.  It allows you to add DNS settings to your **/etc/network/interfaces** file that'll over-ride DHCP settings.

---

### Post by dayal_78 on 2005-10-16
hi,
I logged into recovery mode and did:
chattr -i /etc/resolv.conf
and then logged back onto regular mode.
but still ubuntu is hanging on configuring-interfaces
you can take a look at my other thread:
hi,
I logged into recovery mode and did:
chattr -i /etc/resolv.conf
and then logged back onto regular mode.
but still ubuntu is hanging on configuring-interfaces
you can take a look at my other thread:
[http://ubuntuforums.org/showthread.php?t=77242&page=2](http://ubuntuforums.org/showthread.php?t=77242&page=2)
for any pointers towards this problem.

thanks
Dayal

---

### Post by Nipoc333 on 2006-02-05
Try this; it worked wonders for me. Even though it recommends a 20 sec timeout my connection still works perfectly with a 10 timeout. Though I think this works because of disabling eth0 on boot more than any thing. Anyway here's the link

[http://ubuntu.wordpress.com/2006/01/31/configuring-network-interfaces/](http://ubuntu.wordpress.com/2006/01/31/configuring-network-interfaces/)

---

### Post by dustigroove on 2006-02-05
Pressing Ctrl+C when it hangs will allow you to cancel network configuration and proceed.

**Edit - Looks like mlomker beat me to the punch.  **:)

---

