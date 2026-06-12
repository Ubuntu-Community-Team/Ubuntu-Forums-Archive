---
title: "No internet connection at all, but it says it's connected?"
date: 2017-03-26
forum: Networking &amp; Wireless
---

### Post by zolika1351 on 2017-03-26
I wanted to install Ubuntu in dualboot, and I got everything working except internet. I have a wired connection. Windows works just fine. Also, I even tried copying the same exact settings from windows to ubuntu and it didn't work.
It can't even connect to the gateway, or google, or 8.8.8.8, only localhost.
Dynamic IP doesn't work on the router so I set it to manual and copied the settings from Windows.
Pinging gateway results in this message displayed 3 times:
192.168.1.6 - Destination Host Unreachable
and gets 100% packet loss.
Pinging google results in this message:
Unknown host google.com

---

### Post by TheFu on 2017-03-26
Excellent troubleshooting so far.  I assume you tried to ping the gateway using the IP? Yes?  
And that you **know** the correct subnet/gateway/netmask with 100% certainty?

Please post output from 
**sudo lshw -C network**
there is a way to get similar information from **lspci**, but the command for that is a hassle. [https://www.cyberciti.biz/faq/linux-list-network-cards-command/](https://www.cyberciti.biz/faq/linux-list-network-cards-command/)

Probably have the wrong driver or driver options for the card. This happens about 5-10% for Realtek NICs. Sometimes Windows doesn't correctly leave the card state correctly for some models. We don't know what to suggest without seeing the exact NIC being used.

Not that it helps now, but using Intel NICs in the future is something to seek to avoid issues like this. Plus the intel drivers will offload CPU work to the NIC. Started getting only Intel NICs for my systems whenever possible about 10 yrs ago and all these issues have disappeared. The intel PRO/1000 line is very stable and has great drivers.  If for some reason we can't fix this which is highly, highly, unlikely, the $22 for an Intel NIC is worth it.

---

### Post by zolika1351 on 2017-03-27
Here's the output:
  *-network               
       description: Ethernet interface
       product: Killer E220x Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 10
       serial: 40:8d:5c:b7:59:a8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.1.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:40 memory:fe800000-fe83ffff ioport:d000(size=128)

---

### Post by TheFu on 2017-03-27
I don't have any answer, just some ideas.  Hopefully someone else can chime in with a good answer.
The driver seems to be correct for that NIC. Not an easy fix.

1st, the router IP of 192.168.1.6 is a little odd.  I would expect it to be 192.168.1.1 or 192.168.1.254. ARE YOU POSITIVE it is correct?  Pinging the IP of the card should work too, but really want to ping the router by IP.

2nd, what do the log files say about this device/driver?  Always check the logs on Linux. Always.

[https://bugzilla.kernel.org/show_bug.cgi?id=70761](https://bugzilla.kernel.org/show_bug.cgi?id=70761) is a kernel bug for this. Setting the MTU to 8192 from the default seems to have helped 1 person.

[https://forums.linuxmint.com/viewtopic.php?t=215169](https://forums.linuxmint.com/viewtopic.php?t=215169)  they just disabled IOMMU - which is only used for virtualization HW passthru to my knowledge. If that isn't something you need, can't hurt.

[https://askubuntu.com/questions/333938/how-do-i-get-a-qualcomm-atheros-killer-e2200-gigabit-ethernet-card-working](https://askubuntu.com/questions/333938/how-do-i-get-a-qualcomm-atheros-killer-e2200-gigabit-ethernet-card-working) is from 2013, so the driver should "just work" by now.  Is your switch/router really 100 base-tx?  If so, using ethertool and locking the speed at 100Mbps (instead of using autonegotiate) used to help with that.  If the switch is GigE, check that your cable is at least CAT-5e or better.

Try a different switch port. Sometimes a semi-working port really isn't. 

[https://wiki.linuxfoundation.org/networking/alx](https://wiki.linuxfoundation.org/networking/alx) is the Linux Foundation information about this driver. Nothing exactly useful, but there are some names.

Check the log files with every change. They are usually helpful.

---

### Post by jeremy31 on 2017-03-27
I would set the IP for the computer to be something different like 192.168.1.12
What version of Ubuntu and what kernel? ```
uname -a
```

---

### Post by zolika1351 on 2017-03-28
> **jeremy31 said:**
> I would set the IP for the computer to be something different like 192.168.1.12

That actually made me able to ping my router, but websites still don't work.
EDIT: If I specify 8.8.8.8 in nslookup it works, but I already have that set as my DNS so wut?

> **TheFu said:**
> 2nd, what do the log files say about this device/driver?  Always check the logs on Linux. Always. Where do I access the logs? Sorry, this is the first time I ever had a Linux-based operating system

> **TheFu said:**
> 
[https://bugzilla.kernel.org/show_bug.cgi?id=70761](https://bugzilla.kernel.org/show_bug.cgi?id=70761) is a kernel bug for this. Setting the MTU to 8192 from the default seems to have helped 1 person. Didn't work.

> **TheFu said:**
> 
[https://forums.linuxmint.com/viewtopic.php?t=215169](https://forums.linuxmint.com/viewtopic.php?t=215169)  they just disabled IOMMU - which is only used for virtualization HW passthru to my knowledge. If that isn't something you need, can't hurt. It seems that I can only set it to Soft, otherwise my USB keyboard and mouse stop working completely and just turn off.

> **TheFu said:**
> 
Try a different switch port. Sometimes a semi-working port really isn't. 
That's one of the first things I tried.

---

### Post by chili555 on 2017-03-28
> Dynamic IP doesn't work on the router so I set it to manual and copied the settings from Windows.What DNS nameservers did you use?

---

### Post by zolika1351 on 2017-03-28
> **chili555 said:**
> What DNS nameservers did you use?

8.8.8.8

---

### Post by zolika1351 on 2017-03-28
Using nslookup and /etc/hosts, I can actually access webpages. (I'm posting this from Ubuntu.) So I think this is a DNS problem.

---

### Post by TheFu on 2017-03-28
Some of my questions have never been answered. Very frustrating. Hard to help.

If you are posting this from the Ubuntu machine, then it seems to be solved. 
First you can't ping 8.8.8.8 or the router, but you can now?  If that is the case, none of the kernel or driver questions matter anymore.

**etc/hosts** isn't usually the same file as **/etc/hosts**.  Please be precise to prevent confusion, even if it is only my confusion.

All Unix systems handle logs in 1 of 2 ways. Fortunately, the "new way" (systemd) of looking at them doesn't prevent the "old way" from working. [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles) explains.

My basic method is to search all the recent logs for warnings and errors to get close to the issues. **egrep -i 'warn|error' /var/log/*log** will do that. That provides a list of log files showing lines with potential problems that I can view inside the full files and decide whether the issue occurring is related or not.

If you can ping 8.8.8.8 and that is really the DNS being used by the system, please post the /etc/resolv.conf file back here. Here's mine:```
$ more /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 172.22.22.1
nameserver 66.151.188.45
nameserver 209.69.32.138
```/etc/resolvconf/resolv.conf.d is where I control it (no GUI here).  If you are using a GUI, be certain to keep using it.  The GUI managing the DNS should still end up in that file after a few minutes.

---

### Post by zolika1351 on 2017-03-28
Log file:
[https://paste.ubuntu.com/24268703/](https://paste.ubuntu.com/24268703/)
I can't seem to be able to open resolv.conf, is it hidden or something? I even tried sudo gedit resolv.conf and it just gave me a blank text file.  
Also, I don't really get how the same DNS doesn't work when set as a DNS in Network Manager but works in nslookup (The way I made it access the internet was using for example "nslookup google.com 8.8.8.8" then pasting the ip address into the hosts file.)
EDIT: Can I bump this? I can't reach Steam's download servers because I can't find the URL it's trying to connect to to put in my hosts file.

---

### Post by TheFu on 2017-03-28
a) no, /etc/resolv.conf isn't hidden. If it doesn't exist, THAT is the issue.  I'd re-install the **resolvconf** package.
**sudo apt-get --reinstall install resolvconf**
**$ more /etc/resolv.conf** will show the contents.

b) using *sudo gedit* is dangerous. Use **sudoedit /etc/resolv.conf**, if that is what you intend.  There are a few different reasons that sudo ***_should never_*** be used with any GUI program.  Set the EDITOR environment variable to whatever editor you wish to use. I think it is nano by default, but gedit can work on a desktop install running a GUI. It will not work on a GUI-less install.  sudoedit is the safest solution to editing system text files.

c) On Linux, '**dig**' is the program to perform DNS queries. nslookup has been deprecated about 10 yrs.

---

### Post by zolika1351 on 2017-03-28
Reinstalled resolvconf, tried to show contents, it says:
more: stat of /etc/resolv.conf failed: No such file or directory
EDIT: HOLY....the problem all along was resolv.conf not existing. I created a file and put this in: 
nameserver 8.8.8.8
nameserver 8.8.4.4
And now everything works!
Thanks for the help.

---

### Post by TheFu on 2017-03-28
Hope the fix sticks.

But ... that file will be overwritten by the **resolvconf** process which gets clues form network-manager or from the /etc/network/interfaces file or from whatever other network tools you may be using.  I use wicd-curses on 1 of my systems, since network-manager gets confused by non-trivial networking, for example. There are other tools.

Anyway - I suspect this won't solve it forever.  Whatever was removing the file is probably going to happen again.  Hopefully it won't, but computers tend to do the same things under the same conditions over and over.

Also, since 14.04, resolv.conf shouldn't be edited manually because the resolvconf tool will overwrite it with other settings.  I never liked this overly complicated package for very little usefulness.  /etc/resolv.conf had been working well for 30+ yrs, until someone decided to make intermediate files and complicate it because they felt too many cooks were touching that file.  </rant>

Of solved, please mark this thread [solved] to help others.

---

