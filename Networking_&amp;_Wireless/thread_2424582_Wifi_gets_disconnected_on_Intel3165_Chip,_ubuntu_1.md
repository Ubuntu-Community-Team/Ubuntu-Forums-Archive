---
title: "Wifi gets disconnected on Intel3165 Chip, ubuntu 18.04"
date: 2019-08-11
forum: Networking &amp; Wireless
---

### Post by darthvader1234 on 2019-08-11
Hi,
My wifi is consistently getting disconnected after about half an hour of usage. Any ideas regarding what I could do to fix it?

Things I have tried to give you guys information:

hidden@hidden-Inspiron-13-5378:~$ uname -a
Linux anand-Inspiron-13-5378 5.0.0-23-generic #24~18.04.1-Ubuntu SMP Mon Jul 29 16:12:28 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


hidden@hidden-Inspiron-13-5378:~$ lshw -C network
  *-network                 
       description: Wireless interface
       product: Wireless 3165
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 79
       serial: 7c:67:a2:67:c8:02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.0.0-23-generic firmware=29.1044073957.0 ip=10.22.22.84 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:146 memory:d1000000-d1001fff

---

### Post by praseodym on 2019-08-11
Try this one
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi-11n.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by darthvader1234 on 2019-08-30
I tried this, This worked for a day, and then disabled my wifi completely, after restarting my system. Is there any other info you need to give me a more accurate solution, thanks in Advance, Sorry for the delayed response, my screen stopped working(hardware issue), and I had to give my laptop for servicing.

---

### Post by darthvader1234 on 2019-08-31
Please help me, the issue has become significantly worse, i now disconnect from wifi within 10 minutes of restarting my system, and to re enable it, i need to restart my system again

---

### Post by him610 on 2019-09-01
Have you followed the instructions found here, [https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108")

---

### Post by darthvader1234 on 2019-09-02
I followed the instructions
Here is the link to my pastebin: [https://pastebin.com/A5pnwep8](https://pastebin.com/A5pnwep8)

---

### Post by him610 on 2019-09-02
darthvader1234,
While I am only a network novice (there are others who are network gurus of the Nth order), in reviewing your wireless-info.txt, I noticed:

```
56. SecureBoot enabled
388. Region: Atlantic/Reykjavik (based on set time zone)
381. country 00: DFS-UNSET
```

Recommend: 

In BIOS/UEFI change to SecureBoot disabled

Region and country should correspond. If you are really in Iceland, from a terminal
```

sudo iw reg set IS
sudo sed -i 's/=.*/=IS/' /etc/default/crda

```
The first line sets the country code temporarily while the second line sets it permanently.
Country codes can be found in /usr/share/zoneinfo/zone.tab

I hope this helps.

---

### Post by darthvader1234 on 2019-09-02
I am not in Iceland, I was there at the time of installation of Ubuntu. I am now in India, And have run the commands with the Appropraite Zone, Let me see if the problem persists and post an update here soon

---

### Post by darthvader1234 on 2019-09-02
Unfortunately, The problem persisted, but Now I can stay on a connection for 30 minutes or so before getting kicked out. I have updated the pastebin after rerunning the code(I have also re enabled secure boot after making the changes)

---

### Post by him610 on 2019-09-03
darthvader1234,
There is another issue in your wireless-info.txt
```

58  ##### lsmod #############################
60.  libkmod: ERROR ../libkmod/libkmod-module.c:1931 kmod_module_get_holders: could not open '/sys/module/windrvr6/holders': No such file or directory

```
This is what mine looks like,
```
##### lsmod #############################

iwlmvm                364544  0
mac80211              778240  1 iwlmvm
iwlwifi               286720  1 iwlmvm
cfg80211              622592  3 iwlmvm,iwlwifi,mac80211

```

Unfortunately, I, a novice, have no recommended solution for you, but maybe gurus, chilli555 or jeremy31 will respond your post.

---

### Post by darthvader1234 on 2019-09-17
I fixed the lsmod issues, One of the softwares I had on my laptop was causing it(Xilinx ISE 14.7, The installation changes the global variable LD_PRELOAD, causing lsmod issues), Just wanted to mention the solution to that part here in case someone has the same issue.
However this still doesn't fix the issue.
I have updated the pastebin, and here is the link to that [https://pastebin.com/A5pnwep8](https://pastebin.com/A5pnwep8)

---

### Post by darthvader1234 on 2019-09-18
Oh yeah one more thing, in case it helps, My wifi was perfectly fine on ubuntu 16.04, when I upgraded, I started having these issues. I upgraded by deleting my OS and reinstalling ubuntu 18.04 in my dual boot partition, but I have already attempted whatever I tried when I fixed my wifi on 16.04

---

### Post by jeremy31 on 2019-09-18
Try a live iso and see if you still have issues

---

### Post by darthvader1234 on 2019-09-25
Hi Jeremy,
I tried booting from a live USB. It still threw an error, and wifi stopped working after 10 or so minutes
I have pasted the error report here:
[https://pastebin.com/SLi8HAWZ](https://pastebin.com/SLi8HAWZ)

---

### Post by jeremy31 on 2019-09-25
Edit grub ```
gedit admin:///etc/default/grub
```
Add ```
net.ipv4.tcp_ecn=0
```
Inside the quotes along quiet splash, then see if it works, found the info at [https://bbs.archlinux.org/viewtopic.php?id=240916](https://bbs.archlinux.org/viewtopic.php?id=240916)

---

### Post by darthvader1234 on 2019-09-26
When I run this on ubuntu(no live iso) I get the error:
/etc/default/grub: line 34: net.ipv4.tcp_ecn=0: command not found

I will try it out on a live iso shortly

---

### Post by darthvader1234 on 2019-09-26
I also realized the the live iso doesnt have the updated drivers that are there in my dual boot version of ubuntu, giving rise to the change in error message

---

### Post by jeremy31 on 2019-09-26
I think you should have made the change to this line in grub ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
So that it is ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash net.ipv4.tcp_ecn=0"
```
Save and then do ```
sudo update-grub
```

---

### Post by darthvader1234 on 2019-09-27
Yeah, that didnt work either. Infact, this time the wifi stopped working within minutes of booting the laptop

---

### Post by darthvader1234 on 2019-09-28
I realized, It would be easier to start with a clean slate to fix this issue, I have just freshly installed ubuntu 18.04 on my system, and have switched off power management for wifi driver. Thats all

Now this is the error : [https://pastebin.com/G1LfZTrG](https://pastebin.com/G1LfZTrG)

---

### Post by darthvader1234 on 2019-10-13
Just an update on the issue, it was again magically back to normal and I spent 48 hours on the same wifi network without being disconnected. Howeever the issue has surfaced again, and this was the paste bin this time around
[https://pastebin.com/FrPgTEWf](https://pastebin.com/FrPgTEWf)

---

### Post by darthvader1234 on 2019-11-04
Did anyone else with a similar issue figure out how to fix this?
I found this link: [https://bugzilla.kernel.org/show_bug.cgi?id=201469](https://bugzilla.kernel.org/show_bug.cgi?id=201469), but I am not sure if this is the reason my wifi driver is failing. How can I verify this?


Edit:
I have a dual boot system. On windows as well, my wifi keeps disconnecting and reconnecting, In Ubuntu, it is unable to reconnect, and hnce it fails. Could there be a link between the two failure cases?

---

