---
title: "How do i set mtu, path mtu discovery,rwin"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by tomski on 2005-12-01
Hi all,

i have a bit of a problem 
when i browse the net with windows my general session is quite responsive as i have set the  mtu = 1458, path mtu discovery =yes & rwin = 551736 settings using DrTcp to make my session more responsive, this was advised by the site 'broadband reports'
when i first chaged these i did notice the difference in downloads and general browsing so i now use those as defaults.

how do i make these adjustments in linux ?
i know how to set the mtu by specifiying in the /etc/network/interfaces file but where do ichange the other settings?

---

### Post by rmjokers on 2005-12-01
Alot of these network settings are in:

/proc/sys/net/ipv4/

You can make the changes permanent by placing them in:

/etc/sysctl.conf

(Make sure you read the warning at the top of the file)

To just test a setting, you can use the sysctl command.

---

### Post by tomski on 2005-12-01
Thanks rmjokers 
but
1) what is the correct syntax 
2) what other options can i add

---

### Post by rmjokers on 2005-12-02
In all honesty, I dont know which settings you would have to change to get the same behaviour as the windows settings you mentioned.  I have read somewhere that the linux kernel modifies the recieve window dynamically, and automatically does path mtu discovery, so it shouldnt have the performance problems you mentioned.  To get a list of all of the configurable parameters in the kernel, just run

sysctl -A

To look at a particular value (/proc/sys/net/ipv4/icmp_echo_ignore_broadcasts)

sysctl net.ipv4.icmp_echo_ignore_broadcasts

To change the value,

sudo sysctl net.ipv4.icmp_echo_ignore_broadcasts=1

For a description of what each of these settings does, you have to read the kernel documentation.  For the IP options for example, look at Documentation/networking/ip-sysctl.txt which is in the kernel source code.

---

### Post by tomski on 2005-12-02
thanks rmjokers
 i know this is a bit of a grey area but you have pointed me in the right direction which is more than i had when first made this post

cheers & thanks for the help

---

### Post by veloct on 2005-12-22
[http://www.santa-li.com/linuxonbb.html](http://www.santa-li.com/linuxonbb.html)

Try that site, good information. HTH

---

### Post by tomski on 2005-12-22
thanks veloct that was just right on the nose cheers

this is what i like about this forum everyone is soooo helpful

---

### Post by dcstar on 2005-12-22
[QUOTE=veloct][http://www.santa-li.com/linuxonbb.html](http://www.santa-li.com/linuxonbb.html)

Try that site, good information. HTH[/QUOTE]
The recommended Powertweak package is good, certainly worth installing if you want to modify these things.

---

