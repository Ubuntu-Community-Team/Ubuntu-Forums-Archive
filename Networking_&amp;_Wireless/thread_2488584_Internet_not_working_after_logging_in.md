---
title: "Internet not working after logging in"
date: 2023-07-10
forum: Networking &amp; Wireless
---

### Post by samrat_dutta on 2023-07-10
Ubuntu 20.04, Kernel 5.4.0.153-generic

Wifi is connected but internet is not working. ping [www.google.com](www.google.com) shows Temporary failure in name resolution. ping 8.8.8.8 shows  sendmsg: Operation not permitted.
Interestingly, internet is working while in recovery mode as root! But after normal boot, internet is not accessible. I've tried modifying /etc/resolv.conf / netplan but it didn't help. 
Requesting your guidance to resolve this. Any help is very much appreciated. 
Thanks .

---

### Post by TheFu on 2023-07-10
> **samrat_dutta said:**
> Ubuntu 20.04, Kernel 5.4.0.153-generic

Wifi is connected but internet is not working. ping [www.google.com](www.google.com) shows Temporary failure in name resolution. ping 8.8.8.8 shows  sendmsg: Operation not permitted.
Interestingly, internet is working while in recovery mode as root! But after normal boot, internet is not accessible. I've tried modifying /etc/resolv.conf / netplan but it didn't help. 
Requesting your guidance to resolve this. Any help is very much appreciated. 
Thanks .

So, if you can't ping 8.8.8.8, then networking between the computer and that IP is broken somewhere.  Can you ping your LAN router by IP address?  If you can, then the problem is on the internet, not your equipment.  

If not, then I'd guess the issue is with the wifi adapter drivers.  You'll want to get the information about the working drives from the recovery mode and save those off.  Then boot into the non-working OS and look for differences.  Fix those.

---

### Post by samrat_dutta on 2023-07-10
Thanks for the reply. I cannot ping my own IP with normal boot. It would  be helpful if you could provide a pointer to get the working driver  info from the recovery mode.

---

### Post by TheFu on 2023-07-10
> **samrat_dutta said:**
> Thanks for the reply. I cannot ping my own IP with normal boot. It would  be helpful if you could provide a pointer to get the working driver  info from the recovery mode.

I have doubts that the driver is different.  That's why I specifically asked you do see the differences.  There could be options to the driver that need to be tweaked.

Sorry.  I use desktops, not wifi, so someone else would need to help.  All my connections are wired, except a tablet and wifi-only smartphone.

For my systems, I carefully pick the internal chips uses and pre-ensure they are well-supported by Linux BEFORE I buy.  I've been burned.  None of this helps you.  there is a wireless troubleshooting script which others have asked to be run.  Get it here: 
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```
I don't know if that is sufficient to get the desired details or not. If a URL is provided which contains the technical information, just post that URL here for wireless experts to review.

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) has more details. That post is a Sticky Post at the top of the _Networking & Wireless_ sub-forum here.

---

### Post by samrat_dutta on 2023-07-10
Facing the same issue with wired connection. The system was working fine  since I migrated to 20.04. A few weeks back, I faced this problem and  it was resolved through upgrading the kernel to the current version. But  my questions is what changes when I enter into the normal boot from  recovery mode as internet is working in the recovery mode? Secondly,  I've another system with exactly same configuration where ubuntu 20.04  with same kernel version  is running without any issue!! How can I use  the network configuration of the second laptop to resolve the issue of  the first?

---

### Post by TheFu on 2023-07-10
If you won't provide the requested data, nobody can help.  Things that seem similar often are not.

---

### Post by samrat_dutta on 2023-07-11
Sorry, I misunderstood the requirement. The output is available below. 
[https://paste.ubuntu.com/p/2Rjd6cV2d2/](https://paste.ubuntu.com/p/2Rjd6cV2d2/)

---

### Post by chili555 on 2023-07-11
From your paste:

> [777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']

The file /etc/resolv.conf is intended to be a symbolic link to /run/systemd/resolve/stub-resolv.conf Check:

```
ls -al /etc/resolv.conf
```
If it is not, correct it:

```
sudo rm /etc/resolv.conf
sudo ln -s /run/systemd/resolve/stub-resolv.conf  /etc/resolv.conf

```You should be all set.

---

### Post by TheFu on 2023-07-11
So - if you run the script in safe mode AND in the non-working mode, then compare the results, perhaps what is different will jump out?  I'd use the 'meld' tool for that comparison.  The differences are what will likely help you to figure this out.

As for the wired ethernet issue, Realtek NICs often get confused and the wrong driver is picked.  I stopped buying any computers with realtek due to this problem since around 2015. 

Of course, some wifi experts may be able to review the output and know exactly what's wrong.  That isn't me. Sorry.

---

