---
title: "No internet or network connection of any kind on 20.04 installation"
date: 2021-07-08
forum: Networking &amp; Wireless
---

### Post by Paul King on 2021-07-08
Hi

I am a fan of Ubuntu Studio, as I have used this OS to do some video and graphics on top of some programming. I had the 20.04 version, which seemed to change to "Ubuntu 20.04" after successive updates. 

A couple of months ago, one update caused the network to fail. The same machine is dual-boot, and I can see the internet quite well on Windows, as I am doing now. This is over an ethernet connection. By fail, I mean no internet, and no local intranet.

I decided to download, burn and install a DVD of Ubuntu Studio 20.04 (not Ubuntu 20.04) on the affected partitions. Right from the start, no network was ever detected, so that the installation could not download updates. I also must say that the partition manager leaves a lot to be desired, but that's another topic. Even after the installation, I remained in splendid isolation from the rest of the planet, network-wise. I can't even see the computer across the living room on my new installation.

Has Ubuntu Studio gone to the dogs? Is there a fix? Anything I should look for?

Paul King

---

### Post by TheFu on 2021-07-08
Well, some simple troubleshooting is needed first, to determine the real issue.

[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has steps to follow, in order.

Often, people say the *network is down*, when it is something completely different like DNS.  DNS is a different issue and "the network."  That's was the steps in that link will determine.
Run the steps in order, post the commands and output here.  Please.
You'll need to save the output to a file, probably on a flash drive so you'll be able to access it from Windows and copy/paste it here.

---

### Post by Paul King on 2021-07-09
For whatever reason, the forum won't allow me to past the output of the lsmod command. I guess if there is anything you want to know about modules, I will hope to answer in some other way.

the output of ip addr:
```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether d8:50:e6:4d:0c:da brd ff:ff:ff:ff:ff:ff
    altname enp0s25
    inet6 fe80::5d50:2fb1:dd1e:15fd/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


```

the output of the ping to my router:
```

ubuntu-studio@ubuntu-studio:~/B321-38BF$ ping 192.168.2.13
ping: connect: Network is unreachable

```

---

### Post by jeremy31 on 2021-07-09
Can you paste the result to paste.ubuntu.com or dpaste.com and post URL?

---

### Post by Paul King on 2021-07-09
I am getting a forbidden error, and can't seem to post very much, including pastebin stuff.

lsmod: [https://pastebin.com/qV6j3nyf](https://pastebin.com/qV6j3nyf)

dmesg, lshow, and resolv.conf: [https://pastebin.com/BskfrpFJ](https://pastebin.com/BskfrpFJ)

---

### Post by TheFu on 2021-07-09
They did a forum software upgrade a few days ago. That's been causing huge issues for posting content. So far this morning, I haven't had **any** issues posting replies, so perhaps it is fixed?  Yesterday, I had lots of issues.

Ok, looking at the **ip** and **ping** commands. I have a few guesses.
[LIST]
[*]That IP address for the router seems to be odd.  .13 is a very unusual router IP.  Normally it would be .1 or .254. Please check the value.
[*]It looks to me like your system isn't getting a DHCP response from any DHCP Server on the network.  Often, that would come from the router. eno1 doesn't have an IP assigned, hence the DHCP concern.
[/LIST]

Looked at the lshw. I217-V and the e1000e driver.  I use that driver with some of my Intel NICs, but I do vaguely recall the I217-V hardware having some issues. I don't have any i217-v hardware. One person found that disabling WoL in the BIOS and in Windows fixed the problem on their dual boot Linux system.  A cold boot (full power off boot, not a reset) also had the ethernet working.

---

### Post by Paul King on 2021-07-09
> **TheFu said:**
> They did a forum software upgrade a few days ago. That's been causing huge issues for posting content. So far this morning, I haven't had **any** issues posting replies, so perhaps it is fixed?  Yesterday, I had lots of issues.

Ok, looking at the **ip** and **ping** commands. I have a few guesses.
[LIST]
[*]That IP address for the router seems to be odd.  .13 is a very unusual router IP.  Normally it would be .1 or .254. Please check the value. 
[*]It looks to me like your system isn't getting a DHCP response from any DHCP Server on the network.  Often, that would come from the router. eno1 doesn't have an IP assigned, hence the DHCP concern. 
[/LIST]

Looked at the lshw. I217-V and the e1000e driver.  I use that driver with some of my Intel NICs, but I do vaguely recall the I217-V hardware having some issues. I don't have any i217-v hardware. One person found that disabling WoL in the BIOS and in Windows fixed the problem on their dual boot Linux system.  A cold boot (full power off boot, not a reset) also had the ethernet working.

I have a bit of an odd configuration. This is because I have 2 cabelled computers and one printer and the internet modem supplied by my isp permits only 1 (2 if you count the TV). So there is a second router for all of my household connections (wired and wireless). The router which bits go through first has the 2.13 designation. The one that is 2.1 leads my ISP modem. My windows 10 computers, printer, both W10 laptops, and cell phone (Android) have no problem figuring this out, and all connect to the 2.13 router (except the television). This is strictly a Linux PC problem, by all appearances.

On the modem end, the router IP is the given with the 2.1 ending, so they match. Both have enabled DHCP.

There have been many cold boots since the problem started, and I have had the same failure in Linux not auto-detecting the network. More recently I have tried a Ubuntu Studio DVD, a Debian DVD, and the same problem each time.

Could you please explain the strange fix for WoL (whatever that is)? You appear to be suggesting that I go into windows and "fix" something that is working properly. 

Paul

---

### Post by Paul King on 2021-07-09
Scheme of my home configuration:
```

[Devices, PCs, Laptops] ------> Router ------> Modem ------> Internet
                                                   ^
                                                   |
                                                  TV

```
Modem also supplies cable to my television, so that will show up on the modem's network also.

---

### Post by praseodym on 2021-07-09
Please download the wireless script from the sticky thread, run it as described and paste the output completely

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by TheFu on 2021-07-09
WoL = Wake on LAN.  If you don't know what it is, then it isn't being used and is 100% safe to disable in the BIOS and in MS-Windows.
Google found that answer. It surprised me too. It could have easily been only for that single persons hardware failures, but since WoL doesn't get used unless it is actively used (and known), there's no harm in disabling it and certainly no harm in disabling it temporarily.

Running the wireless info script won't hurt and could help. It isn't just for wireless stuff. We'll get a more complete picture of the Linux setup, though without a working DHCP, I don't see how it will be much use.  Would could be useful is booting from 16.04, 18.04, and 20.04 "Try Ubuntu" flash drives.  You could setup a multi-boot flash drive to accomplish this. 8G flash storage (or microSD or SD) would be fine to hold all those (and more) distros.  I say this because 20.04 seemed to include updated drivers that broke some not-bleeding-edge networking setups.

BTW, I'll have to take my website down this weekend for some hardware swaps inside the same system, so that blog.jdpfu.com link won't be available for most of the Saturday. Use the wayback machine if you need it. It should be back up by Sunday afternoon at the latest.

---

